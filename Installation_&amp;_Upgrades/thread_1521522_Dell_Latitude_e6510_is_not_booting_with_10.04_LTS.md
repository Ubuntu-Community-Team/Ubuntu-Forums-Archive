---
title: "Dell Latitude e6510 is not booting with 10.04 LTS"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by ramsrambo on 2010-06-30
Need to understand which version to install on this core i7 720QM (i686) machine with bluetooth, wifi Intel centrino 6200, nvidia 3100 NVS 

In the past tried installing 64bit, 32 bit 9.10 and 10.04 none of these versions boot the machine.

If none of the versions are available let me know the time estimate for releasing for an i686 cpu (Intel P6)

---

### Post by ramsrambo on 2010-07-03
Looks like nobody wanna try answering this

---

### Post by thegreatrhino on 2010-07-04
Its quite possible to make work. I am using what appears to be the same laptop you are to make this post:

~$ sudo lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04 LTS
Release:	10.04
Codename:	lucid


~# dmidecode |egrep '6510|Q 720';uname -a
	Product Name: Latitude E6510
	Version: Intel(R) Core(TM) i7 CPU       Q 720  @ 1.60GH 
Linux slim 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux

What you need is the 64bit version of 10.04. 

I would wager that the system actually is working but is having some sort of issue during start up or is not properly loading the display.

For what its worth I had some minor issues with the display on mine in that the default install did not like my display (I went for the 1900x1080).

First see if you are actually booting or not. Try hitting ctrl+alt+<F6> for example. If you can login here than your system is booting and you have what is very likely an X problem. If its not pop in a rescue disk and see if you have any relevant logs. Step one in fixing a problem is understanding what the problem is.

---

### Post by dbuell on 2010-07-25
This may help you. I'm not sure if it is limited to 64-bit systems or not.
[http://ubuntuforums.org/showthread.php?t=1509957&highlight=e6510](http://ubuntuforums.org/showthread.php?t=1509957&highlight=e6510)

---

### Post by bach on 2010-08-25
See 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453)

and

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453)

---

### Post by GenBattle on 2010-08-25
> **ramsrambo said:**
> Looks like nobody wanna try answering this

You need to provide far more information. Does it give an error on boot? does it load anything? does it give a blank screen? does the screen flicker or turn off and on? Provide more information, then you will get answers.

You could be having the same problem as I had, which there are solutions for (by editing the grub entries on boot):
[http://ubuntuforums.org/showpost.php?p=9766336&postcount=8](http://ubuntuforums.org/showpost.php?p=9766336&postcount=8)

---

### Post by ramsrambo on 2010-11-17
Solved this by installing ubuntu 10.10 maverick and it was only a boot param problem.

---

