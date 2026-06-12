---
title: "Bootup Problem. Alert! /dev/disk/by-uuid... does not exist"
date: 2012-03-04
forum: Installation &amp; Upgrades
---

### Post by ScientificProp on 2012-03-04
I just tried to install Ubuntu 11.10 after verifying that everything works properly by testing with a LiveUSB setup. The LiveUSB boot works properly and I then successfully installed the NVidia driver 290.10 for my GeForce 520 graphics card.
The full install, onto an external USB HDD, however won't successfully boot. I put Grub2 onto the USB drive and select it from the BIOS boot options. The normal boot stalls with a blank screen. A bootup with the recovery option provides more feedback, the last message is:
[2.276032] usb 2-1: config 1 interface 0 altsetting 0 endpoint 0x81 has an invalid bInterval 0, changing to 32.
Gave up waiting for root device. Common problems ....
Alert! /dev/disk/by-uuid/a77f81e8-1163-4e88-816e-3bde661f7b5c does not exist
Dropping to a shell!

Then I get a message that BusyBox v1.18.4 (Ubuntu 1:1.1..4-2ubuntu2) has loaded.
At this point I don't think the kernal has loaded, I'm not sure what BusyBox is.
I am also not sure what the device is that seems to be causing a problem.

Thanks, ScientificProp

---

### Post by darkod on 2012-03-04
It seems to complain that it can't find the partition with that UUID. Boot into live mode and check the UUIDs with:
sudo blkid

See if that UUID is correct for your root partition.

Also, you can post the results of:
sudo fdisk -l (small L)

You can try to reinstall grub2 to the MBR, it can't hurt.

---

### Post by ScientificProp on 2012-03-04
Thanks darkod, that's the information I was hoping for.
I ran sudo blkid and see that the uuid that was listed in the alert is associated with a logical partition on the hard drive that is connected by a USB cable, a 250MB drive. Specifically is it listed for /dev/sdc6 and is an ext4 format. I also ran the fdisk command as you suggested and sdc6 is associated with a Linux partition.
BTW, the commands were run from a LiveUSB boot (on a flash drive) with the external USB HDD connected to the system. I had tried to boot from the USB HDD both with and without the Flash drive (with the LiveUSB) connected to the system.
The output of the commands follow:
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="45998ddf-01e6-464a-94a5-7ba2eddaea49" TYPE="ext3" 
/dev/sda1: LABEL="HP" UUID="B2147F89147F4EFB" TYPE="ntfs" 
/dev/sda2: LABEL="Recovery" UUID="2C88743C8874071C" TYPE="ntfs" 
/dev/sdc1: UUID="c01a65d2-e5fe-449c-b7cc-39679ae46063" TYPE="ext2" 
/dev/sdc5: UUID="57927473-1533-42e8-88ac-582ea589b180" TYPE="swap" 
/dev/sdc6: UUID="a77f81e8-1163-4e88-861e-3bde661f7b5c" TYPE="ext4" 
/dev/sdc7: UUID="ee70c739-8b1b-4123-9d81-42115ed083da" TYPE="ext4" 
/dev/sdd1: LABEL="M-^IPNG^M^J^Z" UUID="122A-7325" TYPE="vfat" 
/dev/sdi5: LABEL="HP Personal Media Drive" UUID="0858A6AD58A69948" TYPE="ntfs" 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb6b4f0ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   958229054   479114496    7  HPFS/NTFS/exFAT
/dev/sda2       958229055   976768064     9269505    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000917b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048      976895      487424   83  Linux
/dev/sdc2          978942   360351743   179686401    5  Extended
/dev/sdc5          978944     8790015     3905536   82  Linux swap / Solaris
/dev/sdc6         8792064    67383295    29295616   83  Linux
/dev/sdc7        67385344   360351743   146483200   83  Linux

Disk /dev/sdd: 16.2 GB, 16231956480 bytes
64 heads, 32 sectors/track, 15480 cylinders, total 31703040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00025add

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          32    31703039    15851504    c  W95 FAT32 (LBA)

Disk /dev/sdi: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x32b8ff8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1           16065   976768064   488376000    f  W95 Ext'd (LBA)
/dev/sdi5           16128   976768064   488375968+   7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ 

Thanks, ScientificProp

---

### Post by darkod on 2012-03-04
So, the external disk is the 250GB /dev/sdc?

There are cases that the system doesn't see the usb hdd fast enough, and hence it reports the UUID as missing.

Also, since you have a number of Linux partitions on /dev/sdc, do you know which one is root and do you have a separate /boot partition?

---

