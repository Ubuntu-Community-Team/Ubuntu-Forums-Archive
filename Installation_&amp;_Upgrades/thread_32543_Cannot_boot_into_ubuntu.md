---
title: "Cannot boot into ubuntu"
date: 2005-05-08
forum: Installation &amp; Upgrades
---

### Post by joesta on 2005-05-08
Installed boot to ubuntu's logical partition of a harddrive, cannot boot into it at startup

Hi, I'm a novice linux user and decided to install ubuntu on my computer alongside Windows XP, in order to aquaint myself with the linux OS even further.  I have repeatedly messed up the MBR by installing the Ubuntu as directed with the GRUB loader, plus once installing another distro with the LILO loader.  Therefore I installed  Ubuntu onto a logical partition, and put the GRUB loader in that drive, with the instention of running the command:

```
dd if=/dev/hda5 of=/datashared/ubuntu.bin bs=512 count=1
```

where** /datashared** is a 1Gb  fat32 partition I created to share data between Windows XP and Ubuntu.

The only problem is thatI cannot boot into Ubuntu, or ge to any place that allows me to execute that command.  I have inserted the Ubuntu live Cd with hope of doing so, after mounting the devices to a folder on the Desktop (**/home/ubuntu/Desktop/hda5**) and also an attemp to mount the floppy (**/home/ubuntu/Desktop/floppy**), using the command:
```

dd if=/home/ubuntu/Desktop/hda5 of=/home/ubuntu/Desktop/floppy/ubuntu.bin bs=512 count=1
```
and
```
/dev/hda5 of=/home/ubuntu/Desktop/floppy/ubuntu.bin bs=512 count=1
```

It seems that I do not have permission to access the hda5 drive, I have also tried this using the live CD Knoppix (which I have once used originally to partition my harddrive).  Therefore I am now lost, and cannot think of any way to copy the bootloading sector of ubuntu to a shaered directory, or a floppy disk, so that I can add the linux.bin file to windows XP, and create a reference from the WinXP bootmanager to this.  I would prefer to use the windows bootmanager as opposed to Grub, since Grub and Lilo have cause me too many problems.  

If anybody could help then it shall be deeply appreciated.

Joesta

---

### Post by MavisCruet on 2005-05-08
Hmmm, I have a similar issue, the grub installer and lilo both failed on the expert installation, didn't specify why, and so as a resut, though I think the installation went fine, I have no boot menu.  Any suggestions?

Just as a thought, would it make a difference that the drive is SATA?

I have managed to create a partition on there, what are the best settings to use?

---

### Post by joesta on 2005-05-09
.

---

### Post by joesta on 2005-05-09
[QUOTE=joesta].[/QUOTE]
 If anybody has any solutions I would appreciate the help.  Ubuntu is still inaccessible :(

Is there any way to boot into ubuntu linux, without lilo or grub on the mbr?  I do not have a boot disk.
Or is there anyway I can make windows recognise where Ubuntu is?

---

### Post by blakdogg on 2005-05-10
I haven't run dual boot in years, but your approach seems somewhat odd. I think the boot loader (grub/lilo) has to be on the boot partition, which isn't usually logical - not sure it can be logical.

If you are worried about messing up Windows, I would suggest trying a boot floppy this should allow you boot.

---

### Post by kosmic on 2005-05-10
When installing in expert mode, the way to install GRUB to the Master boot record is :

if your drive is HDA

then in the line that lets you chosse where do you want to install GRUB wirte :

/dev/hd0 (its a zero) and it will install in the MBR

---

### Post by spd106 on 2005-05-10
hi, i understand your frustration, but the easiest and more common way is to have grub (or lilo) in the mbr. 

You can use the windows bootloader instead, as you have found it won't be straight forward to setup though.

I assume you are following a guide. A quick google turned up this page
[http://www.highlandsun.com/hyc/linuxboot.html](http://www.highlandsun.com/hyc/linuxboot.html)
that might be some use.

it might be worth running fsck to check your file systems aren't corrupt first.

Hope this helps

---

### Post by xubuntu on 2005-11-17
I think the initial question was never anwered.:(  
I have the same problem that I can not boot to my sucessfully installed ubuntu because I have not installed the boot loader in the MBR, since I would never take the risk to get in trouble with my windows XP installation.

But my big question now: Is there another solution to get a linux.bin without the "dd"-command. I guess the boot sector should be allways the same on all installation, isn't it? Please inform me if not. If yes, i guess an image of the boot sector should be somewhere on the installation cd. Does anybody know where.  Or does anybody know where I can get the linux.bin File from the internet? Thanks for any help.

---

