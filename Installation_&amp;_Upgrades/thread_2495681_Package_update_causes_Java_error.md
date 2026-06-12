---
title: "Package update causes Java error"
date: 2024-02-27
forum: Installation &amp; Upgrades
---

### Post by oliverkohll on 2024-02-27
Last night some Ubuntu 20.04.6 LTS servers updated some packages:

libpq5 libxml2 openjdk-17-jdk openjdk-17-jdk-headless openjdk-17-jre openjdk-17-jre-headless

That resulted in errors in our Java application, e.g. messages

'java.io.IOException: error=0, Failed to exec spawn helper'

in the logs when trying to upload files etc.

The workaround described here worked: [https://stackoverflow.com/questions/61301818/java-failed-to-exec-spawn-helper-error-since-moving-to-java-14-on-linux](https://stackoverflow.com/questions/61301818/java-failed-to-exec-spawn-helper-error-since-moving-to-java-14-on-linux)
i.e. adding

-Djdk.lang.Process.launchMechanism=vfork

to the Java command line options.

So that's good, but I'd like to report this to whoever should know knows - any idea where that should go?

---

