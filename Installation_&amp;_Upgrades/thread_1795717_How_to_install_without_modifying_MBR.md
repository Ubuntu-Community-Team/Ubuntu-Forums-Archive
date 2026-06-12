---
title: "How to install without modifying MBR?"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by Luke M on 2011-07-03
When I installed ubuntu on an HD with an existing OS it placed GRUB in the MBR without asking. Maybe there was an option that I missed? How do you I tell the installer to confine itself to the install partition and leave the MBR alone? (I'll use the system BIOS to select the boot partition).

---

### Post by YesWeCan on 2011-07-03
Hi. Good question. :)
There are a few answers I can give you,
1) The latest Ubuntu installer is remiss by not making you explicitly choose where the Grub boot code is put, except if you choose "something else"/"Advanced". There is a pull-down menu where you can choose among partitions.

2) The Grub boot system does not work reliably when the boot code is put in a partition in the way that the Ubuntu installer and grub-install does it. It creates a dependency between the boot code and the absolute sector address of a file in /boot. There are some circumstances when the location of this file may change.

3) Because of 2) the file, core.img, is put in sectors 1 to 50 (approx) on the disk where it won't move and the boot code is put in the MBR in sector 0, thus wiping out the standard boot code that Windows relies on. This does not mean that the boot code has to be in the MBR. It can be in a partition instead.

...confused yet?

4) I agree with you that all the Ubuntu boot stuff should be contained in the Ubuntu partition. But this is not reliably supported by Ubuntu. You can achieve a compromise by installing as normal to the MBR area and then moving just the sector 0 boot code to the start of a primary partition, then restore the standard boot code and set the boot flag for that partition. This will avoid almost all Windows MBR conflict issues.

5) Easier and most reliable is to install Grub to the MBR of a separate disk. Even a USB stick. The Grub MBR and boot file need not be on the same disk as the /boot partition.

---

