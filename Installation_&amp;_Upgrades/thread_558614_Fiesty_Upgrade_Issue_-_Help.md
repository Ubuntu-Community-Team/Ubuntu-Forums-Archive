---
title: "Fiesty Upgrade Issue - Help"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by PhantomWA3 on 2007-09-24
Updated my Edgy installation last night to Fiesty through the little icon that pops up giving you updates, anyway everything went fine but on reboot the Ubunto logo appears and then nothing and after a while I get the following error:

> 
/bin/sh/: can't access tty; job controll turned off
(initramfs)

Cant seem to find a solution to this and am posting this message from work, any help is most appriecated  as I really dont know what to do now.

Thanks.

---

### Post by jnorthr on 2007-09-24
Is there any way you could go back to try booting from a live CD of ubuntu ? If you could get back into your system that way, you could use dmesg command from a terminal to examine the kernel messages for further clues.

Do you have access to or can you burn some CD's to put supergrub on a CD you can boot from ? [http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml](http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml) for that. 

Oherwise you may have a partition problem and a live CD for gparted may be useful to gain more clues. [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)  and take the live Cd route.

---

### Post by Sef on 2007-09-24
Did you use automatix to install any software?

[A possible solution]("http://www.linuxquestions.org/questions/showthread.php?t=474493&page=2") for you:

> I got same error while booting an ubuntu 6.10 machine that worked fine before.

I used the ubuntu live CD to start it. (sorry for those who can't)
and by using:
sudo fdisk -l

I found that mysteriously the name of the hard drive had change.
Before it was hdb and now it is hda

So I mounted the hard drive and corrected the /boot/grub/menu.lst file
I changed
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash

for

kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash

and I did the same for the rescue mode
I reboot the machine and it worked fine again

So if that problem occur after an update or something, it may be good to investigate that option (Like DrewL, may be your trouble is similar)

For those who have this problem with the live CD I'm sorry it's probably different
so I wish you good luck

---

### Post by PhantomWA3 on 2007-09-24
I have a Edgy live cd somewhere, so from there would I just boot into Edgy and then what?

No i never used automatrix.

Thanks.

---

### Post by PhantomWA3 on 2007-09-24
Ok thanks I will give it a try tonight.

Thanks.

---

### Post by PhantomWA3 on 2007-09-24
No the above solution didnt work for me, however I can boot up using the generic kernal from the grub menu.

Thanks for your help, keep it coming :-)

Phantom

---

### Post by PhantomWA3 on 2007-09-24
Got a little more info now, when I boot normally and it hangs and then bombs out to a command prompt if I then press ctrl->F1 there is the following error messge:

```
Check root=bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/hda1 does not exist.  Dropping to a shell!
```

I have managed to boot up using a the generic kernal from grub and once in Ubuntu if I run fdisk -l, i get the following:

```
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30024   241167748+  83  Linux
/dev/hda2           30025       30401     3028252+   5  Extended
/dev/hda5           30025       30401     3028221   82  Linux swap / Solaris

```

So hda1 does exist so why is it complaining?

Hope this helps.

---

