---
title: "Boot loader with btrfs"
date: 2014-04-03
forum: Installation &amp; Upgrades
---

### Post by spacerocket on 2014-04-03
Hello!

I installed ubuntu 13.10 using this as guide: [http://www.linuxbsdos.com/2014/02/01/dual-boot-windows-8-or-windows-7-and-ubuntu-13-10-with-ubuntu-on-a-btrfs-filesystem/](http://www.linuxbsdos.com/2014/02/01/dual-boot-windows-8-or-windows-7-and-ubuntu-13-10-with-ubuntu-on-a-btrfs-filesystem/)

Created swap area and Ext4 journalizing filesystem(which I added as a device for boot loader installation(dev/sda6), mount point /boot) all these from free space. I also created btrfs journaling file system (44,83 Gt visible in my picture) for ubuntu from free space. Then I installed ubuntu and restarted my comp, went to windows 7. There I added the ubuntu 13.10 entry as my picture shows. Now when I click edit boot menu I have windows 7 (default) and ubuntu 13.10. When I restart my computer I get a boot loader where is windows 7 and Opensuse 13.1(my old linux system). The Opensuse 13.1 does not even work anymore(deleted) windows7 works but where is ubuntu 10.3?? Not in the boot loader. Strange?

---

### Post by oldfred on 2014-04-03
I do not know EasyBCD.
You may do better here if you want EasyBCD.
 [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

If you want to use grub2, not grub legacy as shown in EasyBCD screen?

      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
With UEFI If you run any fixes from Boot-Repair do not say yes to 'buggy' UEFI fix. That is only for systems where UEFI has been modified by vendor to only allow Windows to boot.

---

### Post by spacerocket on 2014-04-03
Hi!

Thx. I already tried GRUB2 though that didn`t work either. I downloaded boot repair disc from here:[http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)

Then write image file to disc(CD) with imgburn and start computer with CD in dvd-drive?

---

### Post by oldfred on 2014-04-03
You can create it as a Repair CD or flash drive just like any other Linux repair tools.

Or you can just boot your Ubuntu installer DVD or Flash drive and install to that. (You then have to reinstall with every reboot). With persistence I think you can save download though.

---

### Post by spacerocket on 2014-04-03
Ok. Now I burned the repair file to my CD and started my computer. Then I chose Recommended repair(repairs most frequent problems).

Then it did something and said:

sda1 ...
sda2 ... (some windows issue)
....

sda6: Filesystem: ext4
        Boot sector type: -
        Operating system:
        Boot files: /grub/grub.cfg

sda7: Filesystem: btrfs
        Boot sector type:-
        Operating system:
        Boot files:
... 

Boot successfully repaired.   -> Then I restarted my comp and I`m still having the same issue, there is no boot loader for ubuntu 13.10, only for windows. Maybe I did something wrong?

---

### Post by oldfred on 2014-04-03
Post link to BootInfo report that Boot-Repair creates.

---

### Post by spacerocket on 2014-04-04
Hi

Now this link [http://paste.ubuntu.com/7203086/](http://paste.ubuntu.com/7203086/) it didn`t fix my boot issue, what`s going on?

Thx

---

### Post by oldfred on 2014-04-04
I do not know enough about btrfs to know issue.
But Boot-Repair and script does not see fstab in sda7, which would be same issue that grub would have.

Are you missing drivers for btrfs? Did they not get installed? 
Grub also has extra drivers that you have to load for non-standard file systems.
I do know you cannot use tools like e2fsck as that is for the ext family and must have separate tools for btrfs systems.

 BTRFS, not ready for prime time
[http://ubuntuforums.org/showthread.php?t=2111487](http://ubuntuforums.org/showthread.php?t=2111487)

 Linux 3.11 File-System Performance: EXT4, Btrfs, XFS, F2FS
[http://www.phoronix.com/scan.php?page=article&item=linux_311_filesystems&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_311_filesystems&num=1)
EXT4 Still Leads Over Btrfs File-System On Linux 3.8
[http://www.phoronix.com/scan.php?page=article&item=linux_38btrfs_ext4&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_38btrfs_ext4&num=1)
[http://www.phoronix.com/scan.php?page=news_item&px=MTM1MTE](http://www.phoronix.com/scan.php?page=news_item&px=MTM1MTE)

---

### Post by spacerocket on 2014-04-04
Hi

I can`t read all those links. It can`t be this complicated. Now you are saying that I should use ext4 in sda7 instead of btrfs? This too seems too tricky. Why is there not visible** install ubuntu alongside with windows**, only **erase disc **or [B]something else.
[/B]
Here is installation type: **install ubuntu alongside with windows**. [https://sites.google.com/site/easylinuxtipsproject/installation](https://sites.google.com/site/easylinuxtipsproject/installation)     Why there is no this option when I try to install ubuntu?

---

### Post by spacerocket on 2014-04-04
maybe this is the solution: [https://sites.google.com/site/easylinuxtipsproject/reserve-10](https://sites.google.com/site/easylinuxtipsproject/reserve-10)

---

### Post by spacerocket on 2014-04-04
I installed ubuntu 13.10 with these settings but there is once again no ubuntu 13.10 on the bootloader, only windows 7! That`s very strange.

---

### Post by spacerocket on 2014-04-04
Creating a partition for /boot won`t change much I guess, I already tried that without success. The boot throws me always at windows loader whatever I do don`t know why.

---

### Post by oldfred on 2014-04-04
Did you use btrfs?

I am changing your title to include btrfs, as only a few have experimented with it and they may then see this thread and can help.

---

### Post by spacerocket on 2014-04-04
No I didn`t I followed very carefully the instructions from here: [https://sites.google.com/site/easylinuxtipsproject/reserve-10](https://sites.google.com/site/easylinuxtipsproject/reserve-10)

---

### Post by oldfred on 2014-04-04
Then post a new link to BootInfo report.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by spacerocket on 2014-04-04
Ok... so I should copy the new http:// paste .... link created and send to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]?

---

### Post by oldfred on 2014-04-04
No, have not seen Yann around for ages.
Just post link.

---

### Post by spacerocket on 2014-04-04
Ok now I went again to recommended repair. Now the system told to write some commands to "lubuntu terminal window" and after writing them the terminal window told "no such command". Then it asked Remove GRUB2 from /boot/grub? It couldn`t go forward, I don`t know what happened.

---

### Post by grahammechanical on 2014-04-04
> [COLOR=#000000]1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown [/COLOR][COLOR=#AA22FF]type [/COLOR][COLOR=#000000]OS. [/COLOR]

Now, I find that comment in the Boot Repair report very interesting. It means that Ubuntu is not installed. The Grub configuration files are in sda6 
> [COLOR=#000000]Boot files:        /grub/grub.cfg [/COLOR]

And Grub config is telling Grub to look here
> [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd0,msdos6' [/COLOR]

That is the first hard disk and the 6th partition = sda6 but is Ubuntu on sda6?

Grub uses a tool called os-prober to find the location of any OS including Linux kernels but when Boot Repair ran os-prober it got his back
> [COLOR=#000000]os-prober[/COLOR]/dev/sda1:Windows 7 [COLOR=#666666]([/COLOR]loader[COLOR=#666666])[/COLOR]:Windows:chain[COLOR=#222222][FONT=Verdana]

And that is all. When I run os-prober on my machine by running sudo update-grub I see this.

[/FONT][/COLOR]> Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-21-generic
Found initrd image: /boot/initrd.img-3.13.0-21-generic
Found linux image: /boot/vmlinuz-3.13.0-20-generic
[FONT=Verdana]Found memtest86+ image: /boot/memtest86+.bin[/FONT]
Found Windows 8 (loader) on /dev/sda1


[COLOR=#222222][FONT=Verdana]Boot Repair should be showing the Linux kernel and memtest in the OS-prober report if they were installed.

Regards.

[/FONT][/COLOR]

---

### Post by spacerocket on 2014-04-05
Ok now  I deleted all possible linux kernels and have Windows C 45,29Gt and Unallocated space 66,50Gt.

1) Maybe I could re-install windows and see if that fixes anything

2) Or you could tell me what partitions I should create when choosing **something else** from select installation type. **Note: **I have not the option of going for Install ubuntu alongside with windows.

Thanks for your time.

---

### Post by oldfred on 2014-04-05
You may have other hidden data on drive. 
Was system or drive every RAID, did you use gpt partitioning, did you create partitions with Windows and it converted to dynamic (not basic) partitioning. 
 Most of reasons for installer not showing Windows, any partition type error
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

For manual partitioning you need the /(root) and swap. 
I suggest / of 20 or 25GB, swap about 2GB, and if  dual booting include a NTFS shared data partition. But you cannot create NTFS partition during install, so either partition in advance or leave space during install and use gparted. The remaining space would either be /home or /mnt/data partition formatted ext4. If less than 25GB just include that in / (root).

---

