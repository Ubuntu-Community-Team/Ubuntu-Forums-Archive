---
title: "Unbuntu installed to External USB Drive - Can't boot"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by plomaris on 2006-11-03
First, I am new to Ubuntu.

I successfully installed Ubuntu 6.10 to an external USB drive.  When I did the install, I disconnected the onboard SATA drive to ensure I didn't accidentally install Ubuntu and/or Grub to that drive.  However, it seems now that I reconnected the SATA drive, I can't boot to the external drive.  I did ensure that the USB drive is before the onboard SATA drive in the BIOS boot order.  I just get a message now that the PC can't boot from that drive and to hit F1 to retry or F2 for setup.

I probably have to somehow change some config files on the external USB drive to rename the drive or something.  I do recall in a previous install attemp that it showed up as /dev/sdb when the SATA drive was connected.  It now shows up in the /boot/grub/device.map as /dev/sda.  Can I just change that?

Can anyone assist?

Thanks.

---

### Post by dannyboy79 on 2006-11-03
yes, you'll want to boot up with a live cd and correct your device.map file so that it knows where to retrieve the files from. since there are no boot files on sda ubuntu can't boot so you need to correct this. also, make sure that your fstab is updated and correct as well otherwise it won't know where root is either. fstab probably states sda1 as well for it's root parition. good luck

---

### Post by plomaris on 2006-11-03
Dannyboy:

Thanks for the tip.  Where is the fstab file located?  Are those the only two changes?

Tom

---

### Post by dannyboy79 on 2006-11-03
> **plomaris said:**
> Dannyboy:

Thanks for the tip.  Where is the fstab file located?  Are those the only two changes?

Tom

i'll tell you how to find it since I think it's better to learn than for me to just tell you where it is. this is the code you should run, sudo find / -name fstab
what this will do is using root privalages, it will search your root (/) partition for any file mathcing fstab. once you find it, you'll want to always first make a backup of it, sudo cp filename newfilename. then you'd edit fstab with sudo favoriteeditorhere (examples: nano, gedit) fstab. I believe those 2 changes should do it.

---

### Post by plomaris on 2006-11-03
Thanks Danny, I'll try it.

---

### Post by dannyboy79 on 2006-11-03
> **plomaris said:**
> Thanks Danny, I'll try it.

wait, you might need to update /boot/grub/menu.lst also, looking at that it defines where the kernel is for instance. here is one line from my menu.lst file:

title           Ubuntu, kernel 2.6.15-27-686
root            (hd0,0)
kernel          /vmlinuz-2.6.15-27-686 root=/dev/hdc2 ro quiet splash
initrd          /initrd.img-2.6.15-27-686
savedefault
boot
 notice the hdc2, if you do cat /boot/grub/menu.lst and look towards the bottom, does yours have sda1 there? if so, then you need to change this to sdb1 as well. for each line in your menu.lst file.

also, i have read thru a thread that is dealing with almost the exact same problem where your hard drives are getting mixed up when booting. i am confident that if you read this entire thread, [http://ubuntuforums.org/showthread.php?t=288411&highlight=change+boot+partition+numbers](http://ubuntuforums.org/showthread.php?t=288411&highlight=change+boot+partition+numbers), you will be able to figure it out.

---

