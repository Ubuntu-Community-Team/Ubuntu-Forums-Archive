---
title: "GRUB Error - No Such Device etc."
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by porkchop_001 on 2010-12-05
Hi Guys,

I had a solid dual-booting machine of Windows 7 and Ubuntu 10.10 on my ASUS Eee PC netbook but I've hit an issue...

I installed Burg and when I re-booted I get the GRUB error message:

[B][I]error:no such device: 74ef5b4a-1215-4460-b67d-9994f72fa678
Entering rescue mode....
grub rescue>[/I][/B]

Most of the solutions lying around involve inserting the live CD etc. but I'm, obviously, unable to do that as I'm on a netbook without a CD drive. Any solution guys? Thanks in advance!

---

### Post by sikander3786 on 2010-12-05
You can try booting from Grub Rescue > prompt as explained here by **drs305**.

[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

Or if not successful, you'll need to boot from an Ubuntu Live USB (as you don't have a CD drive).

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

Then run and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

And wrap your output with code tags # from post menu. [/code] at the end and [code] at the beginning.

---

### Post by porkchop_001 on 2010-12-05
Cool thanks sikander - I'll get on it right away and let you know!

---

### Post by porkchop_001 on 2010-12-06
Okay so sadly it isn't working. I've tried using both unetbootin and the in-build Ubuntu Startup Disk creator and both haven't worked. I've put the USB drive into a working computer and it acts as a USB OS and all, but when it's plugged into my netbook it simply doesn't work. I've configured the BIOS settings to ensure that the Removable Drive is loaded first...but still no deal.

Any further ideas? I've even tried to simply restore my netbook to factory default (done by tapping F9 on my ASUS Eee PC 1005HA) and even that doesn't work.

---

### Post by sikander3786 on 2010-12-06
What happens when you boot the same USB on your netbook? Black screen? Any errors? How far does it get?

---

### Post by wilee-nilee on 2010-12-06
Here is a condensed manual boot from a grub prompt.

Manual boot from grub prompt for grub2

set root=(hd0,X)    X=the partition # of OS 
linux /boot/vmlinuz(tab=kernel) root=/dev/sdaX 
initrd /boot/initrd(tab, then enter) 
boot (enter)

---

### Post by niteshreddy on 2010-12-06
Is your installation a wubi install? 

if it is... then the first few lines in this post

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

should solve your porblem

---

### Post by porkchop_001 on 2010-12-06
> **wilee-nilee said:**
> Here is a condensed manual boot from a grub prompt.

Manual boot from grub prompt for grub2

set root=(hd0,X)    X=the partition # of OS 
linux /boot/vmlinuz(tab=kernel) root=/dev/sdaX 
initrd /boot/initrd(tab, then enter) 
boot (enter)

Tried this and it didn't work - is the code correct? The first line was fine but it came up with 'Unknown command 'linux''. Ideas?

> **niteshreddy said:**
> Is your installation a wubi install? 

if it is... then the first few lines in this post

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

should solve your porblem

It sounds like it'd work but I can't *get* into Windows...so that method seems useless at the moment sadly.

*sigh* I should start reading release notes with more care hey!

---

### Post by sikander3786 on 2010-12-06
> **porkchop_001 said:**
> Okay so sadly it isn't working. I've tried using both unetbootin and the in-build Ubuntu Startup Disk creator and both haven't worked. I've put the USB drive into a working computer and it acts as a USB OS and all, but when it's plugged into my netbook it simply doesn't work. I've configured the BIOS settings to ensure that the Removable Drive is loaded first...but still no deal.

Any further ideas? I've even tried to simply restore my netbook to factory default (done by tapping F9 on my ASUS Eee PC 1005HA) and even that doesn't work.
Why don't you concentrate on trying to boot an Ubuntu Live USB? The problems might be curable once you let us know about them.

---

### Post by bcbc on 2010-12-06
It sounds like it is a wubi install. See problem #1 here: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Wubi needs the windows bootloader (or equivalent) in the MBR. Burg overwrites this.

Note, many OEM computers have custom bootloaders in the MBR that are similar to the Windows bootloader but also do other things. Like that F9 key for instance, it's possible it isn't a bios option, but rather the bootloader checks whether it's in the keyboard buffer after the BIOS passes control to it (my dell works that way). Since you now have grub2 or burg installed in the MBR that function won't work anymore unless you can download and restore the original bootloader (see your manufacturer if you need to fix that).

But in terms of getting windows and ubuntu booting again, Rubi1200's guide has all the info you need - and you'll need either an Ubuntu USB or a Windows repair USB to do that. PS it's just the bootloader that needs replacing (not the windows bootsector or anything else).

Of course, assuming this is Wubi - but it sounds like it.

---

### Post by ch3rryc0ke on 2010-12-06
I believe I have the same problem-- wubi install gone wrong on an Asus 1215N. I believe it installed grub, and now the native Asus bootloader won't work.

I contacted Asus to see if there is a way to reinstall the native bootloader, and am also independently trying to boot from Ubuntu USB.

