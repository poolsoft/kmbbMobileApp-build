# kmbbMobileApp Build

Public iOS build workflow for the private poolsoft/kmbbMobileApp repository (flutter branch).
Only the workflow and these instructions belong in this repository. Never push application source or signing files here.

## Configure Actions secrets

Open https://github.com/poolsoft/kmbbMobileApp-build/settings/secrets/actions and replace every `-` placeholder:

| Secret | Value |
| --- | --- |
| APPLE_ID | Apple Developer account email |
| APPLE_PASSWORD | Apple app-specific password used by the existing Fastlane workflow |
| APP_STORE_CONNECT_API_KEY_KEY_ID | App Store Connect API key ID |
| APP_STORE_CONNECT_API_KEY_ISSUER_ID | App Store Connect issuer ID |
| APP_STORE_CONNECT_API_KEY_KEY | Base64 encoded contents of the .p8 file; Fastlane uses is_key_content_base64: true |
| GIT_BASIC_AUTHORIZATION | GitHub PAT starting ghp_ or github_pat_, or Base64 of username:token; must access private source and Match certificates branch |
| MATCH_PASSWORD | Existing Fastlane Match encryption password; do not replace with an unrelated new password |
| TEAM_ID | Apple Developer Team ID |

Optional secrets: APP_IDENTIFIER and GIT_URL. When absent, Fastlane defaults to the existing app identifier and private source repository. Match uses its certificates branch.

## Run

Actions > iOS TestFlight ve App Store Dagitimi > Run workflow.
Choose artifact_only to build an IPA without a TestFlight upload, or testflight to build and upload.
The workflow stops before cloning when any required secret is missing or still a placeholder.
IPA artifacts are uploaded; application source is not uploaded as an artifact.

No build was started during repository setup. Actual macOS/signing validation requires valid secrets and a manual run.