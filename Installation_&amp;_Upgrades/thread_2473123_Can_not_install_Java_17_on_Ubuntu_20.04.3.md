---
title: "Can not install Java 17 on Ubuntu 20.04.3"
date: 2022-03-24
forum: Installation &amp; Upgrades
---

### Post by Roland_Msl on 2022-03-24
Just wanted to use Apache Open meetings. But Open meetings told me current installed Java  has only Variables 52 and 55 required.

So I tried to install Java 17 by the instructions on [https://wiki.ubuntuusers.de/Java/Installation/OpenJDK/](https://wiki.ubuntuusers.de/Java/Installation/OpenJDK/)

Everything is fine until a screen comes, that I have to agree to the terms.
I have no idea how to agree.
Click on the OK button, enter Y or OK, but there is no prompt.
Regardless what I do, this message remains.

---

### Post by Roland_Msl on 2022-03-24
I tried now sudo apt-get install openjdk-16-jre but suddenly again the screen with "Configuring oracle-java17-installer" and nothing to continue
After restart, I searched for oracle* and deleted in var/cache/apts/archive 2 files
But again apt-get install openjdk-16-jre leaded to the screen with "Configuring oracle-java17-installer"

---

### Post by rikuitop on 2022-03-28
They are 2 versions: open-source builds and commercial builds from Oracle.

Here is what I did:
> java -version
Command 'java' not found
It is fine otherwise you have to uninstall previous versions.
Download the open-source build from [https://jdk.java.net/17/](https://jdk.java.net/17/) 
> sha256sum -b openjdk-17.0.2_linux-x64_bin.tar.gz
sudo mkdir -p -v /opt/java/64
cd ~/Downloads
tar -zxvf openjdk-17.0.2_linux-x64_bin.tar.gz
sudo mv -v jdk* /opt/java/64
sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/64/jdk-17.0.2/bin/java" 1
sudo update-alternatives --set java /opt/java/64/jdk-17.0.2/bin/java
java -version
openjdk version "17.0.2" 2022-01-18

---

### Post by ajgreeny on 2022-03-28
When you see that Oracle terms and conditions window use Tab to highlight the OK at the bottom, then hit Enter and it should proceed through the rest of the necessary installation.

---