### Post by mikewhatever on 2011-07-03
> **Luke M said:**
> When I installed ubuntu on an HD with an existing OS it placed GRUB in the MBR without asking. Maybe there was an option that I missed? How do you I tell the installer to confine itself to the install partition and leave the MBR alone? (I'll use the system BIOS to select the boot partition).

That has always been the default behavior. If you want it modified, choose the advanced partitioning option (it's now called 'Something else').


> **YesWeCan said:**
> 

4) I agree with you that all the Ubuntu boot stuff should be contained in the Ubuntu partition. But this is not reliably supported by Ubuntu. You can achieve a compromise by installing as normal to the MBR area and then moving just the sector 0 boot code to the start of a primary partition, then restore the standard boot code and set the boot flag for that partition. This will avoid almost all Windows MBR conflict issues.



You can install Grub entirely to the root partition, but then, how would you boot the new installation? Do you think it a good idea to make new installations unbootable by default?

---

### Post by YesWeCan on 2011-07-03
> **mikewhatever said:**
> You can install Grub entirely to the root partition, but then, how would you boot the new installation? Do you think it a good idea to make new installations unbootable by default?
Good point, you also need to make the root partition active/bootable. This can be done easily in GParted or Disk Utility or using sfdisk.
Alternatively, keep Windows active and add the Grub boot sector in a file to your Windows loader and select your OS using Windows.

---

### Post by Morbius1 on 2011-07-03
After you select the "Something Else" option you will eventually see a screen that looks like the attached. You can put it on sda or sda1, sda2, sdawhatever.

---

### Post by mikewhatever on 2011-07-03
> **YesWeCan said:**
> Good point, you also need to make the root partition active/bootable. This can be done easily in GParted or Disk Utility or using sfdisk.

Actually, you don't. Apparently, the boot flag is a Windows thing, and Grub doesn't really care about it.

> 
Alternatively, keep Windows active and add the Grub boot sector in a file to your Windows loader and select your OS using Windows.

That is easier said then done, also, what if there is no Windows installed?

---

### Post by YesWeCan on 2011-07-03
> **mikewhatever said:**
> Actually, you don't. Apparently, the boot flag is a Windows thing, and Grub doesn't really care about it.

That is easier said then done, also, what if there is no Windows installed?
Sorry, I am not being very clear.
The boot flag is used by standard MBR boot code. The boot code loads and executes the partition boot code of the "active" partition. The active partition doesn't have to be Windows. The same method can run the Grub boot code when it is installed in a partition boot sector.
The Grub boot code ignores the partition table (it has its own table of OS's in another file) and simply loads and runs another Grub file. So yes, when the Grub code is in the MBR the boot flag is ignored.
So I'm saying use the standard MBR code and set the partition that conatins the Grub boot code to be "active" (note, this can be any primary partition that isn't already being used for booting something).

---

### Post by Luke M on 2011-07-03
> **Morbius1 said:**
> After you select the &quot;Something Else&quot; option you will eventually see a screen that looks like the attached. You can put it on sda or sda1, sda2, sdawhatever.

 Ah...I missed that option. I guess the "device" language threw me off - I don't automatically associate devices with partitions.  By the way, do you really need a swap partition? I think the install won't let you proceed until you create one.

---

### Post by srs5694 on 2011-07-03
> **Luke M said:**
> (I'll use the system BIOS to select the boot partition).

A standard BIOS doesn't let you select a boot *partition*, although most or all BIOSes made in the past 5 years (at least; maybe 10 or more) enable you to select a boot *disk*. The BIOS then loads the MBR boot code and executes it. That code decides how to proceed with the boot process.

If you're using a DOS/Windows MBR, the boot loader code runs the code in the boot sector of the partition that's marked as "active." Normally, only one partition will be so marked -- but it's possible to put a boot loader there (and in related files that are boot loader-specific) to redirect the boot process to another partition.

Thus, if you want to leave the MBR's boot code alone, you can do so (at least in theory), but you'll probably need non-BIOS tools to select your OS -- either a boot loader in the active partition that's capable of chainloading other boot loaders or an fdisk-type tool to change the active partition whenever you want to boot another OS. (This second option would be extremely awkward, of course.) The only way in which you can use BIOS options to select your boot OS is if you've got at least two disks, in which case you can store different boot loaders in the MBRs of the two disks, or even use the same DOS/Windows boot loader in each one but set up your OSes so that one uses an active partition on one disk and the other uses an active partition on the other disk.

That said, the (relatively) new UEFI system of booting *does* enable you to select the boot OS from within the firmware. This isn't done by selecting a boot *partition*, though, (or even a boot disk) but by selecting a *boot loader file* on the EFI System Partition (ESP), which is a partition that exists to hold boot loaders, EFI drivers, etc.

---

### Post by Morbius1 on 2011-07-03
> **Luke M said:**
> Ah...I missed that option. I guess the "device" language threw me off - I don't automatically associate devices with partitions.  By the way, do you really need a swap partition? I think the install won't let you proceed until you create one.
Usually at this point in the install there's a moment of sheer terror that you're not telling the installer to reformat that 1TB data partition that you want it to mount so it's easy to overlook.

As for swap I'm not sure. You would think with the amount of RAM that comes with current machines it isn't necessary but doesn't hibernate depend on swap?

---

### Post by Luke M on 2011-07-03
Well I have to confess I lied about using the BIOS...I actually use the PLOP boot manager. It's in ROM though so it works like a BIOS feature.

---

### Post by Morbius1 on 2011-07-03
I never heard of PLOP. I use BootIt-Bare Metal myself.

---

### Post by srs5694 on 2011-07-04
> **Morbius1 said:**
> As for swap I'm not sure. You would think with the amount of RAM that comes with current machines it isn't necessary but doesn't hibernate depend on swap?

Yes, for hibernate (suspend-to-disk) functionality, you need swap space that's at least as large as your RAM.

[quote=Luke M]Well I have to confess I lied about using the BIOS...I actually use the  PLOP boot manager. It's in ROM though so it works like a BIOS feature.[/quote]

I've never used PLOP, but based on [its Web site,](http://www.plop.at/en/bootmanager.html) it looks like a standard disk-resident boot loader, not something that you put in ROM. (The [features page](http://www.plop.at/en/bootmanager.html#features) mentions where it can be installed: "Start of the boot manager from harddisk, floppy, USB, CD, DVD".) Storing any disk-resident boot loader in a standard PC's ROM would be tricky, although probably not impossible if you had sufficient skills or were following instructions from somebody with such skills. Is that what you've done?

---

### Post by Luke M on 2011-07-05
> **srs5694 said:**
> Yes, for hibernate (suspend-to-disk) functionality, you need swap space that's at least as large as your RAM.
 
 
 
I've never used PLOP, but based on [its Web site,]("http://www.plop.at/en/bootmanager.html") it looks like a standard disk-resident boot loader, not something that you put in ROM. (The [features page]("http://www.plop.at/en/bootmanager.html#features") mentions where it can be installed: &quot;Start of the boot manager from harddisk, floppy, USB, CD, DVD&quot;.) Storing any disk-resident boot loader in a standard PC's ROM would be tricky, although probably not impossible if you had sufficient skills or were following instructions from somebody with such skills. Is that what you've done?
 
Plop is designed to go into ROM, among other places. You can easily put it on any expansion ROM (e.g. ethernet card), or if you are brave, insert it into your system BIOS. Back to the subject of installing ubuntu...I reinstalled and this time selected the install partition for booting, or so I thought. However, it didn't work; the install partition doesn't have a boot sector. I didn't change the partition type to primary, which may have been a mistake. After installing, I changed the partition type to primary (and it mounts fine), but of course it doesn't boot since there's no boot sector.

---

### Post by Luke M on 2011-07-05
I ran the boot-repair program and was able to put grub on a partition (using the "force" option) without reinstalling.

---