### Post by ScientificProp on 2012-03-04
I created 4 partitions on the drive, /boot, swap, /root and /home and yes, the external disk is the 250GB disk. The sdc5 partition is listed as the swap which is the partition I created just before creating the /root partition. Then, sdc7 is likely the /home?
BTW, I installed this from the USBLive. Would it have been better to have installed it from a CD?

Thanks, ScientificProp

---

### Post by darkod on 2012-03-04
There should be no difference that you installed from usb stick.

To try and reinstall grub2 to the MBR of /dev/sdc from live mode, in terminal do:

```
sudo mount /dev/sdc6 /mnt
sudo mount /dev/sdc1 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sdc
```

Reboot and let it boot from the external hdd, see if it works.

If it still doesn't work, try this:
Reboot and enter your motherboard boot menu, usually with hitting F12 or similar. After the boot menu shows, wait 5-6 seconds to let the ext disk spin up. Then select the usb hdd as boot device and see if it worked.

---

### Post by ScientificProp on 2012-03-04
Thanks darko, for the help and information. If it is a response time issue, maybe I'll go with my original plan which was to install a 2nd internal SATA hard drive. However, I'd also like to have the option and portability of an external USB drive.

---

### Post by efflandt on 2012-03-04
This puzzles me:

**The LiveUSB boot works properly and I then successfully installed the NVidia driver 290.10 for my GeForce 520 graphics card.**

Even if you have persistent data on the USB with live/install iso, you cannot install things like video drivers or different kernels, etc. (or they will not actually take effect) because the kernel is loaded from a fixed squashfs file system before the rest of the system or persistent data is loop mounted.  That has nothing to do with your boot issue, but is something to be aware of.  You can make settings (timezone, wireless security, etc.) and install programs that run after boot, but anything you try to install related to boot (kernel, video drivers, etc.) will not exist during that part of the boot.

For nvidia you likely need to use **nomodeset** kernel boot parameter if not doing that already.  If I do not use that for GTX550Ti my display says "no signal" after the grub menu.

But you may have a problem that has been a mystery to me for some time.  I have 2 computers that boot fine from relatively large internal drives or 160 GB USB drives, but they refuse to boot from 500 GB USB that boots fine with other computers.  I might expect that for the older desktop from 2004, but not my newer desktop from 2010.

The 2010 Dell desktop has a 1 TB internal drive that boots Maverick (10.10) fine from the last partition sda4 on its internal drive.  It also boots fine from 160 GB USB drive.  But grub2 in the USB MBR has trouble finding the rest of itself (drops to grub rescue) on a 500 GB USB drive.  And even grub2 on my internal drive (where I can get to a grub prompt instead of grub rescue) can list what is in /boot, but cannot properly see what is in /boot/grub on the Ubuntu partition of the 500 GB USB drive.  Both Dell and Toshiba laptops from 2006 have no trouble booting that 500 GB USB drive, it is not a problem with the drive or Linux on it.

Some people mention a 137 GB limit for the BIOS of older computers, but that does not explain why even my 2004 desktop can boot Linux at the far end of the 200 GB drive it came with, but cannot boot a 500 GB USB drive, much less why my 2010 desktop cannot when it came with 1 TB hd.  I never got around to seeing if putting a /boot partition at the beginning of the USB drive would help, but that is where yours is.

So it is still a mystery to me what that USB drive size cutoff point is for some computers that can easily handle a larger internal drive.

---

### Post by ScientificProp on 2012-03-04
Efflandt,

Although I've worked on computers for 30 years, I'm only just learning the details of Linux and Ubuntu so I'm not sure I can fully comment on your post. I did install the NVidia 290.10 driver and was able to switch to higher resolution video mode as a result, that video mode has persisted. I cannot specifically verify that the NVidia driver is still installed  - not sure of the commands or programs to use.
As for the drive question. I'm still investigating. I reinstalled grub per darko suggestion, but it didn't help, nor did waiting to select the boot option. I should add, however, that the 2.5" laptop HDD that I put into the external USB enclosure is questionable. My daughter (who is not computer experienced) said it was not working, so I bought her a new USB 3.0 portable hard drive (yes, my daughters have Dad wrapped around...). Then, I connected the drive she said wasn't working to my computer, it worked so I copied the pictures and stuff to my network drive and tried to use it for Ubuntu.
So, maybe the drive itself is a potential problem. But, it seems like it's being recognized by the system so I would think that means that it's working.
Which brings me back to your comments about drive size and the miscellaneous observations you quoted. Not sure what it could mean.
I plan to try the external USB HDD on my wife's laptop...

Thanks for sharing your observations. ScientificProp.

---

