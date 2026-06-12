---
title: "Can't load Java 6"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by tigcaldwell on 2010-11-05
Just created a partition to run Ubuntu 10.04.  Need to execute an Xcel spreadsheet that requires Linux and a JRE from Java.  ATT is my DSL provider, but they do not support Linux, so I have no internet connectivity.  I downloaded JAVA 6.0 from another machine and attempted to load it - with no success.  Two days of no success!  I run OS X and Windows 7, but Linux is new to me.  I'm trying, but I'm missing something.

Here's the file on my desktop...

jre1.6.0_22

It opened from the native download...

jre-6u22-linux-i586.bin.sh

Any help is greatly appreciated.

tig

---

### Post by oldos2er on 2010-11-05
After you've extracted the java folder, you need to "tell" your system it's there: ```
sudo update-alternatives --install "/usr/bin/java" "java" "/home/user/jre1.6.0_22/bin/java" 1
sudo update-alternatives --set java /home/user/jre1.6.0_22/bin/java
```
Run those commands one at a time; obviously you'll need to replace "user" with your username.

You might want to post about the AT&T problem in the Networking & Wireless subforum; I'm sure there's *someone* who's using their DSL with Linux.

---

### Post by tigcaldwell on 2010-11-05
Thanks for your help, but I got the following message...

update-alternatives: error: no alternatives for java

I typed the commands exactly as you suggested, but this is what came back.  Was "usr" in the first prompt supposed to be user?

Your help IS appreciated!!!!

---

### Post by oldos2er on 2010-11-06
> **tigcaldwell said:**
> Thanks for your help, but I got the following message...

update-alternatives: error: no alternatives for java

I typed the commands exactly as you suggested, but this is what came back.  Was "usr" in the first prompt supposed to be user?


No.

Would you mind copying and pasting the commands in your terminal, and showing the output? Also can you verify the java folder location on your system /home/<user>/jre1.6.0_22/bin/java ?

Edit: If you don't want to fiddle around in the terminal, try [http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html)

---

