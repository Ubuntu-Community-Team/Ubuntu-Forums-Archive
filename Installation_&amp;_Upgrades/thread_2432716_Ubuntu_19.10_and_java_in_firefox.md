---
title: "Ubuntu 19.10 and java in firefox"
date: 2019-12-07
forum: Installation &amp; Upgrades
---

### Post by dominbdg on 2019-12-07
Hello,

I have a following issue,
I need to have firefox in my Ubuntu 19.10 running with java but to be honest - I don't know what to do.
The requirements are thaty java engine should be in vewrsion 8.
SO I installed java 8

[FONT=monospace][COLOR=#000000]root@dominik:/home/dominik/Downloads# java -version[/COLOR]
openjdk version "1.8.0_232-ea"
OpenJDK Runtime Environment (build 1.8.0_232-ea-8u232-b09-0ubuntu1-b09)
OpenJDK 64-Bit Server VM (build 25.232-b09, mixed mode)

and strange think is that when typing javac -version:

[/FONT][FONT=monospace][COLOR=#000000]root@dominik:/home/dominik/Downloads# javac -version[/COLOR]
javac 13.0.1

I have 13 version

but the another thing is that I need to have java support in firefox, I know that this is realised by icedtea-plugin but I don't have such package in my Ubintu version,

can anyone help me with that ?

Best Regards[/FONT]

---

### Post by The Cog on 2019-12-07
How did you install java 8?

This lists the openjdk packages you can install easily in Ubuntu:
```
sudo apt search openjdk
```

If you want javac, mayne you want openjdk-8-jdk.

---

### Post by dominbdg on 2019-12-07
Hello The Cog,
I have installed java from the apt directly:
apt-get install openjdk-8-jdk

but the problem is that probably firefox don't see java.
This is very needed for me, because I need to work remotely using checkpoint vpn and this solution from website don't see java:

I'm trying to use firefox and I red that there's needed icedtea-plugin package which I cannot find.

this is the result from my side:
[https://1drv.ms/u/s!AqdJa_pamP_OgqsMBEM ... g?e=eTwT1e]("https://1drv.ms/u/s!AqdJa_pamP_OgqsMBEM1j8HkkKHTIg?e=eTwT1e")

best Regards
Dominik

---

### Post by walts48 on 2019-12-07
The Java plugin hasn't been allowed in Firefox since version 52.0.

[https://support.mozilla.org/en-US/kb/npapi-plugins](https://support.mozilla.org/en-US/kb/npapi-plugins)

---

### Post by akounga on 2019-12-30
Me too, i am having the same issue. Not able to make firefox see java 8 plugin enable with a symbolic link ./jre1.8.0_231/lib/amd64/libnpjp2.so.

 My OS is Ubuntu 16.04

alain@ubuntu:~$ java -version
openjdk version "1.8.0_232"
OpenJDK Runtime Environment (build 1.8.0_232-8u232-b09-0ubuntu1~16.04.1-b09)
OpenJDK 64-Bit Server VM (build 25.232-b09, mixed mode)

I will appreciate if i can get any help on how to go about this.

---

### Post by walts48 on 2019-12-31
> **akounga said:**
> Me too, i am having the same issue. Not able to make firefox see java 8 plugin enable with a symbolic link ./jre1.8.0_231/lib/amd64/libnpjp2.so.

 My OS is Ubuntu 16.04

alain@ubuntu:~$ java -version
openjdk version "1.8.0_232"
OpenJDK Runtime Environment (build 1.8.0_232-8u232-b09-0ubuntu1~16.04.1-b09)
OpenJDK 64-Bit Server VM (build 25.232-b09, mixed mode)

I will appreciate if i can get any help on how to go about this.

What version of Firefox?

> The Java plugin hasn't been allowed in Firefox since version 52.0.

[https://support.mozilla.org/en-US/kb/npapi-plugins](https://support.mozilla.org/en-US/kb/npapi-plugins)

---

### Post by akounga on 2020-01-02
I have Firefox version 71 (64bit). it's any work around this issue you can recommend? like starting java web start application short of having java install?
Or should i go ahead and downgrade to Firefox version 51.0.1 I just use this server for labs not more than that so i don't need the latest Firefox as long as i install java.

If i install Firefox Extended Support Release will that help with this issue?

---

