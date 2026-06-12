---
title: "I need help with some Linux terminal commands."
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by wizarddrummer on 2010-07-31
Hi,
   
Since not one person understood my question I will try the question phrased a different way.


I need to know the commands to enter into the terminal to do these three things...

1) fix the mbr of a linux system that does not boot.

2) uninstall grub.

3) re-install grub on the linux hard drive.

---

### Post by wizarddrummer on 2010-08-01
I hope someone can help me.

---

### Post by jerenept on 2010-08-01
You want to check out "Grub2 Guide".
It describes all the you are looking for.
:[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by confused57 on 2010-08-01
Here's a link to your other thread, in case someone else may see your problem and can offer another solution:
[http://ubuntuforums.org/showthread.php?t=1540489](http://ubuntuforums.org/showthread.php?t=1540489)
If your system is capable of booting first to your drive with Ubuntu, you can use section#13 from the link jerenept provided to install grub to it's mbr.  The instructions I gave you in your previous thread should allow you to boot XP when your Ubuntu drive is disconnected, which is what I understood you needed to do.

---

### Post by wizarddrummer on 2010-08-02
> **jerenept said:**
> You want to check out "Grub2 Guide".
It describes all the you are looking for.
:[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Thanks,

reinstalled grub and it's working again.

---

### Post by wizarddrummer on 2010-08-02
> **confused57 said:**
> Here's a link to your other thread, in case someone else may see your problem and can offer another solution:
[http://ubuntuforums.org/showthread.php?t=1540489](http://ubuntuforums.org/showthread.php?t=1540489)
If your system is capable of booting first to your drive with Ubuntu, you can use section#13 from the link jerenept provided to install grub to it's mbr.  The instructions I gave you in your previous thread should allow you to boot XP when your Ubuntu drive is disconnected, which is what I understood you needed to do.

Thanks,

I would just caution people that don't know is that if you have two hard drives; one ubuntu and the other XP only install grub on the hard drive with linux.

I disconnected the XP disk, installed grub while in the live cd mode. this brought the hard drive back where it could boot. 

i connected the xp disk and grub found it.

all is well

---

### Post by confused57 on 2010-08-02
> **wizarddrummer said:**
> Thanks,

I would just caution people that don't know is that if you have two hard drives; one ubuntu and the other XP only install grub on the hard drive with linux.

I disconnected the XP disk, installed grub while in the live cd mode. this brought the hard drive back where it could boot. 

i connected the xp disk and grub found it.

all is well
Thanks for the update.
Good to hear you were able to get your problem solved.  Many people who install Ubuntu to an external USB device experience the same problem, grub's IPL gets installed to the internal drive's mbr & the computer won't boot unless the USB device is connected.

During the installation of Ubuntu, one can click the "Advanced" button & select to install grub's IPL to the Ubuntu drive's mbr(e.g. /dev/sdb).

---

