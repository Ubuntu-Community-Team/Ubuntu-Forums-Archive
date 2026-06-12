---
title: "data.sys error and &quot;ubuntu&quot; boot option"
date: 2015-09-22
forum: Installation &amp; Upgrades
---

### Post by anton39 on 2015-09-22
Hello people,

**Fixed "ubuntu"  boot option problem, by q-flashing motherboard.**

I know there are a ton of threads like that but none of them could help me. I hope you will help me to find a solution.

I deleted windows and installed ubuntu, then ubuntu started acting weird (freeze for infinite amount of time) and I deleted it too. But, in my Bios i still have option boot "ubuntu" as a hard drive, while i formated my whole drive into NTFS when i was installing windows.

The other problem I cannot start windows because of Data.sys error, similar freeze i got when i installed "ubuntu" again and tried to run it. 

I tried various fixes:

1. I ran "bootrec /fixboot" and "bootreg /fixmbr" commands from recovery windows disk.

2. I deleted all different partitions, and formated all space to NTFS.

3.  turned on and off "[COLOR=#000000][FONT=verdana]AHSI" in Bios.

[/FONT][/COLOR]I installed Easybcd 2.2 on my little laptop, but not really familiar with the program so don't know how to make a bootable version of this program so i can repair booting on my desktop PC.

I would really appreciate any help. 

Ultimately, i would like to install both windows and ubuntu on my desktop.

P.S. it's third day without my desktop. I have to get it back :D

P.S.S i don't have wired connection to internet(( cannot just run sudo get-apt in Linux

---

### Post by anton39 on 2015-09-22
I just opened up the case of my computer and disconnected the hard drive. Then i started the PC and "ubuntu" boot option is still there, without Hard hard drive. Anyone knows how to delete it? Or completely restore factory settings. (pull the battery out didn't help). **Flashed the motherboard and got rid of it!**

---

