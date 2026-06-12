---
title: "Oracle JDK 7 installer error"
date: 2013-02-14
forum: Installation &amp; Upgrades
---

### Post by sebass99 on 2013-02-14
Hello, I'm not entirely new to Ubuntu, been using it steadily for half a year now, but I still have some major and minor gaps. The other day, I tried to install Oracle JDK 7, through a repository. I used this code;

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

but, every time I try to install it, it fails, it gets stuck at 'Removing outdated cached downloads...'. It then proceeds to fail the installation. I don't know what to do, any and all sudo apt-get commands ties an installation attempt of the JDK to it, so every apt-get command will end in an attempt and failure of the JDK installation. I tried deleting the file, no dice, I tried 
```
sudo apt-get remove oracle-java7-installer
```
but it didn't work, as it wasn't properly installed. PPA purging didn't work either, as it was a apt-get command, so it just ended with a reinstallation of JDK 7. Any help to removing this completely from my computer? The other java based installations I have are; IcedTea java plugin, and Eclipse with integrated development.

---

### Post by slickymaster on 2013-02-14
Try the following:
```
sudo dpkg -r --force-all oracle-jdk7-installer
```

---

