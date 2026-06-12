---
title: "XP/Ubuntu dual boot"
date: 2011-10-04
forum: Installation &amp; Upgrades
---

### Post by bryansheeks on 2011-10-04
I've have a new XP install.  I made a separate partition for Ubuntu and installed it there.  I also have another partition for /swap.  The problem is that when I start my laptop it just boots to XP without giving me the option of Ubuntu.  Any suggestions on how to make ubuntu an option ?  Thanks

---

### Post by cyclonous_gt on 2011-10-04
Bro,
  You could try Wubi (Search it on the Ubuntu homepage) and just installed it inside the WINXP environment and Woala! you have dual booting for both OS.

Note: Wubi is somehow a virtual installation of ubuntu in Windows and it is much more easier.  You need an internet connection during installation of Wubi

---

### Post by bryansheeks on 2011-10-04
Thanks,  I'll give it a try and let you know.

---

### Post by drs305 on 2011-10-04
bryansheeks

Welcome to the Ubuntu forums.  :-)

Please boot an Ubuntu LiveCD (Installation CD) and run the boot info script. Post the contents of RESULTS.txt  This file will show us the status of your boot files.

You can download the script and see how to run it from this link:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by bryansheeks on 2011-10-05
I'll dl and run that script tonight and repost the results. Thanks

---

### Post by vinterkind on 2011-10-05
Did you install WinXP first ?

Is the Bootloader simply hidden ? (press left shift key at the bootup)

@cyclonous_gt
> You could try Wubi 

Why using wubi ?
Then you could use Oracle's Virtual Box too ... (If you like to install OSes into OSes ...)

---

### Post by YannBuntu on 2011-10-07
Hello
please try [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 
 (from Boot-Repair-Disk , or an Ubuntu CD in which you will install Boot-Repair)

---

