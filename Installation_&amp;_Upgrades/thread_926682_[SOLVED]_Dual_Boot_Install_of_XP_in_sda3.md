---
title: "[SOLVED] Dual Boot Install of XP in sda3"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by pwaugh on 2008-09-22
I just re-installed from scratch, and setup the following

sda1 /boot
sda2 swap
sda5 / (logical)
sda3 unused

and I want to now re-install XP (dual boot) in sda3.  How do I do this?  Do I just stick in the CD, and then point to the partition?

I did install Grub (I think) during the initial install in the "advanced" options.

Patrick

---

### Post by Pumalite on 2008-09-22
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by prshah on 2008-09-22
> **pwaugh said:**
> I just re-installed from scratch, and setup the following

sda1 /boot
sda2 swap
sda5 / (logical)
sda3 unused

and I want to now re-install XP (dual boot) in sda3.  How do I do this?  Do I just stick in the CD, and then point to the partition?

I did install Grub (I think) during the initial install in the "advanced" options.

Patrick

First, into ubuntu and backup your MBR (master boot record). ```
sudo dd if=/dev/sda of=/root/mbrbackup bs=446 count=1
```

Next, boot off your Windows XP CD, and, during installation, select the (empty) partition. If Windows does'nt use the empty partition, delete only that partition, and create a new partition in the unallocated space, and continue with the XP installation.

When you've finished, you will lose the ability to boot into Ubuntu. At this point, boot off the ubuntu live CD and restore the MBR```

sudo mount /dev/sda5 /mnt -o ro
sudo cp /root/mbrbackup /
sudo umount /mnt
sudo umount /dev/sda1
sudo umount /dev/sda3
sudo swapoff -a
sudo dd if=/mbrbackup of=/dev/sda bs=446 count=1
sudo reboot

```

After this, GRUB will load, but only with options for ubuntu. Boot into ubuntu, and edit the "/boot/grub/menu.lst" file to add the options for your Windows XP installation, below the line which contains "### END DEBIAN AUTOMAGIC KERNELS LIST"```


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Microsoft Windows XP
root		(hd0,2)
savedefault
makeactive
chainloader	+1

```

Save the file, go to a terminal, and give the command```
sudo update-grub
```, then, on the next reboot, you should see your Windows XP entry and should be able to boot it!

Post back if you run into any trouble.

The information given here is very dangerous; a single mistake can wipe out your data, in a fraction of a second. I have reviewed it, and as far as I can see there are no errors; but you still perform these at your own risk. Perhaps you can wait for someone else to confirm the steps before you carry them out.

Good luck!

---

### Post by caljohnsmith on 2008-09-22
> **prshah said:**
> 
The information given here is very dangerous; a single mistake can wipe out your data, in a fraction of a second. I have reviewed it, and as far as I can see there are no errors; but you still perform these at your own risk. Perhaps you can wait for someone else to confirm the steps before you carry them out.

Good luck!
As far as I can tell, it looks like your steps would work just fine, prshah, but I think it is a bit more trouble then necessary; also (as you point out) it is a little risky because of the "dd" command you used. :) Instead of backing up the MBR and restoring it with all those steps, I think a simpler, safer way would be to just reinstall Grub after the Windows install with these steps (no need to backup the MBR beforehand):
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
The above will reinstall Grub to the MBR and point it to sda1 for all its system files like menu.lst.

---

### Post by pwaugh on 2008-09-22
Thanks guys.

Not only was Ubuntu the easiest OS install ever, it has certainly been the easiest OS re-install ever.

I also will now partition in a way that will let me easily backup /home.

My girlfriend in Poland thanks you too, because she doesn't have to wait 2 days to see me again on Skype.  :lolflag:

Cheers

---

### Post by prshah on 2008-09-22
> **pwaugh said:**
> 
My girlfriend in Poland thanks you too, because she doesn't have to wait 2 days to see me again on Skype.

(Totally offtopic: [Typing in Polish on an English system (how?)]("http://ubuntuforums.org/showthread.php?t=926550"))

If you feel this problem is solved, then click Thread tools near the top right of the page, and click "Mark thread as solved".

EDIT: Hang it all, I just realized that other thread's yours as well! Well you can mark that solved as well, if it works for you (it should!)

---

### Post by pwaugh on 2008-09-22
Well, I spoke tooo soon...

I put in my WinXP disk, and get the "Setup is inspecting your system..." message, but then after a couple of seconds the screen goes blank and the HD never goes off.

When I re-created the partition table, I did not initialize the empty partition, because there was only FAT32, no NTFS option.  Could this be why it is dying?

Ideas?

P.S.  Thanks for the reminder about marking posts solved... will do.

Patrick

---

### Post by caljohnsmith on 2008-09-22
If you use the Ubuntu partition editor (gparted) you should be able to format that partition to NTFS. Try booting your Live CD, press ALT + F2, type:
```
gksudo gparted
```
And try using that. Let us know how it goes.

---

### Post by pwaugh on 2008-09-22
> **caljohnsmith said:**
> If you use the Ubuntu partition editor (gparted) you should be able to format that partition to NTFS. Try booting your Live CD, press ALT + F2, type:
```
gksudo gparted
```
And try using that. Let us know how it goes.

That allowed me to format the partition NTFS, but still no joy on booting from the win CD.

Perhaps the last partition is to far out on the 300 G disk for windows?  Not sure what else to do other than maybe kill the partition table and see if windows will now recognize the disk and then put it in the first partition.

---

### Post by caljohnsmith on 2008-09-22
Is the partition you formatted to NTFS a primary partition? Also, is your HDD SATA maybe? If it is SATA, I think you have to use special SATA drivers with the Windows Install CD to get Windows to recognize the HDD. Also, if you also just installed Ubuntu, it would probably be more ideal to make an NTFS partition at the beginning of the HDD for Windows like you mentioned (I'm not sure it will help, but it certainly won't hurt); so instead of moving things around, if you did just install Ubuntu, you could just wipe the HDD clean and start over. That would make it easy to put Windows at the beginning of the drive.

---

### Post by pwaugh on 2008-09-22
> **caljohnsmith said:**
> Is the partition you formatted to NTFS a primary partition? Also, is your HDD SATA maybe? If it is SATA, I think you have to use special SATA drivers with the Windows Install CD to get Windows to recognize the HDD. Also, if you also just installed Ubuntu, it would probably be more ideal to make an NTFS partition at the beginning of the HDD for Windows like you mentioned (I'm not sure it will help, but it certainly won't hurt); so instead of moving things around, if you did just install Ubuntu, you could just wipe the HDD clean and start over. That would make it easy to put Windows at the beginning of the drive.

Hey, worked like a charm after I just killed the partition and put the Windows partition at the beginning of the drive.  Thankfully, I remembered from years ago that it needed to be so.

All up and running, now thanks.  Was still the easiest re-install I've ever had to do, with the live CD available.  Also, made easier by doing Windows first as then Grub gets installed without extra effort.

Patrick

---

### Post by caljohnsmith on 2008-09-22
> **pwaugh said:**
> Hey, worked like a charm after I just killed the partition and put the Windows partition at the beginning of the drive.  Thankfully, I remembered from years ago that it needed to be so.

All up and running, now thanks.  Was still the easiest re-install I've ever had to do, with the live CD available.  Also, made easier by doing Windows first as then Grub gets installed without extra effort.

Patrick
Great, glad to hear you got Windows to install OK. Cheers and have fun. :)

---