### Post by ScientificProp on 2012-03-04
To Darko:
I re-installed grub, per your instructions and booted from the bios (with a delay), nothing worked. I got the same error message about sdc6. I will try to connect the external drive to my wife's laptop and see if it'll get a different result.

Thanks again, ScientificProp

---

### Post by ScientificProp on 2012-03-05
I tried booting up the Ubuntu 11.10 partition on the external USB drive, but this time on a different computer - my wife's laptop. Same result (it didn't work) for the same reason (message that the uuid) does not exist?
Could this be due to a problem with the hard drive itself?

Thanks, ScientificProp

---

### Post by darkod on 2012-03-05
In theory it should work fine, but since it doesn't you can disable the search for the UUID. That should ignore this message and continue booting your ubuntu.

Instructions how to boot once (step 1) and how to disable the search permanently (step 4) are here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

### Post by ScientificProp on 2012-03-05
I followed the instructions from the sourceforge site and deleted the line, "search --no-floppy ...".
That did not work. When I continued the boot (after the line was deleted) I got an error message 
"error: file not found"
The error message would only be displayed for about 30 seconds, then the system would go directly into the edit grub mode. The error seemed to occur at the line
"linux /vmlinuz-3.0.0-15-generic root=UUID=a77f81e8-1163-4e88-861e-3bde661f7b5c ro recovery nomodeset"
I say that because the screen did show the results from an echo statement which was the preceding line.

ScientificProp

---

### Post by ScientificProp on 2012-03-05
So, I reviewed my notes and wrote down the contents of the grub edit menu when it opens (I assume this is what it is starting with). The search line, that I attempted to delete, contains a reference to a UUID with the code,
"search --no-floppy --fs-uuid --set=root c01a65d2-e5fe-449c-67cc-39679ae46063 "
then two lines after, there is the line
"linux /vmlinuz-3.0.0-15-generic root=UUID=a77f81e8-1163-4e88-861e-3bde661f765c ro recovery nomodeset"
So, my question, why are there 2 references to a root with 2 different uuid values?
The uuid ending 46063 is the uuid for the ext2 partition I created for the /boot partition.
The uuid ending f765c is the uuid for the ext4 partition I created for the /root partition.

Could I be having this boot problem because of something I did incorrectly when I created the partitions?

ScientificProp

---

### Post by ScientificProp on 2012-03-05
Another observation (going back to my original post): When the boot fails (in a recovery boot) I get a message about a problem
usb2-1: config 1 interface 0 altsetting 0 endpoint 0x81 has an invalid bInterval 0, changing to 32.
What does that mean? The message after this last statement says it gave up waiting for the root device.
Unfortunately, I assume there is no screen dump feature or way to look back at the entire bootup sequence of messages.

I wishing I could just get this working.

ScientificProp

---

### Post by darkod on 2012-03-06
The two different UUIDs are because of the separate /boot partition.

But that fact itself shouldn't be a problem for it to work. You can install with separate /boot although it is very rare for home desktop, even for servers.

I can't think of anything else.

If you feel like it, you can try installing once again, this time without the separate /boot. And if there is still problem with the search line, at least there will be only one UUID search to sort out, the / partition UUID.

I don't know what else to suggest.

---

### Post by Quackers on 2012-03-06
You could try the following to confirm whether it is a time related problem (to do with the amount of time it takes the usb HDD to spin up or to be recognised).

