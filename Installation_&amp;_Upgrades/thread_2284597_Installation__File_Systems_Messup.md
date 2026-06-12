---
title: "Installation / File Systems Messup"
date: 2015-06-30
forum: Installation &amp; Upgrades
---

### Post by Muhammad_Abdullah_ on 2015-06-30
In a bit of a situation here, trying best not to freak out. I was toying with Ubuntu last night and I think I messed up the process somewhere during installation. I ran the ubuntu setup from windows 8.1 and wanted to install it on a new partition on the only hard disk I have installed in my laptop. The installation didn't work I guess because at one point the computer restarted and just stopped booting altogether. Have been looking all the over the internet, but can't really figure out what the problem is. 

Have tried to boot with a Windows 8.1 setup USB, the computer doesn't pick it up at all. 
It won't boot from the hard disk either.

I used another PC to make a linux USB (running Live Ubuntu now) and it's picking up that a hard disk exists, but Ubuntu wants me to reformat it I guess. 

Can anyone help me out? Have more than 4 years of data on the hard disk, afraid I'll do something wrong and lose all of it.

---

### Post by ajgreeny on 2015-06-30
From your comment about  running the ubuntu setup from windows 8.1 it sounds as if you were trying to use the WUBI installation method which is no longer supported, and will not work with Win8 even if you try to use it and it apparently manages to install the OS.
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

It is possible that you need to simply restore the Win8 bootloader system, but I will have to leave others to show you how to do that as I no longer run Windows, but if you have a Win8 DVD you may be able to do it from that in some way.  If you have no Win8 DVD it may be more difficult, but wait for others to answer as they will probably have more help to give than I can manage.

---

### Post by grahammechanical on 2015-06-30
I am not speaking from experience. Just speaking from viewing threads on this forum. If Windows 8.1 was pre-installed then the motherboard will have a UEFI boot system and you may well have to enter the UEFI settings utility to instruct the motherboard to load an OS from the Windows 8.1 USB memory stick.

Regards.

---

### Post by oldfred on 2015-06-30
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Boot-Repair cannot fix most Windows issues, but report will tell us all about where you are at.

---

