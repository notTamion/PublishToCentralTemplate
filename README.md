# Publish to Maven Central using Gradle and Github Actions

This repo contains a template gradle buildscript and workflow. The workflow can basically be copy-pasted.

I tried to remove anything that is not required and make it as minimal as possible.

### How to use with Github actions:
1. Setup the following repository secrets on github:
- GPG_SECRET_KEY: Output of the `gpg --export-secret-keys -a <key-id>` command
- GPG_SECRET_KEY_PASSWORD: Password of the used key
- SONATYPE_USERNAME: Username for Sonatype
- SONATYPE_PASSWORD: Password for Sonatype
2. When creating a release it will automatically publish to Maven Central

### How to use without Github actions:
1. Setup gradle.properties like this and make sure you have the gpg key imported:
```
signing.gnupg.passphrase=Password for used key (Optional)
sonatypeUsername=Username for Sonatype
sonatypePassword=Password for Sonatype
```
2. run `./gradlew publish closeAndReleaseStagingRepository`

In both cases you should be able to access the published dependency after about 30 minutes