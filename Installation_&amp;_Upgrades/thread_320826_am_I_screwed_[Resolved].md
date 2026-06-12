---
title: "am I screwed? [Resolved]"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by Daboo on 2006-12-18
I have a standard dual boot setup. Due to viruses, my windows partition got really messed up, so I ran windows setup to restinall it. I noticed the setup wasn't showing 2 partitions, so I quit before install and rebooted. Bam, my MBR was gone. I used a live cd and tried in vain to restore the MBR, but ubuntu was not detecting the drive. I then decided to run a windows repair. I tried a fixmbr at the prompt, that didn't help. I then tried a fixboot. Now, I think I f'ed up the partitions as I get "invalid partition table." Is there any way I can recover my data from either drive?

---

### Post by aysiu on 2006-12-18
I have no idea how to use it, but the program you want is GPart (different from GParted).

---

### Post by Daboo on 2006-12-18
Cool, I'm getting somewhere now:

gpart worked and I can see both my partitions:

xp on /dev/sda1 
unbuntu on /dev/sda2

I tried installing smart boot manager (from knoppix live cd):

sudo ./sbminst -d /dev/sda

and it said successful. Upon reboot, after post I get a black screen. 

I then tried installing GRUB:

grub-install /dev/sda

Could not find device for /boot: Not found or not a block device.

Ideas? Thanks.

---

### Post by Daboo on 2006-12-18
fixed! Via this thread:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I was able to get GRUB reinstalled. The ironic thing is, I wouldn't have gotten grub installed if I hadn't wrecked then fixed the partition table with gpart. Thanks for the tip aysiu!

---

### Post by nalmeth on 2006-12-18
This help?

[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

EDIT: 
Fine, nevermind then! 

:D

---

