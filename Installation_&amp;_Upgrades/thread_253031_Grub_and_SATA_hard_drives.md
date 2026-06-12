---
title: "Grub and SATA hard drives"
date: 2006-09-07
forum: Installation &amp; Upgrades
---

### Post by sen~ on 2006-09-07
Hi, the hard drive containing my linux installation died recently and I decided to switch from IDE to SATA. However, grub doesn't seem to like SATA... I restored a backup on the new drive, installed Grub to the MBR and updated the menu.lst but when I select the Kernel in the Grub prompt it can't find the kernel:
```
Booting 'Ubuntu, kernel 2.6.15-26-amd64-generic'

root (hd5,0)
Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda1 ro quiet splash

Error 15: File not found
Press any key to continue...
```

Don't wonder about the fact that the root partition is on the sixth hd. The system contains seven hard drives (5xIDE, 2xSATA) and Grub counts the IDE hard drives first.

After checking the grub config a few times I reinstalled Ubuntu on this hd via Live-CD, but even after the installation and the autoconfiguration of Grub by the setup I still get the same error. [-( 

Is there a trick to make Grub boot from SATA drives or is there another solution? If its possible I would prefer not install Grub on one oft the IDE drives and put the boot stuff on it because I want to switch completly to SATA in the near future... that would only be a temporary solution.

Any hints are welcome!

---

### Post by Herman on 2006-09-07
Hello, sen~> Grub error 15 : File not found. This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.Maybe Grub is telling you it can't find the specified kernel. Usually this is because of some small mistake in  your menu.lst file, for example, the exact path or name of your kernel or initrd.img contains an error of some kind.You should be press your 'c' key from your Grub menu to get into Grub's Command Line Interface, to see what I mean by that, [click here.]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")

Grub's Command Line Interface ('CLI') is useful because for each step, you  can see some 'feedback' of what Grub is doing. The following link might help you, [How To Boot Linux from GRUB's CLI]("http://users.bigpond.net.au/hermanzone/p15.htm#How_To_Boot_Linux_from_GRUBs_CLI")  Of course you would replace commands shown in the example with commands that suit your particular hard disk and partition arrangement.
That should boot Ubuntu directly by a symlink to the current Ubuntu kernel. 
You could try testing first to check that Grub can detect a symlink to your kernel for sure and what hard drive and partition it is on by typing 'find /vmlinuz' after the grub prompt as illustrated in that link. Probably it will just confirm your information. if that is correct, then you would use  'root (hd0,5)', and then 'kernel /vmlinuz root=/dev/sda1' With some luck, you will hopefully receive feedback like '[COLOR=#ffffff]**[COLOR=Black][[/COLOR][COLOR=Black]Linux-bzImage, setup=0x1c00, size=0x157812][/COLOR]**[/COLOR]
If you do, then success! You will be able to boot Ubuntu by following the rest of that how-to. That boots Ubuntu by a symlink to the kernel in the root of the filesystem, just in case the exact kernel name has a problem.
If that doesn't work, then maybe the 'dev/sda1' part is where the problem is, but I think that would give error 17 instead, if that was wrong. What ever Grub considers to be your Linux 'root' partition should go there. You can test to verify the location of your 'root' partition by using 'find /sbin/init' after the grub prompt. That is illustrated in the How-To also.  That might be interesting. I don't have a Sata drive myself to try that with. I guess that should still return 'hd0,5', the partition your kernel is on, since Grub notation does not distinguish between IDE and SCSI disks. If that happens you  may need to experiment with what to  replace '/dev/sda1' with. possibly  '/dev/sda6' might be worth a try?  You could try 'cat (hd0,5)/boot/grub/device.map' to see what devices Grub thinks you have.  That should tell you for sure what to replace the 'root=/dev/sda1' part with. 
If you keep notes while you use grub's CLI,  then once you can get Grub to boot Ubuntu using CLI mode, you will know how to edit your menu.lst file to correct whatever the error may have been. However, it is usual to use the exact name and path for your kernel for every-day booting then just the symlink.
 I hope that helps, if not. please ask for more ideas, Regards, Herman :D

---

### Post by sen~ on 2006-09-08
Tank you Herman! The Problem was simple...

I did configure Grub via CLI, but I used the wrong root partition! Now comes the weird thing, when I run Grubs CLI with a root Terminal on a booted LiveCD it tells me:
```
find /vmlinuz
(hd0,0)
(hd5,0)
```
That's why I thought hd5,0 to be the correct root Partition (hd6, first partition). But when I check this before booting the kernel, like you suggested (by pressing 'c'), the same command returns:
```
find /vmlinuz
(hd0,0)
(hd3,0
```
So when booting Grub see the first SATA drive as hd4 and when the system is up it change to drive 6.
The reason for this behaviour musst be my IDE RAID controller! Two IDE hds are connected to it and Grub can't see them before the kernel is up... I haven't thought about that.

Tanks again, the problem is solved! :)

---

### Post by Herman on 2006-09-08
sen~, Thank You for letting me know your solved your problem and providing the excellent feedback.Your answer might help others, I'm happy that you solved it, good work! :)
Regards, Herman

---

