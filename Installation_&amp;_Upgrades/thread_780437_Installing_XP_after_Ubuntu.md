---
title: "Installing XP after Ubuntu"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by ilmalcom on 2008-05-03
Hello, that's the first time I try Ubuntu and for now I'm really satisfied :-) but for the first time I had to install Linux before Windows on my PC, since I needed to save a lot of data from my old Linux partitions.

Now I installed Ubuntu on sda, using the entire disk, and I'd like to install XP on sdb, using the entire disk, but it seems I can't, because when I try to install XP I get an error such "I can't continue the installation, because I can't write some data on the PRIMARY disk".

Is there something I can try before disconnecting the primary disk and install on the secondary? Thanks in advance

---

### Post by Pumalite on 2008-05-03
This might help:
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by ilmalcom on 2008-05-03
> **Pumalite said:**
> This might help:
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)
Uhm it is for installing XP on the same disk as Ubuntu, I'd like to install it on the secondary disk (the procedure differs)

---

### Post by Pumalite on 2008-05-03
Do you have 2 SATA HDD, 2 IDE or a mix?

---

### Post by mdlueck on 2008-05-03
At least the volume license CD of XP Pro SP2 refuses to even boot when it detects Linux on the HDD... not sure exactly what it sniffs, maybe the filesystem, maybe Grub as the MBR.

My method of hand installing dual boot WinXP / Linux is to first install XP on a Primary partition at the front of the disk. Then add Linux, allow it to install Grub at the MBR, and the Grub menu will have a selection on the menu to boot Windows.

---

### Post by ilmalcom on 2008-05-04
> **Pumalite said:**
> Do you have 2 SATA HDD, 2 IDE or a mix?
2 SATA

I know it would be a better idea to install XP first, but I couldn't, it seems impossible to me there's no decent solution :)

---

### Post by bulldog on 2008-05-04
> **ilmalcom said:**
> 2 SATA

I know it would be a better idea to install XP first, but I couldn't, it seems impossible to me there's no decent solution :)

Make the windows hdd the first boot disk in your BIOS,or disconnect the ubuntu hdd.
Install windows and set the ubuntu hdd as the first boot disk again and the windows hdd as the secundary.
Open your menu.lst and add the windows entry like this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by ilmalcom on 2008-05-04
> **bulldog said:**
> Make the windows hdd the first boot disk in your BIOS,or disconnect the ubuntu hdd.
Install windows and set the ubuntu hdd as the first boot disk again and the windows hdd as the secundary.
Open your menu.lst and add the windows entry like this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
I just installed Windows XP following your advice and it seems ok :) Now I'll try to boot Windows from Grub when I reboot, but the installation went fine. I really thank you for your reply ;-)

---

### Post by Luke771 on 2008-05-04
Just install windows in its partition.
It will overwrite the MBR and your system will boot straigh into Windows rather than the boot loader.

Here's the trick:
BEFORE you install Windows, get Super Grub [** CLICK HERE**](http://supergrub.forjamari.linex.org/).
Download the image, burn it to a CD using the 'burn image' feature to preserve bootability.


NOW, install Windows.
-After installing, reboot with SuperGRUB in the tray.
-Use SuperGRUB to restore the GRUB boot loader (it's easy, I promise: just boot from SuperGrub and follow the on-screen instructions)

SuperGrub will restore GRUB as it was before installing Windows. Now you need to add Windows to the boot loader.
Open a terminal and run:
```
sudo gedit /boot/grub/menu.lst
```
Add this entry to the bottom of menu.lst:
```

title		WINDOWS
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

You may need to modify it to match your windows partition. Mine is written for Windows installed in sda1, i.e. the first partition of the first (SATA) disk.
For Windows installed in the second partition of the second disk, the line

root (hda0,0)

would have to be 

root (hd1,1)

and for Windows installed in the third partition of the first disk, the line would be: 

root (hda0,2) 

Got it? 
The part in parentheses after 'root' means (<partition>, <disk>) and counting starts from zero rather than from one.

---

### Post by Luke771 on 2008-05-04
Oh. I just wrote a useless post.
I hope it will be useful so someone else.

---

