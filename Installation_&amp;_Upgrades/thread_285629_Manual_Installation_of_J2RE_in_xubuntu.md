---
title: "Manual Installation of J2RE in xubuntu"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by textguru on 2006-10-27
I want to install j2re with firefox plugin manually without using the repositories. I already downloaded deb files (saved on separate folder as listed)

sun-java5-jre_1.5.0-06-1_all.deb
sun-java5-bin_1.5.0-06-1_i386.deb  sun-java5-plugin_1.5.0-06-1_i386.deb

I have tried installing these deb files thru:

sudo dpkg -i sun*.deb

But I encounter problem (as indicated on previous post: [http://ubuntuforums.org/showthread.php?t=285488](http://ubuntuforums.org/showthread.php?t=285488))

I have followed another instruction:

[http://ubuntuforums.org/showthread.php?t=148075]("http://ubuntuforums.org/showthread.php?t=148075")

After downloading the new installer file (jre-1_5_0_09-linux-i586.bin). I encounter error when executing the file:

```
ubuntu@mypc:~/Desktop/Softwares$ sudo mv jre-1_5_0_09-linux-i586.bin /usr/local
ubuntu@mypc:~/Desktop/Softwares$ cd /usr/local
ubuntu@mypc:/usr/local$ ls
bin  games  include  jre-1_5_0_09-linux-i586.bin  lib  man  sbin  share  src
ubuntu@mypc:/usr/local$ sudo chmod a+x jre-1_5_0_09-linux-i586.bin
ubuntu@mypc:/usr/local$ sudo sh jre-1_5_0_09-linux-i586.bin
jre-1_5_0_09-linux-i586.bin: line 1: syntax error near unexpected token `newline'
jre-1_5_0_09-linux-i586.bin: line 1: `<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">'
ubuntu@mypc:/usr/local$

```

Need help on this.

---

