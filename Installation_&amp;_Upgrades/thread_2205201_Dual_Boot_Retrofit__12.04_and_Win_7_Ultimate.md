---
title: "Dual Boot Retrofit / 12.04 and Win 7 Ultimate"
date: 2014-02-12
forum: Installation &amp; Upgrades
---

### Post by pcar916 on 2014-02-12
Goals: 
1. To add an existing (new) Win7 Ultimate drive (1TB) to an existing Ubuntu 12.04/WinXP dual-boot system.
2. Then copy data from the XP file system to the Win7 file system.

Current configuration
1. 12.04LTS and XP on SATA 1 and SATA 2 drives
2. GRUB works to take me to either partition.
3. XP won't boot any more but I don't need it anyway, and that file system is accessible from Linux.
4. I installed Win7/Ultimate on SATA 3 with the other two drives disconnected.
______________________________________________________________________________________________
Problem: If I connect all drives the computer will only boot to Win7 and not grub.

Question: 
Is there a way to make GRUB work again and give me the choice to boot either 12.04 or Win7 without reformatting
anything? Is this a simple partition manager configuration?

If not then what's my proceedure from here?

Thanks in advance,
Ron

---

### Post by oldfred on 2014-02-12
Have you chosen the Ubuntu (or maybe XP) drive as boot drive in BIOS? It may depend on where grub2's boot loader was installed. Best to have it in MBR of Ubuntu drive. And keep Windows boot loader on Windows drive(s).

Do not run auto repair as that installs grub to every drive's MBR. You can use Advanced & choose which system and which MBR to install boot loader.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by pcar916 on 2014-02-12
The boot loaders are on separate drives. I did that on purpose thinking it would be simpler for potential boot emergencies down the road. I'll do the reading and check out the BIOS options and links as well, then report back.

Thanks,
Ron

---

### Post by pcar916 on 2014-02-13
Sorry for the delay. Between the mysteries of USB booting with this new motherboard, and the lack of wireless networking on both LiveCD and LiveUSB, I'm finally able to report that the boot-repair report is located at [http://paste.ubuntu.com/6927086](http://paste.ubuntu.com/6927086).

The current BIOS configuration has me booting to GRUB and Ubuntu. I can change that at any time to boot from the Win7 drive, and I can see it in my GUI Devices list.

I'm learning linux command line, but am eager to use it as much as possible to fix things and learn my way around Ubuntu.

Thanks

---

### Post by oldfred on 2014-02-13
So is it working to boot Ubuntu and from grub menu can you boot Windows or only from BIOS?

Not sure why Boot-Repair thought partitions were mounted, it then did not give as much data. But otherwise looks normal.

Does BIOS show all 3 drives correctly?

---

### Post by pcar916 on 2014-02-13
Correct, 
1. Ubuntu boots perfectly from the grub menu
2. Win7 only boots from the BIOS when that drive is rotated into the top position in the "boot priority"
3. All three drives are visible in BIOS, but only the WIN7 and Ubuntu drives show as bootable devices (AMI BIOS). The XP drive won't rotate up into the top position in the "boot priority"
Note: 
That makes sense as the grub menu shows the XP partition, but it won't boot... it starts but reboots the computer, so there be something wrong with the MBR on that partition.
I'm moving all data from the XP drive onto the Win7 drive. Then I'll give that space to Ubuntu with gparted, since it's on a small drive right now.

4. The Win7 partition manager sees all drives and partitions and reports them as healthy.

At least it's consistent.

---

### Post by oldfred on 2014-02-13
Because of the already mounted errors, I cannot tell if Windows has all the boot files needed. Usually grub will not offer to boot Windows unless it can mount partition and the initial boot files are there. But grub can then only boot working Windows as it really just passes boot process to Windows. 

Sometimes BIOS, grub & Windows do not work well together. Some systems just have to have grub in MBR of first drive. Grub is supposed to remap BIOS drive entries when chain loading Windows as it has to see itself as first boot drive. Sometimes only work around has been to install grub into Windows drive.

---

### Post by pcar916 on 2014-02-13
Ok, then is it possible to "reinitialize" grub, or delete and recreate it with the XP drive disconnected? 

1. Somehow make grub aware of the win7 boot files with additional lines to grub itself... or "some other way" like a utility... or
2. As you stated, install grub onto the Win7 drive. What would be the process to move grub? If that happens then...

3. when grub is moved, what are the implications to the boot process and/or Ubuntu updates vs Windows updates?