From the grub menu (tap the shift key during boot if you don't get the grub menu by default).
With the Ubuntu entry highlighted press the "e" key.
On the next screen navigate to the end of the kernel line (where you put the nomodeset boot option) and add this ```
rootdelay=30
``` then press ctrl + X to boot.

This will give the system an extra 30 seconds to find the required UUID.

---

### Post by ScientificProp on 2012-03-06
Quackers- thanks for the suggestion, it was listed as a potential fix in the bootup error message, but I didn't know how, or where, to add the rootdelay command. Good suggestion, but it didn't help - I got the same bootup error message. I think I can rule out that it's the USB since changing the delay didn't work, I tried to boot up on a different computer - a laptop, and that didn't work.

Next, I guess, is as Darko suggested, to reinstall with a simpler partition setup. Without the separate /boot partition. I wanted to try it this way because I read (somewhere) that it was a good route to use if I wanted to install multiple Ubuntu systems on the same drive. I'd also like to try CAELinux which I read about and is based on 10.04. The goal was to have both on a portable format. Can I still do this without a separate /boot partition. I assume in that case I would have /, swap and /home partitions? How large should the / be for both / and /boot?

Thanks, ScientificProp

---

### Post by darkod on 2012-03-06
The boot folder (when it is only a folder inside /) does not affect the / size at all. The files inside /boot reach up to 100-200MB usually. Don't even bother thinking about it.

In fact, for multiple installs I am not sure separate /boot is good (but I might be wrong). Depending what linux OSs you want to install, having boot files on same partition might interfere between versions.

Also, after you install your ubuntu with /, swap and /home, I guess it's best to make different /home for the other installs, or in fact leave it inside / for them. The reason is the same, interference between different types of linux. I am not sure how that would work but have never tried it either.

One thing is for sure, all linux installs can use the same swap space since you only have one OS booted at the same time, so it takes over the use of the swap space.

So, if you plan ubuntu to be your main install, you might consider something like (again, the final decision is up to you and depends on your usage of your computer):
For ubuntu
/
swap
/home (as big as you plan to use)

For linux2
/
(it can use the same swap)

For linux3
/

etc...

---

### Post by Quackers on 2012-03-06
ScientificProp, when you get to the initramfs prompt try leaving it for a short time then typing in EXIT and press enter. Does it then boot?
I suspect it won't, but it's worth trying.

---

### Post by ScientificProp on 2012-03-07
Correct. It didn't work either. I repeated the error message and brought me back to the same propmpt.

---

### Post by ScientificProp on 2012-03-07
I re-installed Ubuntu 11.10 with a simplified partition architecture (no /boot partition), but it still failed to boot-up!? 

I started over and created /, swap and /home partitions. Their sizes were 30000MB (30GB), 4000MB (4GB) and 150000MB (150GB), repectively in a 250 GB drive. The install seemed to proceed as it should, but I got the same bootup error message when trying the recover boot option. I didn't have time to do any detailed checks, but it seems like the same problem. The diskutility program indicates that the hard drive in the external USB enclosure is working properly?

Is there something about the computer and it's USB ports that is creating some compatibility issue? It's an HP Pavilion Media Center TV m8100n Desktop with Athlon 64 X2 (W) 5600+ 2.8 GHz processor. The existing hard drive is a 500 GB SATA 3G (3.0 Gb/sec), 7200 rpm. I replaced the onboard video with an NVidia GeForce 520 card.

I'm thinking I may have to add a 2nd hard drive (I'd rather not mess with the Windows drive).

Thanks, ScientificProp

---

### Post by ScientificProp on 2012-03-08
I'm still stuck on this problem, I've tried a few other install combinations. Simplifying the partition configuration to 3 partitions (/, swap and /home) did not change anything. Same boot error message, "/dev/disk/by-uuid... does not exist". I have found a couple other threads that reported the same boot error message, although one of them believes the cause to be related to a softraid program (I don't know what that is), see the following thread.

[http://ubuntuforums.org/showthread.php?t=1653682](http://ubuntuforums.org/showthread.php?t=1653682)

Why does the LiveUSB boot fine, but not the OS installed to a USB harddrive? I tried to install without doing the simultaneous updates - in case there's a key difference. But, it didn't change anything, I got the same boot error messages. I tried repeatedly entering exit at the initramfs command prompt as suggested by someone in the above refrenced thread, but the boot process never restarted.
The OP of this thread suggesting adding a command #update-initramfs -a (someone added it should be -u instead of -a (?)). I don't know where this command is supposed to be added? He was thinking it dealt with a problem with softraid, would it also work in my situation?

Next is to try to install 11.04 onto the USB HDD, but this time from a CD. I could also try installing Ubuntu onto a USB Flash drive, I think I have a spare 16 GB flash drive available?
I could try installing 11.10 onto the same USB HDD, but from a different computer?

Does anyone have any other ideas?

Thanks, ScientificProp

---

### Post by oldfred on 2012-03-08
Post link to latest run of boot info script from Boot-Repair.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

What mode is BIOS in. You should have drives set to Large or LBA not IDE unless it is an old system with IDE drives.

---

### Post by ScientificProp on 2012-03-08
I seem to have solved the problem, apparently you cannot install ubuntu onto a USB HDD from a LiveUSB boot. I have always been installing from my LiveUSB Ubuntu 11.10 boot. Early in this thread it was suggested that switching to an install from a CD boot should not make a difference. Well it did. First, I successfully installed and booted from Ubuntu 11.04 from a CD boot, then I reinstalled and booted Ubuntu 11.10 64 bit from a CD.
From all that was said, it should not have made a difference. I don't know? Maybe this behavior is unique to my HP computer? However, there are a few others who have received the same error message while trying to boot. I believe one of them had also installed from a LiveUSB boot.
So, my initial problem has been solved and I have installed Ubuntu 11.10 onto a USB HDD.

---

