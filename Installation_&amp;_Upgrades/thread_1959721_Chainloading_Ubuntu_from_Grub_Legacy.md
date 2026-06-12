---
title: "Chainloading Ubuntu from Grub Legacy"
date: 2012-04-16
forum: Installation &amp; Upgrades
---

### Post by lostinspace2011 on 2012-04-16
I am trying to boot ubuntu as an alternative OS running from an external hard drive. My main boot loader on /dev/sda is grub legacy. I have Gentoo running on sda and sdb and Ubuntu on sdc. 

So I figured I can simply configure a chainloader on grub-lagacy to boot either into Gentoo or Ubuntu. Gentoo works well enough, however Ubuntu does not work via this method. A little bit of research brought me to this page :

[http://ubuntu-install.blogspot.com.au/2010/05/chainloading-grub-legacy-to-grub2.html](http://ubuntu-install.blogspot.com.au/2010/05/chainloading-grub-legacy-to-grub2.html)

which suggest to use the core.img file instead. However my ubuntu installation does not contain this file ?

Here is what I got in grub.conf

```

title Ubuntu 3.2.0-23
root (hd2,0)
kernel /vmlinuz-3.2.0-23-generic root=/dev/sdc2
initrd /initrd.img-3.2.0-23-generic

title Ubuntu Chainloader
root (hd2,0)
chainloader (hd2,0)+1

```The first option is working, but requires me to change the kernel everytime it is updated. The second option does not work.

Here is a file list of the files on my ubuntu boot partition.
```

-rw------- 1 root root  2884032 Mar 28 01:22 System.map-3.2.0-20-generic
-rw------- 1 root root  2884358 Apr 11 08:26 System.map-3.2.0-23-generic
-rw-r--r-- 1 root root   789425 Mar 28 01:22 abi-3.2.0-20-generic
-rw-r--r-- 1 root root   791023 Apr 11 08:26 abi-3.2.0-23-generic
-rw-r--r-- 1 root root   140211 Mar 28 01:22 config-3.2.0-20-generic
-rw-r--r-- 1 root root   140279 Apr 11 08:26 config-3.2.0-23-generic
drwxr-xr-x 3 root root     6144 Apr 11 23:52 grub
-rw-r--r-- 1 root root 14174668 Apr 11 23:23 initrd.img-3.2.0-20-generic
-rw-r--r-- 1 root root 14172749 Apr 14 12:02 initrd.img-3.2.0-23-generic
drwx------ 2 root root    12288 Apr 11 22:39 lost+found
-rw-r--r-- 1 root root   176764 Nov 27 18:00 memtest86+.bin
-rw-r--r-- 1 root root   178944 Nov 27 18:00 memtest86+_multiboot.bin
-rw-r--r-- 1 root root  4965584 Apr 12 06:17 vmlinuz-3.2.0-20-generic
-rw------- 1 root root  4965840 Apr 11 08:26 vmlinuz-3.2.0-23-generic

```

Any suggestions on what to try out to get this working better.

---

### Post by haresear on 2012-04-16
For Ubuntu 11.10 and earlier (not sure about 12.04) there should be links in the / directory pointing to the latest kernel files, i.e. /vmlinuz and /initrd.img, which can be used to boot instead of the specific kernel files. The links are updated automatically when the kernel is updated.

Actually I am a little puzzled why your specific kernel files appear to be in / rather than /boot subdirectory. I haven't looked at Ubuntu 12.04 yet -- maybe the boot files have been moved?

Edit: Never mind -- I see you apparently have a separate boot partion. This might affect the links I described above.

---

### Post by oldfred on 2012-04-16
Your chainload is to  the PBR. You would have to install grub2 to the partition which is not recommended. Grub2 is larger than grub legacy and converts to blocklists or hard coded addresses for grub files to continue to boot. If on a grub update files are relocated on drive, boot is broken and you have to reinstall grub.

The suggestion by haresear is probably the best if you do not want to update.

Grub legacy example:

title 1 Most Current Ubuntu on sda8
root (hd0,7)
kernel /vmlinuz root=/dev/sda8 ro quiet splash
initrd /initrd.img

---

### Post by perspectoff on 2012-04-16
Grub2 is always installed to the partition. That's where it lives. The Master Boot Record is only a small area on the hard drive with a bit of information that points to the location of the bootloader. You don't really "install Grub2 to the MBR."

The problem with the bit of deception about this is that should someone install Ubuntu with Grub2 and then erase the installation, Grub2 disappears as well. If the MBR has been set to refer to Grub2 (i.e. "installing Grub2 to the MBR") then the computer will not boot once the partition with Ubuntu in it has been erased. I think that this misinformation, perpetuated in many forums, is one of the biggest disservices to the average user that the Ubuntu installation process does.

Grub2 becomes more and more convoluted with time, and what works one month doesn't work the next month. It used to be trivial to chainload Grub2. Some months it is easy to do so, some months it isn't, depending on what new "feature" they have decided to throw into an update.

I now don't bother with Grub2 at all, and start my (K)Ubuntu partitions directly from Grub Legacy (in its boot partition) using the entry:

title Kubuntu Oneiric OS (chainloader)
rootnoverify (hd0,6)
kernel /vmlinuz root=/dev/sda7 ro
initrd /initrd.img

However, I used to chainload using the entry:

title (K)Ubuntu Oneiric OS (chainloader)
rootnoverify (hd0,6)
kernel /boot/grub/core.img

Grub2 is still in my (K)Ubuntu partition, and I still have to pay attention to it. I just don't use it as my primary bootloader.

---

### Post by Quackers on 2012-04-16
Not sure about some of the comments in the previous post. It seems to me to be contradictory and possibly designed to confuse. Some of it is definitely not correct. The rest is just an opinion.

Lostinspace2011, why don't you just configure your bios to boot from the external hard drive first when it is attached? That way, when it isn't attached your normal system will boot normally.
You could even update-grub on the external drive which will then give options to start your other systems.

---

### Post by oldfred on 2012-04-16
perspectoff is not wrong in that you do not install grub or grub2 to the MBR. I have tried to change to say install grub2's boot loader to the MBR, but it still is too easy just to say install grub as that is what the command is.

sudo grub-install /dev/sda

Grub in an install with a system has many parts.

 GRUB 2 - GRand Unified Bootloader has three main parts plus a boot loader installed to the MBR:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

But grub legacy also had many parts with its stage1.5 and/or stage2 code. Grub legacy has not been maintained for years, and each distribution adds a feature or two to get it to work with their system. Ubuntu updated grub 0.97 with 9.04 to work with ext4 partitions for example.

---

### Post by Quackers on 2012-04-16
Sadly the installer does not differentiate between grub and its bootloader. So, to say that grub is installed to a partition can be misunderstood. Grub (or most of it) is installed to a partition by default but in order for the system to boot grub's bootloader must be installed to the MBR of the bootable drive (ie /dev/sda, for instance) - unless chainloading from a different bootloader.

If a new Ubuntu user reads that grub is installed to a partition and tries to do that he/she will find that error messages are generated about it not being a good idea to do that. 
If that user persists he/she will find that the system will not boot because no bootloader was installed in the MBR of the drive.

This is not an ideal introduction to Ubuntu or grub.

In my opinion it is much simpler and less confusing to instruct people to install grub to the MBR of the bootable drive (ie /dev/sda, for instance) even though in fact most of grub will be installed to Ubuntu's root partition.

Bootloader code in the MBR of the drive is never removed when the operating system that installed it is removed, as far as I'm aware. If Ubuntu is installed, along with grub, and then Ubuntu is removed the bootloader code will stay in the MBR. This is useful for systems with more than one Linux system installed.

---

### Post by haresear on 2012-04-16
@Lostinspace2011
Since you have Ubuntu on a separate drive, it seems you could install the grub2 bootloader for Ubuntu to the MBR of that drive (i.e. /dev/sdc), then chainload to that grub2 from your grub legacy. I use that method myself with no problems, e.g. my grub legacy entry is:

#Grub2 on /dev/sdb
title		Grub2 on /dev/sdb
root		(hd1)
savedefault 6
chainloader +1

---

### Post by haresear on 2012-04-16
> **Quackers said:**
> 
Bootloader code in the MBR of the drive is never removed when the operating system that installed it is removed, as far as I'm aware. If Ubuntu is installed, along with grub, and then Ubuntu is removed the bootloader code will stay in the MBR. This is useful for systems with more than one Linux system installed.
But the problem is that if the operating system that installed the bootloader in the MBR is deleted, then the files needed to complete the boot process (e.g. grub.cfg) may no longer be accessible, and the boot process will hang. To avoid this, one has to remember to update the bootloader in the MBR to point to the necessary boot files in a partition that has not been deleted or reformatted.

---

### Post by Quackers on 2012-04-16
Or just not boot the entry for the missing system if you have more than one system and then re-install grub to the MBR from a booted OS to over-write the MBR.

---

### Post by haresear on 2012-04-16
> **Quackers said:**
> Or just not boot the entry for the missing system if you have more than one system and then re-install grub to the MBR from a booted OS to over-write the MBR.
That will work if the missing system is NOT the controlling OS (i.e. the OS which last installed grub to the MBR). If the deleted system IS the controlling OS, then grub needs to be re-installed from another existing OS BEFORE deleting the controlling OS, otherwise the grub boot menu (grub.cfg) will no longer exist.

---

### Post by Quackers on 2012-04-16
Yep, you're right there :-)

---

### Post by lostinspace2011 on 2012-04-16
Thanks for all your responses. I made some progress. When I installed ubunutu I selected sdc (hd2) for the installation of the MBR. However in my grub configuration I was referencing sdc1 instead.

So I changed my grub-legacy configuration to :
```
title Ubuntu Chainloader
root (hd2)
chainloader +1
```

Which seems to work better but now I get the following error:

```
FileSystem Type Unknown, using whole disk
Loading stage2Error found
```

I might have messed up my grub2 configuration on sdc. Any suggestions on how I can restore grub on sdc.

I also tried to configure my BIOS to boot directly off sdc however that also presented me with the blank screen.

---

### Post by oldfred on 2012-04-16
Chainloading from one drive to another quickly gets confusing. The boot drive is always hd0. So then the remaining drives start at hd1. Or sda is not always hd0. I boot sdb, so a chain load to sda is to hd1.

I have copied my 40_custom from one install to another and had to edit chain loads as drive numbering changed. And if you plug a USB flash drive in it may change even more. I have had flash be sde or sdb, and I am not sure why.

---

### Post by lostinspace2011 on 2012-04-27
I am still in the same position where I am getting this error 
```
FileSystem Type Unknown, using whole disk Loading stage2Error found
```
I am connecting the external drive via SATA cable and the drive is always sdc / hd2.[FONT=monospace]
[FONT=Arial]Any other suggestions to try out ?[/FONT]
[/FONT]

---

### Post by oldfred on 2012-04-27
Post boot info script results. This runs it and creates a link to the results.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

---

### Post by lostinspace2011 on 2012-04-28
Thanks. Boot-Repair fixed my problem

---

