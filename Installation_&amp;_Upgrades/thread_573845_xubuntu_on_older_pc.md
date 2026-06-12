---
title: "xubuntu on older pc"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by aakaasha on 2007-10-12
hello!

I have the following problem: I wanted to reactivate an old pc (mainly for text processing and office tasks). It has a **533MHz Processor** with** 256MB RAM**. Win2000 was installed. After backing up old data I inserted the **xubuntu 7.04 alternate cd** and rebooted.
Everything worked fine, it installed for 3.5h and then stuck at the following point:

*"installing software - 65% - configuring anthy"*.

After 2 hours at this point I hit "reset". The install menu came up again. Install was faster this time (probably due to already formatted disc?) and after 2h it came to the critical 65% - and stuck again.

I let it run overnight (~10h) and this morning turned it off.

:confused: Any ideas, what can be wrong and what I should do? I don't want to set up Win on this machine again.

Thanks in advance, Florian

---

### Post by Sef on 2007-10-12
1. Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the download?

2. Did you burn the iso as an iso and at 4x or less?

3. Did you check the disk to make sure it is ok?

---

### Post by aakaasha on 2007-10-12
I found this thread and will give it a try.
[http://ubuntuforums.org/showthread.php?t=293514]("http://ubuntuforums.org/showthread.php?t=293514")

---

### Post by Sef on 2007-10-12
Let us know how it works out - for better or for worse.

---

### Post by kerry_s on 2007-10-12
go debian xfce4 it's faster.

[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)

---

### Post by aakaasha on 2007-10-15
I tried to first install the command-line-system and then added the gui via package manager. Afterwards it did not work, some essential components were missing.

Then I tried the normal install and killed the process "configuring anthy", installation completed, but unfortunately the xserver could not start up.

I called my brother, who is a linux expert. He tried 2 hours to configure the xserver the right way but failed. He says that there is a problem with the graphic card. He tried to specify the correct configuration in the config file, but xubuntu seems to ignore this configuration.

While loading the xserver the following error occurs: "Device not found"

I have only  a basic understanding of hardware specs and I am a linux rookie too, so I cannot tell you more about it.

I am trying to install the debian system and hopefully it recognizes the graphic device...

---

