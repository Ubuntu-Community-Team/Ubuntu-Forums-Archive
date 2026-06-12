---
title: "Installing dual boot Precise (12.04) alongside Windows 7"
date: 2012-06-13
forum: Installation &amp; Upgrades
---

### Post by kjaspan on 2012-06-13
Installing dual boot Precise (12.04) alongside Windows 7
=======================================================
This should not be SO DIFFICULT!!!::mad:

In my wisdom I bought a new HP p7-1247c Pavilion 64 bit AMD computer to replace my old trusty Dell E 320, which was running Win XP and recently upgraded Xubuntu 12.04. I have never had trouble with installation before but this has been very frustrating, to say the least.

I initially tried the default installation, installing XUbuntu 12.04 alongside Windows 7. This clobbered the MBR so I had to use boot-repair to be able to access Windows since then. I must note I had an external WD 1tB drive connected.

I could not, after that, access the Xubuntu installation. When I selected Xubuntu from the dual boot menu, I got a grub menu which looked hauntingly like the grub menu from my old computer, which was probably mirrored on my External (backup) drive.

I tried EasyBSD, as in one of the posts in AskUbuntu, to set up a dual boot menu, but I still get the old grub menu, which says the disk is not found and I have to install the kernel. I tried to use this post:
[http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels](http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels)
but that did not help. 

I have also tried several times to follow this post:
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/2/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/2/)

I am running out of ideas, posts and patience!! Please help, someone! This should have been worked out by Canonical and should have been simple.

Kevin

---