---

### Post by ch3rryc0ke on 2010-12-06
**Update:** To solve my specific issue, I used another windows PC to create a USB Windows repair disk.

From there I followed the instructions on this thread: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

After doing the repair to the bootloader-- the laptop booted directly into the Asus recovery mode.

From there I clicked recover-- and now it's installing the stock image of Win7 again. Hopefully this should recover the Asus custom boot loader to retain the F9 recovery option in the future.

**My next question is**: what is the correct way to go about installing Ubuntu now? It sounds like using Wubi isn't the best way to go.

---

### Post by bcbc on 2010-12-06
> **ch3rryc0ke said:**
> **Update:** To solve my specific issue, I used another windows PC to create a USB Windows repair disk.

From there I followed the instructions on this thread: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

After doing the repair to the bootloader-- the laptop booted directly into the Asus recovery mode.

From there I clicked recover-- and now it's installing the stock image of Win7 again. Hopefully this should recover the Asus custom boot loader to retain the F9 recovery option in the future.

**My next question is**: what is the correct way to go about installing Ubuntu now? It sounds like using Wubi isn't the best way to go.

For most people, doing a system recovery/restore is not an option as it removes all changes you've made since buying the computer.

Generally, installing Ubuntu to partition is recommended over using Wubi, but note this will also remove the custom bootloader you have. I'm not sure that having the custom bootloader is all that important in any case, unless you need to use the system restore feature or have it available just in case. In my Dell, changing the default partitions also prevents the system restore from working, even if the special bootloader is present.

PS some people use easyBCD to boot a direct install of Ubuntu, while keeping the Windows bootloader. And also, for future reference you can just backup the MBR using "dd".

---

### Post by ch3rryc0ke on 2010-12-06
> **bcbc said:**
> For most people, doing a system recovery/restore is not an option as it removes all changes you've made since buying the computer.

Generally, installing Ubuntu to partition is recommended over using Wubi, but note this will also remove the custom bootloader you have. I'm not sure that having the custom bootloader is all that important in any case, unless you need to use the system restore feature or have it available just in case. In my Dell, changing the default partitions also prevents the system restore from working, even if the special bootloader is present.

PS some people use easyBCD to boot a direct install of Ubuntu, while keeping the Windows bootloader. And also, for future reference you can just backup the MBR using "dd".

Thanks! I was able to use system restore since this is a new machine, so no files to worry about. I guess I can live without having the Asus system recovery. I will create a recovery disk as backup just in case though.

My goal is to be able to dual-boot Win7/Ubuntu 10.10 on this laptop. I'm using it to work on a dev project, but this is my first attempt with Linux development, so I want to keep Windows around for a few things.

So now the machine has Win7 installed with the following partitions on 1 physical drive: 
[LIST]
[*]C: System Drive with Win7 installed (80gb free)
[*]D: 117GB free, totally empty
[*]20 MB EFI System Partition, not mounted
[*]15 GB Primary Partition, not mounted
[/LIST]

I'm reading the dual booting guide here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

It sounds like my best option is to use the Live CD to install Ubuntu on the D:\ partition mentioned above. 

Will that work cleanly? I understand that I will need to add a GRUB entry after the install to be able to boot into Win7 from the new bootloader installed by Ubuntu.

---

### Post by ch3rryc0ke on 2010-12-06
Also, for a newbie, is there a benefit to installing 10.04 versus 10.10? I was planning on 10.10.

---

### Post by sikander3786 on 2010-12-06
10.04 is the Long Term Support release, will be supported for 3 years on the desktop. 10.10 is the normal but newer release and supported for 18 months on the desktop. Choice is yours ;-) Both are stable. For productivity, 10.04 would be better.

Regarding partitioning, I would suggest to create an Extended partition in your Free space and then assign these three partitions for Ubuntu.

1. / Ubuntu partition, ext4, size > 10 GB, mount point '/'

2. /home partition, ext4, size=custom, mount point /home

3. Swap partition, size=RAM x 2.

The remaining space from that 117GB can be formatted NTFS and used as a data sharing partition between Ubuntu and Windows.

Ubuntu can be installed with just 2 partitions as well. A '/' and a swap partition but having a separate /home partition always saves you some hard work when you need to re-install Ubuntu. It saves all your settings/configuration and also your personal files so you just need to define /home during a new installation and chose not format it.

---

### Post by ch3rryc0ke on 2010-12-07
> **sikander3786 said:**
> 10.04 is the Long Term Support release, will be supported for 3 years on the desktop. 10.10 is the normal but newer release and supported for 18 months on the desktop. Choice is yours ;-) Both are stable. For productivity, 10.04 would be better.

Regarding partitioning, I would suggest to create an Extended partition in your Free space and then assign these three partitions for Ubuntu.

1. / Ubuntu partition, ext4, size > 10 GB, mount point '/'

2. /home partition, ext4, size=custom, mount point /home

3. Swap partition, size=RAM x 2.

