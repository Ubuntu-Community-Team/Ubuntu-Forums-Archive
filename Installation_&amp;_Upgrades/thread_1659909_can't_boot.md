---
title: "can't boot"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by murdoch201 on 2011-01-04
Hi,

i have Ubuntu 10.04.1 installed with WUBI (beceause when i install thru CD it says something about rewriting configurations to harddisk, which nobody can explain well so...)

When i start up my PC it just starts Windows. It seems Ubuntu is not added to the boot list. I have already installed EasyBCD, but i don't want to take risks. Anybody idea what i need to do now?

Greets,
Murdoch

---

### Post by leaonfm on 2011-01-04
to be honest, i never use WUBI.
but your problem seems that Ubuntu entry was not added to Windows boot loader, and yes, try easyBCD see if it can fix the issue. (i believe ubuntu 10.04 uses GRUB2)

---

### Post by wilee-nilee on 2011-01-04
I believe easybcd is for dual booting not a wubi.

Also Wubi doesn't use grub in a conventional manner as a dual boot does.

Remove the easybcd, and do this below, or just remove wubi and try again, this wiki might help as well.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

---

### Post by bcbc on 2011-01-04
Just check the boot manager entries to see whether Ubuntu was added. Then make sure the timeout is > 0, otherwise it won't give you a choice. I believe easyBCD will let you check the current boot entries and timeout - otherwise use the standard Windows method (Startup & Recovery settings under System properties)

If there is no entry, post the log in the %temp% folder (file wubi-10.04.1-rev190.log)

When (if) you get Ubuntu running, do not update packages grub-pc and grub-common due to a grub problem with Wubi at the moment.

---

### Post by murdoch201 on 2011-01-05
Here is the log file in the Temp folder:

[www.murdoch3d.net/wubi-10.04.1-rev190.log]("http://www.murdoch3d.net/wubi-10.04.1-rev190.log")


I will post that log from the ubuntu live cd when i have it.

My system spec's:
Windows 7 home premium 32-bits
Intel Core 2 Duo
2x Nvidia Geforce 8800 GTX
4 GB RAM

---

### Post by bcbc on 2011-01-05
It looks like it's failing to add the bcd entry for Wubi. It says it succeeded, but when you uninstalled it kept failing saying it couldn't find the entry. Reinstalling then says the entry is already there. Something strange going on. 

Are you trying to install to a dynamic drive? That won't work.

---

### Post by cathy duncan on 2011-01-05
> **bcbc said:**
> It looks like it's failing to add the bcd entry for Wubi. It says it succeeded, but when you uninstalled it kept failing saying it couldn't find the entry. Reinstalling then says the entry is already there. Something strange going on. 
 
Are you trying to install to a dynamic drive? That won't work.
 
I am also of the same view point and in my personal opinion, it would be the problem, because if am not wrong, I have had such a problem in past already and one of my friends came and fixed it for me. Will ask him about this problem too.

---

### Post by murdoch201 on 2011-01-05
Oh, but i think i know what occured this

First, i downloaded wubi.exe from the ubuntu website, which downloaded and installed ubuntu. When i tryed to boot it up it gave me an error about build.mdr (or something). Then i have seen it was a 64-bit version wubi has installed (it didn't asked me which version i would like to have first). I didn't know how to uninstall so i searched google, which said that i have to use EasyBCD. Later, when i downloaded 32-bit iso and burned, started wubi.exe from that drive, it said there is another ubuntu which has to be removed first. But when i click remove it gives me a big error. So, on google instructions, i deleted the 'ubuntu' folder on my external HD. After then it worked and it has been installed. And the rest you know.

Is there anyway to fix this?

greets,
murdoch201

---

### Post by bcbc on 2011-01-05
Run a full manual uninstall as described in the [WubiGuide]("https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?")

Note: wubi downloads 64-bit automatically if it detects your computer is capable of processing 64-bit. The names 'amd' and 'i386' are misnomers - should be 32-bit and 64-bit.

---