I wonder if, by disconnecting the XP drive temporarily, grub can reinitialize itself to see Win7. Of course that's a rhetorical question... easy to test, and I will. I'll report if it magically makes the situation better. I'm bothered by magic, but can accept it if nothing else works.

---

### Post by frank18 on 2014-02-13
> **pcar916 said:**
> Correct, 
1. Ubuntu boots perfectly from the grub menu
2. Win7 only boots from the BIOS when that drive is rotated into the top position in the "boot priority"
3. All three drives are visible in BIOS, but only the WIN7 and Ubuntu drives show as bootable devices (AMI BIOS). The XP drive won't rotate up into the top position in the "boot priority"
Note: 
That makes sense as the grub menu shows the XP partition, but it won't boot... it starts but reboots the computer, so there be something wrong with the MBR on that partition.
I'm moving all data from the XP drive onto the Win7 drive. Then I'll give that space to Ubuntu with gparted, since it's on a small drive right now.

4. The Win7 partition manager sees all drives and partitions and reports them as healthy.

At least it's consistent.

Why not make it easier! install win7 the Virtual-box then install Linux inside win 7,it's so easy most people do it this way, you can install Virtual-box for free for win7 then just follow instruction, there are tones of instructions on the web and on U Tube.

---

### Post by pcar916 on 2014-02-13
> **frank18 said:**
> Why not make it easier! install win7 the Virtual-box then install Linux inside win 7,it's so easy most people do it this way, you can install Virtual-box for free for win7 then just follow instruction, there are tones of instructions on the web and on U Tube.

Interesting, thanks. But I don't know about implications to backup/restore procedures, and I like the separation of OS' into separate drives with no real dependancies except the boot procedure. If one fails I don't have to do much reconfiguration (to this computer) to use the other while I restore the one that's messed up. I have used Wine inside Linux just to see what it's like, but it's a complication unless I have to do it for some reason.

I think of nesting them as good for testing, but it's a little like both a brake and clutch systems sharing a master cylinder. What you do to one usually effects the other. Viable idea though.

Thanks

---

### Post by oldfred on 2014-02-13
You can install grub to sdb, the Windows drive. Just boot into Ubuntu and install grub2's boot loader to sda.
 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

Often Windows seems to work more consistently if sda or first drive in BIOS.
Are all drives SATA or is sdc an older PATA drive? That can also be an issue.

---

### Post by pcar916 on 2014-02-13
> **oldfred said:**
> You can install grub to sdb, the Windows drive. Just boot into Ubuntu and install grub2's boot loader to sda.
 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

Often Windows seems to work more consistently if sda or first drive in BIOS.
Are all drives SATA or is sdc an older PATA drive? That can also be an issue.

All drives are SATA2.

Success!
I executed the commands you suggested. But since I didn't FOLLOW YOUR DIRECTIONS and directed it to install grub on sdc1 and sdc2 (my Win drive partitions) rather than simply sdc, of course it wouldn't work and warned me that that was a very bad idea. But it turns out that failure was not only deserved, but didn't have any impact.

When I saw your last command line, I realized that I hadn't issued the update-grub command after the new drive was installed. During that update it found the bootable Win7 drive and listed it.

Now both Ubuntu and Win7 boot properly. So I'll copy over all appropriate data to Win 7 and format that old XP drive for Ubuntu to use. Now I get to study how much swap-space to create for Ubuntu to use on that ~250gb drive. Too many years have passed since I did that the last time.

Thanks to the both of you for your help.
~Ron

---

### Post by oldfred on 2014-02-14
You almost never install grub to a partition and never to a NTFS partition. NTFS have to have its own size & boot info in the partition boot sector.

Swap depends on RAM size. And if over 4GB of RAM you may not need much swap. If hibernating which is not really recommended if dual booting, you need swap equal to RAM in GiB (not GB) so if RAM is full you have space to copy all of it into swap. 

       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

---

### Post by pcar916 on 2014-02-14
I have 8GB of RAM and I've never use hibernate, so the swap area's looking to be small. The last time I set one up from scratch I didn't have a lot of RAM so it was important.

I'm glad Ubuntu was smarter than I was when trying to move grub... need to sharpen my attention to detail a bit when reading instructions. Now, to RTFM on UEFI.

I've been working the heck out of the grub menu back and forth between boot options and it seems to be rock solid. 

Thanks again for the quick response.

---