### Post by kjaspan on 2012-06-13
I retried the "Something else" installation in the [http://www.linuxbsdos.com/2012/05/17...d-windows-7/2/](http://www.linuxbsdos.com/2012/05/17...d-windows-7/2/)
post but got the grub> prompt. This was using EasyBSD to add my Xubuntu installation as a Grub2 item, with EasyBSD automatically locating the loader (which it found on F:\NST).

If I use EasyBSD to select Grub (Legacy) Loader and specify the Xubuntu boot partition, I just get a blinking cursor.

If I use EasyBSD's default Grub (device automatically detected) with the NeoGrub OS tab, I get the grub prompt again. The loader used was, again, F:\NST

If I specify the boot drive in the Advanced tab, I still get the grub prompt.


I think I have exhausted the simple options.

Why is this so difficult???

---

### Post by darkod on 2012-06-13
No, the simple option is to use grub2 on the MBR. Any reason to insist on windows bootloader and EasyBCD?

Are you sure xubuntu is installed correctly at all? You should run the boot info script (you can do that with boot-repair too since you already used it once) and see what you have and where. Even if grub2 didn't install on the MBR we can help install it.

Use boot-repair again but only to create the boot info results (not to do any repairs) and post the link it gives you.

---

### Post by kjaspan on 2012-06-13
Darko,

Thank you for your reply. Here are the results, attached.

I have been  using Ubuntu for more than 5 years but have never encountered this sort of installation problems.

I look forward to your suggestions.

Once again, I appreciate your help.

Kevin

---

### Post by wilee-nilee on 2012-06-13
You have two 12.04 installs the sda5 could boot it looks like all the grub files are there the sda6 is missing them which one is the one you want?

The sda6 will need the grub files loaded.

---

### Post by oldfred on 2012-06-13
It looks like the fstab for sda6 calls out sda5 as a /boot partition, so it may have overwritten boot files in sda5? 

I normally do not suggest /boot partitions as it just adds this type of confusion.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by kjaspan on 2012-06-13
I don't really care which installation I use though I thought I blew away the previous one. They both should be good Xubuntu 12.04 installations.

So how should I proceed? I really don't have to use EasyBCD - it was only a suggested way from one of the forums to fix the grub dual boot problem. Should I reinstall, without creating a new /boot? I already tried option 1 (Xubuntu installation with automatic partioning) twice and still could not access Xubuntu after installation, as documented in my 2nd post.

---

### Post by kjaspan on 2012-06-13
OK. Suppose I follow Herman's advice and blow away everything but the NTFS partitions and do not specify any ext4 partitions at all. I'm pretty sure I've done that, but could not access Ubuntu following install and reboot. Where will grub go and how will I be able to access both OS's?

Used to be, in Oneiric and before, this was very easy.

---

### Post by wilee-nilee on 2012-06-13
> **kjaspan said:**
> OK. Suppose I follow Herman's advice and blow away everything but the NTFS partitions and do not specify any ext4 partitions at all. I'm pretty sure I've done that, but could not access Ubuntu following install and reboot. Where will grub go and how will I be able to access both OS's?

Used to be, in Oneiric and before, this was very easy.

So you have a number of partitions the extended, sda3 then sda5, sda6, sda7 and a swap sda8.

You can with a live ubuntu cd remove all of them in a from the 8 to the 3 order using gparted on the live cd, make sure no partitions are mounted when you do this. Then install the precise in the free space.

Most of us that help use the something else option this is a custom install. I don't know exactly how that install gui reads now as far as where and how you want the install options

So with a unallocated space I'm not sure if it just asks if you want to use that space, you could do the removals with gparted then when you get there take a screen shot and we could walk you through a custom install or a auto install which you have been using. If you think you want to learn the custom install you can go straight to the install gui and all the manipulations to slip the precise in can be done from the something else option.

If you have anything in the sda7 you want to save do not remove it or the sda3 extended.

The sda3 the exteneded cannot be removed until it is empty anyway but I' m just being cautious as I don't know exactly what you understand or know already, and as a group we want you up and running and happy with all your stuff intact.

---

### Post by kjaspan on 2012-06-13
Thanks wilee-nilee. The auto install does the partitioning automatically. I have used the "somthing else" custom install several times in an effort to get Xubuntu to boot and also to size my own / and /home and make swap 4x RAM size. I don't care. I can (and have) use Gparted to reformat all the space not allocated to NTFS and let the installation do its thing. I am still worried I won't be able to access one or the other OS.

I will do this in the morning (EDT, US) and report on the results.

Kevin

---

### Post by wilee-nilee on 2012-06-13
> **kjaspan said:**
> Thanks wilee-nilee. The auto install does the partitioning automatically. I have used the "somthing else" custom install several times in an effort to get Xubuntu to boot and also to size my own / and /home and make swap 4x RAM size. I don't care. I can (and have) use Gparted to reformat all the space not allocated to NTFS and let the installation do its thing. I am still worried I won't be able to access one or the other OS.

I will do this in the morning (EDT, US) and report on the results.

Kevin

If you have a windows recovery or install disc you could reload the windows boot to be safe, boot the disc to the terminal and run,
```
bootrec.exe /fixmbr
```Here is link on getting to that windows terminal.
                                  [FONT=Verdana, sans-serif][SIZE=1]http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html [/SIZE][/FONT] 
  
If you do not have a recovery or install disc make one asap, in the backup recovery of the admin account in windows, the recovery that is.

We always say have a good backup as well, a clone is a really good thing to have of the windows install.

---

### Post by darkod on 2012-06-14
If you want to use separate /home partition and a swap partition of specific size, I see no reason to use the auto method. In fact, the manual install will always give you more control.

So, just do another manual install (Something Else). But this time, if it doesn't boot by any chance, don't reinstall again, it will rarely help if a new clean install is not working. Instead, be patient and investigate why it doesn't boot.

Also, when making new installs you should be aware and use the same partition(s). Last time it seems you didn't so you ended up with two installs which are just keeping the space.

As wilee says, delete all current partitions, and do a new fresh one with all the partitions you want (/, /home, swap of 4GB, etc). Put the bootloader on the MBR (/dev/sda), not on a partition.

You can delete the current partition either from live mode, or while doing the manual install, it will works that way too. You have the Delete button when it shows you the partitions list, you can delete all that you want, and create the new ones you want. That should be it.

---

### Post by kjaspan on 2012-06-14
Thank you wilee, gracias Darko.

I ran the default (automatic) installation after deleting all ext4 partitions (also removed the EasyBSD reference to Ubuntu), but the installation failed with:

"The 'grub-efi' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot".

I will redo the installation as Darko suggested, with "Something else, etc.".

---

### Post by darkod on 2012-06-14
Strange, why does it want to install grub-efi instead of grub-pc? grub-efi would be used with EFI boot which you don't seem to be using. But something is confusing the installer.

Make sure you have EFI boot disabled in your BIOS, if there is such option. The installer seems to be thinking you are using EFI boot instead of the older type standard BIOS boot, but all other things point towards the BIOS boot. So, I have no idea right now why would it try to install grub-efi.

---

### Post by YannBuntu on 2012-06-14
Hello
the BootInfo you attached is incomplete (eg we cannot see if BIOS is in EFI mode or not).

Please indicate your BootInfo URL: [http://ubuntuforums.org/showpost.php?p=11136267&postcount=1](http://ubuntuforums.org/showpost.php?p=11136267&postcount=1)

---

### Post by martinr on 2012-06-14
> **kjaspan said:**
> "The 'grub-efi' package failed to install

Dear Kjaspan,

Could it be that your new rig uses the new (U)EFI-GTP boot secuence for Win7x64 istead of the old BIOS-MBR way? (Do you see a separate boot partition?)

Furthermore could your 12.04 install have blunbtly overwritter the first sector on your disk (where the MBR used to be), scrambling the GUID Partition Table (GPT) disk in the process? 

I read that EasyBSD is not compatible with EFI, which might have mixed up things even more. 

I also ran into trouble trying to create a dual boot and haven't solved it yet. (see [here]("http://ubuntuforums.org/showthread.php?p=12025501")).

---

### Post by oldfred on 2012-06-14
If you have the new UEFI type BIOS then you should with both Windows or Ubuntu get two choices from the install CD/DVD. One would be legacy/BIOS/MBR and the other UEFI/efi. 

You have to choose the same for both Windows &  Ubuntu. Windows will only boot from gpt partitioned drives with UEFI, but Windows normally still is installed in old BIOS/MBR mode. So then you need to install Ubuntu in BIOS/MBR mode.

Two things tell if UEFI. One is drive will be partitioned with gpt(GUID) not MBR(msdos). The other is the first partition should be the efi partition.

Only if drive does not have Windows (Linux only) can you create a gpt partition scheme and boot with BIOS but then you also need an extra 1MB bios_grub partition.

---

### Post by kjaspan on 2012-06-14
Jeepers guys, such a lot of info. Thanks for all your responses.

Merci Yannbuntu, please see URL  [http://paste.ubuntu.com/1040902/](http://paste.ubuntu.com/1040902/) for the results of my boot info.

Oldfred, Gparted is showing /dev/sda1 as ntfs.

Here is the output of fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x5dc3d822

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   390831847   195312500    7  HPFS/NTFS/exFAT
/dev/sda3       390832126  1953523711   781345793    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       390832128  1937827839   773497856   83  Linux
/dev/sda6      1937829888  1953523711     7846912   82  Linux swap / Solaris

Disk /dev/mapper/cryptswap1: 8035 MB, 8035237888 bytes
255 heads, 63 sectors/track, 976 cylinders, total 15693824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xf1760f35

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

So, I will perform a "Something else" install,as Darko suggested, but do you mean I should put /boot in /dev/sda?

---

### Post by kjaspan on 2012-06-14
Darko,

I understand what you meant. At the bottom of the partitioning window, it says "Device for boot loader installation:" I'm leaving it as /dev/sda.

I specified partitions for /, /home, /usr, /tmp, /opt, /srv, /var, /usr/local but not /boot

Installation has completed. I will reboot and report the outcome in the next message. Hold thumbs!

---

### Post by kjaspan on 2012-06-14
Nope. The installation may have been successful but it does not give me the choice of OSs to boot. It automatically boots Windows.

Here is the output of fdisk -l
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x5dc3d822

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   390831847   195312500    7  HPFS/NTFS/exFAT
/dev/sda3       390832126  1626707967   617937921    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       390832128   454830079    31998976   82  Linux swap / Solaris
/dev/sda6       454832128   650141695    97654784   83  Linux
/dev/sda7       650143744  1040766975   195311616   83  Linux
/dev/sda8      1040769024  1138423807    48827392   83  Linux
/dev/sda9      1138425856  1236080639    48827392   83  Linux
/dev/sda10     1236082688  1333737471    48827392   83  Linux
/dev/sda11     1333739520  1431394303    48827392   83  Linux
/dev/sda12     1431396352  1529051135    48827392   83  Linux
/dev/sda13     1529053184  1626707967    48827392   83  Linux

Here is the output of Bootinfo at this stage: 
[http://paste.ubuntu.com/1041074/](http://paste.ubuntu.com/1041074/)
So should I run boot-repair?

---

### Post by darkod on 2012-06-14
One way or the other, you seem to be booting the ubuntu cd in EFI mode, so it tries to install grub-efi instead of the standard grub-pc. Of course, it fails since you are not running EFI boot.

Boot with the cd in live mode and try this in terminal:
```
sudo mount /dev/sda6 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Just in case, purge grub2 and reinstall it:
```
apt-get remove --purge grub-pc grub-common
apt-get install grub-pc
update-grub
grub-install /dev/sda
```

Exit chroot and unmount all:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

Restart and keep your fingers crossed. :)

---

### Post by kjaspan on 2012-06-14
Darko,

Something is missing. When I enter the command 
sudo chroot /mnt 
I get the message:
bash: groups: command not found
Then, if I try
apt-get remove --purge grub-pc grub-common
there is an error:
bash: apt-get: command not found

How should I proceed?

Kevin

---

### Post by kjaspan on 2012-06-14
In the BIOS there is an option 
Run UEFI Application..
and in the System Setup section, under Boot Order, there were a bunch of devices under UEFI Boot Sources and some more under Legacy Boot Sources. I disabled the UEFI bunch, and will try the installation again.

---

### Post by darkod on 2012-06-14
> **kjaspan said:**
> In the BIOS there is an option 
Run UEFI Application..
and in the System Setup section, under Boot Order, there were a bunch of devices under UEFI Boot Sources and some more under Legacy Boot Sources. I disabled the UEFI bunch, and will try the installation again.

That should do it. Let us know.

---

### Post by kjaspan on 2012-06-14
No, alas, it just booted into Windoze again.

Here is the output of BootInfo:
[http://paste.ubuntu.com/1041352/](http://paste.ubuntu.com/1041352/)

I await responses with bated breath.

It seems to me, unskilled though I am in this regard, that there is a fork in the road where we encounter UEFI, supported both by Intel and AMD but does Grub support it???

Will Boot Repair or EasyBSD fix this???

---

### Post by YannBuntu on 2012-06-14
> **kjaspan said:**
> Here is the output of BootInfo:
[http://paste.ubuntu.com/1041352/](http://paste.ubuntu.com/1041352/)

IMHO it was a bad idea to separate /usr, /tmp, /opt, /srv, /var, /usr/local but not /boot, it's useless and only complicates your problem.
If i were you, i would:
1) create a 1Go separate /boot, at the start of the disk (inside the first 137GB of the disk).
2) reinstall Ubuntu with this separate /boot, and without separate /usr, /tmp, /opt, /srv, /var, /usr/local  (/home can be ok).

Remarks: 
- your BIOS is setup in EFI mode, but as Windows is not installed in EFI, and the disk is not GPT, I would first try to install without EFI (and without BIOS-boot partition), but with the separate /boot as described above.
- today [Boot-Repair doesn't recognize separate /usr]("https://bugs.launchpad.net/boot-repair/+bug/1008469"), but I plan to fix it this week ;)

---

### Post by kjaspan on 2012-06-14
Merci, Yann(ick?), your English is excellent. 

I created /boot in /dev/sda3 and specified the boot loader to be placed there. I hope that's what you meant. Otherwise I just created a swap area, / and /home and am installing now. I hope to have an answer before you switch out the lights.

A bientot,

Kevin

---

### Post by YannBuntu on 2012-06-14
Salut
> **kjaspan said:**
> I created /boot in /dev/sda3

You can try like this, but it may fail because sda2 ends at 200GB of the disk, and the [BIOS limit is generally 137GB]("http://ubuntuforums.org/showthread.php?t=1998257").
If it fails, you will need to place your /boot partition just before or just after your current sda1.

---

### Post by kjaspan on 2012-06-14
Yann,
You were right, alors, it failed. I will try your latest suggestion though I cannot see how to put /boot at the beginning or end of /dev/sda1. But I did specify the boot loader to go in /dev/sda. We shall see, but I don't have a high level of confidence.

Kevin

---

### Post by kjaspan on 2012-06-14
That failed, too. Here is the output of Bootinfo:
[http://paste.ubuntu.com/1041660/](http://paste.ubuntu.com/1041660/)
I am going to take a chance and run Boot Repair now. What the heck, it's been 3 days and counting with this problem! As you can see grub is in /dev/sda6, which doesn't help.

Boot repair says the boot of my PC is in EFI mode but no EFI partition was detected. I may want to retry after creating an EFI partition (FAT32, > 200M, start of disk, boot flag). Perhaps I should put /boot there?

---

### Post by kjaspan on 2012-06-14
Boot Repair ran to completion. Here is the Bootinfo output afterwards:
[http://paste.ubuntu.com/1041672/](http://paste.ubuntu.com/1041672/)

I will report on success/failure after reboot. Holding thumbs!!

---

### Post by kjaspan on 2012-06-14
That resulted in a grub menu giving me the choice of a Windows 7 loader on /dev/sda1 and /dev/sda2. The first booted windows, the second gave me a menu that looked like one from EasyBCD with Windows 7 or Xubuntu 12.04 but, if I chose the second, it just returned me to the first menu. I think I know why: when Boot Repair asked me where to put grub out of 2 choices I chose /dev/sda1 or sda2. The other choice was /dev/sda7. I will try that now.

I reran Boot Repair and it did not ask me to choose where to put grub, but produced this report: [http://paste.ubuntu.com/1041690/](http://paste.ubuntu.com/1041690/)

I am now at an impasse and await further suggestions. Perhaps run Boot Repair in advanced mode or create and EFI file system to put /boot on??

---

### Post by YannBuntu on 2012-06-15
Hello

You now have a GRUB menu with access to all your systems, so Boot-Repair has done its job, it can't do better. 
If you want to customize GRUB (hide an entry, or change the default entry...), you can use [GRUB-Customizer]("https://launchpad.net/grub-customizer").

---

### Post by kjaspan on 2012-06-15
Yann,

Merci.But I still cannot access my Xubuntu installation. I am seriously thinking of just overwriting Windows and having a machine with just Ubuntu, but I occasionally (1-5% of the time) need Windows.

---

### Post by darkod on 2012-06-15
You said it yourself in post #30. The EFI boot is detected, and it all revolves around that.

Windows is installed in standard mode, not EFI, but since EFI is still detected my guess is ubuntu doesn't want to install in standard mode, but it can't install in EFI mode neither because you are not actually running a full EFI mode with the EFI system partition.

Don't waste time on reinstalls or boot-repair, if it could help, it would have helped the first time you used it. Instead, look around very carefully in the BIOS and try to find an option to disable EFI mode. Not just to disable various EFI devices for boot, see if you can disable the whole EFI mode completely. If my logic is correct, in that case it will not even be detected, like it doesn't exist.

Same like if you disable your onboard graphics. From that moment on, it doesn't exist.

When EFI is completely out of the picture, I guess xubuntu will have no problem installing in the standard mode.

---

### Post by kjaspan on 2012-06-15
Yann, 

Grub Customizer did the trick!! I put the linux..-generic and --recovery in the MBR and got the usual menu on bootup, then was able to get into Xubuntu.

Thanks very much (merci, gracias) for all your help. I will mark this as solved.

---

### Post by YannBuntu on 2012-06-15
Glad it worked! :)

(in my last post i hadn't seen that there was no Ubuntu entry in the menu, sorry. I still don't understand why. Please indicate your current [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1"), it may help us understand how this was solved.)

---

### Post by kjaspan on 2012-06-15
Here is the Boot info report.
 [http://paste.ubuntu.com/1042711/](http://paste.ubuntu.com/1042711/)

Darko, I searched around the BIOS Computer Setup menu for something to turn on/off UEFI and haven't found it (yet).

I am going to mark this issue solved. Thanks again, all of you, for all your help. I wonder why I'm the only one who encountered/reported this problem.

---

### Post by martinr on 2012-06-16
> **kjaspan said:**
> Here is the Boot info report.
 [http://paste.ubuntu.com/1042711/](http://paste.ubuntu.com/1042711/)

Darko, I searched around the BIOS Computer Setup menu for something to turn on/off UEFI and haven't found it (yet).

I am going to mark this issue solved. Thanks again, all of you, for all your help. I wonder why I'm the only one who encountered/reported this problem.

Hi Kjaspan,

You're not the only one with this problem.
Have a look at this [solution]("http://ubuntuforums.org/showthread.php?p=12030957#post12030957").

Might you have a boot device selector during POST without UEFI?

Good luck in tuning Ubuntu to your likes (shuffling the window buttons around, etc.).

---

### Post by YannBuntu on 2012-06-16
> **kjaspan said:**
> Here is the Boot info report.
 [http://paste.ubuntu.com/1042711/](http://paste.ubuntu.com/1042711/)

Thanks.
(for information, your BIOS is not in EFI mode any more. That may be what was blocking)

---