The remaining space from that 117GB can be formatted NTFS and used as a data sharing partition between Ubuntu and Windows.

Ubuntu can be installed with just 2 partitions as well. A '/' and a swap partition but having a separate /home partition always saves you some hard work when you need to re-install Ubuntu. It saves all your settings/configuration and also your personal files so you just need to define /home during a new installation and chose not format it.

Thanks for the additional info. Should I create these partitions during the Ubuntu install process, or before I install (e.g. using a Live USB or something)..

For now, in Win 7, I've shrunk the side of the D:/ drive and left 70GB of unallocated space for Ubuntu installation and the partitions you mentioned above.

---

### Post by ch3rryc0ke on 2010-12-07
I tried loading GParted from the Live USB of Ubuntu 10.10, but it always crashes when opening.

The instructions in this article made it sound like creating the partitions before install was the way to go.

Now I'm going to try doing the partitions through the installation.

[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

---

### Post by sikander3786 on 2010-12-07
You can do that from the installer's partitioning step.

---

### Post by ch3rryc0ke on 2010-12-07
> **sikander3786 said:**
> You can do that from the installer's partitioning step.

So that 70GB that is "unallocated space" in Windows shows up as "unusable" space in the Ubuntu installer. I'm unable to add partitions to it.

Any suggestions?

---

### Post by ch3rryc0ke on 2010-12-07
Looks like I am running into the limitation that I can only have 4 primary partitions on one logical disk. Is this a limitation to Windows only?

I guess I'm going to have to delete the Asus recovery partition to get at least 2 partitions for Ubuntu.

---

### Post by sikander3786 on 2010-12-07
> **ch3rryc0ke said:**
> Looks like I am running into the limitation that I can only have 4 primary partitions on one logical disk. Is this a limitation to Windows only?

I guess I'm going to have to delete the Asus recovery partition to get at least 2 partitions for Ubuntu.
Before doing that, I would recommend to go Applications > Accessories > Terminal and post the output of this command.

```
sudo fdisk -l
```

Yes you can't create more than 4 primary partitions.

---

### Post by ch3rryc0ke on 2010-12-07
Thanks a lot for the quick response! This is the output of running the command you mentioned. I had already deleted the 15gb system restore partition before reading your post.

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x29133921

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13055   104857600    7  HPFS/NTFS
/dev/sda2           30399       30402       20664   ef  EFI (FAT-12/16/32)

Disk /dev/sdb: 2021 MB, 2021654528 bytes
255 heads, 63 sectors/track, 245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         246     1974208    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(244, 254, 63) logical=(245, 200, 19)
ubuntu@ubuntu:~$ 
```

---

### Post by sikander3786 on 2010-12-07
If that recovery partition has been deleted already, create an Extended partition in the freed up space and Logical partitions in Extended one as mentioned in one of my previous post.

Did you create a disc backup of your recovery partition or you just don't need that anymore?

---

### Post by ch3rryc0ke on 2010-12-07
> **sikander3786 said:**
> If that recovery partition has been deleted already, create an Extended partition in the freed up space and Logical partitions in Extended one as mentioned in one of my previous post.

Did you create a disc backup of your recovery partition or you just don't need that anymore?

I created a backup recovery drive through the Asus tool, so that should cover me there. I have extra copies of Windows lying around as well if the recovery drive doesn't work (USB).

In Ubuntu I'm unable to use Gparted Partition editor, it keeps crashing. I will try to create the partitions as mentioned through Windows..

---

### Post by sikander3786 on 2010-12-07
No. Dont' use Windows tools for partitioning. Instead, you can partition from the installer's partitioning page.

---

### Post by ch3rryc0ke on 2010-12-07
> **sikander3786 said:**
> No. Dont' use Windows tools for partitioning. Instead, you can partition from the installer's partitioning page.

Is it OK to leave some unallocated space, e.g. free space? So basically in the Ubuntu installer I created:

[LIST]
[*]Mount: "/" size 15GB
[*]Mount /home size 40GB
[*]Mount /swap 5GB
[*]freespace 82GB
[/LIST]

This is in addition to the windows (sda1) drive of 107GB, left untouched by Ubuntu.

The freespace-- will I be able to mount that in Windows?

Thanks again in advance for your quick responses and helping me through this process! I really appreciate it.

---

### Post by sikander3786 on 2010-12-07
Swap seems a bit over-sized. 2 GB is enough in *most* cases.

Regarding unallocated space, create an NTFS partition there and then you'll be able to mount that partition in both Windows and Ubuntu.

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by prbhtthapa on 2011-01-17
when installing ubuntu if you have formatted the whole hard disk(including the third partition which contains the default factory setting) then i don't think that you have any way.but if you have not then it's ok.the f9 key is not working because it has no path to go.you can still boot with your factory setting.when you boot the computer may be there are options(4 or 5):
                       ubuntu.........
                       ubuntu(recovery mode)
                       ---------------------
                       _windows(nt/2000/xp)_
i hope you get it.choose the last one and boot.good luck.let me know.

---

