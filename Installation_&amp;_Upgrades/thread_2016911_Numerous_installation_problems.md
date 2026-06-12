---
title: "Numerous installation problems"
date: 2012-07-04
forum: Installation &amp; Upgrades
---

### Post by ksteuber on 2012-07-04
I have been having a number of problems installing Ubuntu Server 12.04 on my desktop computer.
Originally, I had a RAID0 array with Windows installed. I wanted to dual boot, and I decided to undo the RAID and put one operating system on each drive. I went into the BIOS and changed HDs from RAID to AHCI mode.

Then I installed Windows 7. The installation seemed fine, but the installer said it could only find one of the two hard drives. Since I only needed one, I ignored this. After installation, Windows was able to detect that there was a second hard drive.

I loaded the Ubuntu installer, which found both hard drives. I used the partition layout that I have always used:
200MB EXT2 partition mounted at /boot (sda1)
several gigabytes of swap (sda2)
remaining space in an EXT4 partition mounted at / (sda3)
The installer said that it would install GRUB and that no other operating systems had been found. This is wrong, since there is another operating system, but I figured I could fix it later.

After installation, I restarted and was taken to Windows without ever seeing GRUB. I went in the BIOS and changed the other HD to be first in the boot order. Then ubuntu started, but complained 
> The disk drive for /boot is not ready yet or not present. 
Continue to wait, or Press S to skip mounting or M for manual recovery.
If I press S for skip, the system seems to load. The only apparent problem is the message
> mountall: Plymouth command failed
mountall: Disconnected from Plymouth

However, I am experiencing these odd problems:
[LIST]
[*]I can use ls to see that the /boot folder very much exists and contains just the folder "grub"
[*]Both mount and ls insist that /dev/sda and /dev/sda3 exist, but do not see /dev/sda1, which should contain /boot.
[*]fdisk -l /dev/sda shows the three partitions that it should: sda1, sda2 and sda3
[/LIST]

I tried reinstalling ubuntu entirely, but that did not seem to change anything whatsoever.

I think I can deal with getting GRUB to boot Windows on my own, but I cannot figure out what happened to /dev/sda1. Does anyone know why I still have a /boot folder and what happened to /dev/sda1?

Thanks.

---

### Post by Quackers on 2012-07-04
Hi there.
Did you instruct the Ubuntu installer to use /dev/sda1 as /boot?
If not, then your /boot folder will be in /dev/sda3 and Ubuntu should be booting ok from there.

---

### Post by ksteuber on 2012-07-04
I told it to mount the first partition to /boot, use the second partition as swap, and the third to /. 

Also, is there a way I can make sure that it is using the swap? That partition doesn't show up in /dev either, but I have never really messed around with swap partitions before so I wasn't sure if that was normal.

---

### Post by Quackers on 2012-07-04
Ok thanks.
Can you open a terminal and copy/paste this in please and hit enter ```
sudo fdisk -lu
``` and post the output in your next post.
It sound slike /dev/sda1 (and maybe /dev/sda2 ) are not mounting at boot, though I'm not sure why Ubuntu is booting at all if it can't find /dev/sda1.

---

### Post by ksteuber on 2012-07-04
```
Disk /dev/sda: 1000.2GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes/512 bytes
I/O size (minimum/optimal): 512 bytes/512 bytes
Disk identifier: 0x00035576

Device    Boot Start     End         Blocks     Id  System
/dev/sda1  *   2048      391167      194560     83  Linux
/dev/sda2      391168    68751359    34180096   82  Linux swap/Solaris
/dev/sda3      68751360  1953523711  942386176  83  Linux

Disk /dev/sdb: 1000.2GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes/512 bytes
I/O size (minimum/optimal): 512 bytes/512 bytes
Disk identifier: 0xe970f7d1

Device    Boot Start     End         Blocks     Id  System
/dev/sdb1  *   2048      1953521663  976759808  7   HPFS/NTFS/exFAT
```

---

### Post by Quackers on 2012-07-04
That seems to be fine.
One more thing you can try before going down a longer route is to reboot and as soon as it starts to boot keep tapping the shift key on your keyboard.
This should bring up a grub menu.
The top item will be highlighted and this should be your current Ubuntu system.
Press the "e" key and you will see a new screen.
On that new screen, using your down arrow and right arrow navigate the cursor to the end of the kernel line (the one that currently ends with "quiet splash" (without quotes).
After quiet splash press the space bar and then enter "rootdelay=30" - but without quotes.
Then press ctrl + x to boot the machine.
See if that gets rid of the "press S to skip" message etc.

---

### Post by ksteuber on 2012-07-04
none of mine end with quiet splash.
My window looks like this:
```
setparams 'Ubuntu, with Linux 3.2.0-23-generic'

recordfail
gfxmode $linux_gfx_mode
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 4fc3f09e-decf-40d8-addd-dbd2e5b00490
linux /vmlinux-3.2.0-23-generic root=UUID=f6b316b2-09e9-49cc-8de6-92335773e8b4 ro
initrd /initrd.img-3.2.0-23-generic
```

Which line is the kernel line? Is it the line that starts with "linux" or the line that starts with initrd?

---

### Post by Quackers on 2012-07-04
You need to reboot first then tap the shift key whilst booting to bring up the grub menu.
Then press the "e" key.
Is that what you've done to get that posted above?

---

### Post by ksteuber on 2012-07-04
yes

---

### Post by Quackers on 2012-07-04
Ok, thanks.
Add "rootdelay=30" without the quotes leaving a space after the ro in the next to last line - the one that starts with "linux".
Then press ctrl + x to boot.

---

### Post by ksteuber on 2012-07-04
Ok, I tried that, but it hasn't changed anything. I still get the same messages and errors including the "Press S to skip" message.

---

### Post by Quackers on 2012-07-04
Hmm I'm not sure why this is happening.
I've asked another forum member to take a look at this problem and offer any advice. Hopefully something will be forthcoming.

---

### Post by drs305 on 2012-07-04
Grub sometimes gets confused when RAID has been removed from a system. It seems to find 'bits' of the old installation. I don't recall what the symptoms are since I've never used RAID, but the following commands will remove the RAID remnants.

If you are sure you are not using RAID:

```
		
sudo dmraid --raid_devices -v  #Check for RAID , but run the rest anyway.
dmraid -an 	# activate RAID no
dmraid -si	# sets RAID inactive
sudo dmraid -E -r /dev/sda  # Erase metadata from RAID devices
sudo dmraid -E -r /dev/sdb
sudo apt-get remove dmraid

```

---

### Post by ksteuber on 2012-07-04
You are my hero!

I think that all worked. I still need to get grub to work the way I want and get it to recognize windows, but I have done that before and I think I can do it myself.

---

### Post by Quackers on 2012-07-04
That's great to hear! Those are new symptoms to me for that problem. Thanks drs305 :-)
Your Windows system should show up when running ```
sudo update-grub
``` in the terminal.

---

