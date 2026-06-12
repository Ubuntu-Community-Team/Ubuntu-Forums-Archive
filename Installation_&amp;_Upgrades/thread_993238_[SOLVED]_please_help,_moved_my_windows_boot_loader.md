---
title: "[SOLVED] please help, moved my windows boot loader to external hdd while installing u"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by libertarian on 2008-11-25
Hi all,  I STUPIDLY managed to move the boot loader for windows xp to my private USB HDD from my work owned laptop.

In an effort to have my own OS to use at home I stuffed up my work laptop.  Now when I try to load my work laptop with the USB HDD not attached I get a linux grub error message.  My windows laptop will still boot if I have the usb HDD attached.

Can anyone help me before I get skinned alive by my corporate(no sense of humour) collegues tomorrow?

I partitioned the USB HDD in the following way:

/BOOT 15 G
/ 15G
/HOME 100G
/SWAP 2G

/WINDOWS partiion 15G


Is there any quick and easy way to roll back?

---

### Post by linux_tech on 2008-11-25
Best solution is to reinstall GRUB to the external drive and set the windows drive MBR back to normal
To fix the windows mbr, boot to the recovery console and type fixmbr
(it will wipe out Grub and replace it with Windows boot loader) 

You can also use super grub disk to fix the MBR-
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

You can also try this way to fix the mbr
[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

You can re-install Ubuntu to the external HDD. Just unplug the internal HDD, so it will not interfere when you re-install. 

Here's a link for installing on an external hard drive:
[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

---

### Post by caljohnsmith on 2008-11-25
What happened was not really your fault, it is just how Ubuntu is configured to install by default; Ubuntu puts Grub in the MBR (Master Boot Record) of (hd0), also known as /dev/sda, which is usually your internal drive. That way you can just reboot, and voila, you get Grub. But unfortunately, as you have found out the hard way, that is not always what you want. 

You can easily restore a Windows MBR to your internal HDD by booting a Windows XP Install CD, going to the "recovery console" and running:
```
fixmbr
```

EDIT: I see linux_tech just posted the same thing. If you run into problems, let us know.

---

### Post by libertarian on 2008-11-25
Thank you both very much.

I will now try to recover my work laptop before tomorrow!!!

---

### Post by libertarian on 2008-11-26
To give an update,  I had to use the LiveCD method which was by far the quickest.  

I got the WINDOWS blue screen of death for some reason when booting from the legitimate windows install cd!

Supergrub method did not work either as I kept getting an error stating that there was no bootable drive when [I] tried to boot the supergrub...

As a last resort I tried the LiveCD and hey presto it worked!!!!

SO quick and easy!

I will now try to get my external HDD linux bootable now.

Thanks again, for both your help!

:guitar:

---

