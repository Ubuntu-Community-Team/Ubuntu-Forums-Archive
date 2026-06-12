---
title: "Dual Boot w/ WinXP 2hdd Pri IDE Sec SATA"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by ryanchead on 2007-01-16
Hi all,

I'm new to Ubuntu, though I have used linux in the past, mostly red hat.

I am trying to dual boot Ubuntu with Windows XP. I already have Windows installed on an IDE HDD (NTFS), with a secondary IDE (NTFS) used for storage. I would like to install Ubuntu om a SATA HDD, which would be my third.

Unfortunately I do need the second IDE HDD for storage. My wife works with video and photo editing. So, how can I install Ubuntu without touching my windows OS?

As far as I can tell, my BIOS will not allow me to specify whether IDE or SATA should be the primary boot drive.

Thanks for reading.

---

### Post by logos34 on 2007-01-16
> As far as I can tell, my BIOS will not allow me to specify whether IDE or SATA should be the primary boot drive.
I'd doublecheck your motherboard manual or the documentation that came with your computer, or google your board model.  On my board (Biostar TForce) it's buried inside Advanced BIOS features>Boot Sequence & Floppy Setup>Hard Disk Boot Priority>1. Ch. 0 M (my IDE primary master is set as 1st boot device).

If it doesn't you can still install Ubuntu to the sata, but you'll have to put Grub on the MBR of your winxp disk, which will overwrite the windows bootloader.  So you will boot into the first disk, where grub will give you a choice of windows or linux.  (This is in no way permanent as you can always restore the windows bootloader at a later date).  

What motherboard do you have?

---

### Post by mrhealthpatriot on 2007-01-17
In a slightly different setup, IDE (blank, backup drive) was master and secondary master was the SATA with Windows XP, I would have to install GRUB to the MBR of the SATA and not the IDE, then go into BIOS and set the SATA as the first boot disk.

I was thinking that I could install GRUB to the IDE. That way, if I upgrade windows later on, I don't have to worry about reinstalling the GRUB.

I just      playing with the MBR, but my wife needs windows.

---

### Post by ryanchead on 2007-01-20
On further inspection I found a setting in the bios. A hard disk priority setting. So, now I have Ubuntu installed on my SATA, and I just need to know how to set Unbuntu to see the Windows XP install on my IDE, so that I don't have to go into bios every thime to change which OS I boot to.

---

### Post by logos34 on 2007-01-21
If your primary IDE disk was connected at install time, winxp should have been detected and the appropriate entries created in fstab and menu.lst.  If not, add them:

First, backup:
> sudo cp /etc/fstab /etc/fstab_backup

/etc/fstab
> /dev/hda1 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

Then, 
> sudo mkdir /media/hda1

/boot/grub/menu.lst (bottom)
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows XP 
root            (hd1,0)*
savedefault
makeactive
chainloader     +1

*Or (hd0,0) depending on what order grub recognizes your sata and ide drives.  See /boot/grub/device.map. 

Also if the 'timeout' sec entry at the top of menu.lst is set for like 'timeout  0' or '1' then you might want to change that to a few seconds so you actually see the grub menu before it boots the default os.

Now restart and see if you can boot into winxp.

---

