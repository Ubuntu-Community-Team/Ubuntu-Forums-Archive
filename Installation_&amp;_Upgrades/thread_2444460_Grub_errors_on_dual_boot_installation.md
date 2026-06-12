---
title: "Grub errors on dual boot installation"
date: 2020-05-30
forum: Installation &amp; Upgrades
---

### Post by erehwon2 on 2020-05-30
I am having trouble installing Windows and Ubuntu on my old Samsung laptop.

The laptop just about supports UEFI, but not Secure Boot (that I can see) and I have previously converted my disk to GPT.  Originally I had Windows 10 on it (upgraded from Windows 8) and Elementary OS.
I then decided to change the Linux OS to Ubuntu 20.04.  Things didn't go well and I ended up wiping the entire disk and installing Windows 10 from scratch.  When I got to installing Ubuntu, I kept getting grub errors and it always failed. (I'm installing from USB using Ventoy, but I don't think this is causing any problems - I can run the Live version fine)  Windows still runs not from grub, just from its Boot Manager I think.

Ubuntu gives the following error:
	Executing 'grub-install /dev/sda' failed
	This is a fatal error
	
I also tried PopOS and it told me that sda2 (EFI) was too small at 100MB.  I increased this partition using gpartd and PopOS has stopped complaining but it still doesn't work.  Its install log is here: [https://paste.ubuntu.com/p/FzgjrqCxsF/](https://paste.ubuntu.com/p/FzgjrqCxsF/)

Ubunutu still gave the same grub error, so I ran the Boot Repair iso.
Its Boot Repair log is here: [http://paste.ubuntu.com/p/XxWR8NJBNB/](http://paste.ubuntu.com/p/XxWR8NJBNB/)
And its Boot Info log is here: [http://paste.ubuntu.com/p/mv8P3rsPdH/](http://paste.ubuntu.com/p/mv8P3rsPdH/)


Looking at the logs it looks like there still isn't enough room on sda2.  Running gpartd says there is 550MB but I think Boot Repair still thinks it is 100MB and PopOS says it is running out of space too.  Is this likely to be the cause?  If so, how do I make sure sda2 is the right size?  I'm happy to reinstall Windows, but can I specify a larger size for the boot partition?

I hope someone can help me with this.  I'm a bit out of my depth and I don't understand why this is not working as I don't think I'm doing anything to different.

---

### Post by oldfred on 2020-05-30
Line 36
```
    Boot sector info:  According to the info in the boot sector, sda2 has 
                       204800 sectors.. But according to the info from the 
                       partition table, it has 1122303 sectors.
```

I know with NTFS, after a resize you have to run chkdsk so it updates PBR, partition boot sector with correct info. PBR & partition table must match. Not seen issue with FAT32, but that is what it looks like.
Either run chkdsk from Windows for dosfsck from Ubuntu.

Must be unmounted, so run from live installer:
sudo /sbin/fsck.vfat -V <the fat32 device>
sudo fsck.vfat -t -a /dev/sda2
man dosfsck

The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)


Is this Ubuntu or PopOS? Grub entries all show POP, but POP installs most of /boot into ESP and does not use grub (as I understand it).
POP!OS  uses systemd boot:
Gummiboot is dead, of course, because it was spun into systemd 2015

Systemd boot loader spec (was gummi boot:
[https://systemd.io/BOOT_LOADER_SPECIFICATION](https://systemd.io/BOOT_LOADER_SPECIFICATION)
[https://www.freedesktop.org/wiki/Software/systemd/systemd-boot/](https://www.freedesktop.org/wiki/Software/systemd/systemd-boot/)
 systemd-boot (f. gummiboot)
[https://blobfolio.com/2018/06/replace-grub2-with-systemd-boot-on-ubuntu-18-04/](https://blobfolio.com/2018/06/replace-grub2-with-systemd-boot-on-ubuntu-18-04/)

---

### Post by VMC on 2020-05-30
> **erehwon2 said:**
> ...
I also tried PopOS and it told me that sda2 (EFI) was too small at 100MB.  I increased this partition using gpartd and PopOS has stopped complaining but it still doesn't work.  Its install log is here: [https://paste.ubuntu.com/p/FzgjrqCxsF/](https://paste.ubuntu.com/p/FzgjrqCxsF/)
...
Looking at pop errors:
```

kernelstub.Installer : INFO     Copying Kernel into ESP
[WARN distinst:crates/chroot/src/command.rs:98] kernelstub.Installer : INFO     Copying initrd.img into ESP
[WARN distinst:crates/chroot/src/command.rs:98] kernelstub.Installer : ERROR    Couldn't copy the initrd onto the ESP!
[WARN distinst:crates/chroot/src/command.rs:98] This is a critical error and we cannot continue. Check your settings to see if there is a typo. Otherwise, check permissions and try again.

```How big is pop's esp? Should be 500mb at least. Also this```
No space left on device: '/boot/initrd.img-5.4.0-7625-generic'
```

---

### Post by erehwon2 on 2020-05-31
Hmm, I'm still struggling with this.  I think you are right, @oldfred, the boot partition is a bit screwed up and needs sorting.  I ran the following commands under Ubuntu Live:
  sudo /sbin/fsck.vfat -V /dev/sda2
  sudo fsck.vfat -t -a /dev/sda2
  dosfsck -t -a -V
They ran quickly without any errors, but they didn't appear to help.  I even managed to run chkdsk on the partition from Windows but that didn't help either.  I've fiddled about, even trying to resize the partition again to try to get it to reset itself but I've ended up with a similar error ([http://paste.ubuntu.com/p/NYKsmGNBnD/):](http://paste.ubuntu.com/p/NYKsmGNBnD/):)
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 1085440.

@VMC - It does look like Pop needs a large boot partition so I set it to be more than 500MB.  I seem to remember seeing something somewhere about 500MB.  Ububtu's error is more vague but I'm assuming it needs to be bigger than 100MB.  Anyone know what is the minimum size to dual boot Ubuntu?  Could I set the size of the boot partition when installing Windows?  (Perhaps this is the wrong forum for that ;) )

Anything else to try?  I really appreciate your help.

---

### Post by oldfred on 2020-05-31
Any time you resize you have to rerun the repairs. Make sure it is unmounted.

Your ESP has a 3 line grub that tells grub where to find the rest of grub & the install.
See line 203, But that UUID does not exist for gpt7.
You need to reinstall grub or manually edit that line to have correct UUID, if the rest of grub is correct.

```
sda2/EFI/ubuntu/grub.cfg (line 203): 
search.fs_uuid d7308fca-d388-4646-899b-e3637f6e0ac5 root hd0,gpt7 
"blkid" output (line 159):
/dev/sda7        7d3c443c-c3da-40f5-975f-3f5cc071bd1c   ext4 

```

---

### Post by erehwon2 on 2020-06-01
Still not getting there. :(

I fsck/dosfsck'd the boot partition and even managed to get blkid to match grub.  ([https://paste.ubuntu.com/p/7ZjN9bgCN9/](https://paste.ubuntu.com/p/7ZjN9bgCN9/)) But Ubuntu still won't install, with the same grub-install fatal error. 

I still think it is something to do with the boot partition.  I ran fdisk and it says that sda2 has two partitions (or possibly three!) And Boot Repair says fdisk disagrees with the start point. I wonder if this what is causing the error.  Is it better that I reinstall Windows and try to get a larger boot partition to start with?  I appreciate your help, @oldfred, and your patience!

---

### Post by oldfred on 2020-06-01
The ESP looks large enough. Normally Windows makes it only 100MB which is enough for both Windows & Ubuntu. We normally suggest larger since drive's are now larger and you may need it for other uses in future.

Run both dosfsk & Windows chkdsk on sda2.Must be unmounted, so run from live installer:
Make sure unmounted.
sudo fsck.vfat -t -a /dev/sda2
man dosfsck

I have seen one or two cases where the solution was to totally delete the ESP & recreate it. Back up all files in it, but you normally then have to reinstall both Windows boot loader & grub boot loader as GUID/partUUID that ESP uses for its UEFI boot entries gets changed.
You then need both Windows repair/recovery flash drive and Ubuntu live installer.

What brand/model system?
Do you have UEFI Secure Boot off?

---

### Post by erehwon2 on 2020-06-02
It's a Samsung RV711 from 2011!  I couldn't find Secure Boot in the BIOS settings (it's more BIOS than UEFI!) and I think Secure Boot came after this.

I'll have a go at recreating the ESP.  Thanks @oldfred.

---

### Post by oldfred on 2020-06-02
A lot of the early UEFI implementations were buggy. Vendors did fixes, Linux created work arounds and now most UEFI work, many still require some settings in UEFI and/or boot parameters.

If from 2011, it was before Windows required UEFI/gpt for Windows 8 in 2012. They probably released an UEFI to test or make sure it worked. UEFI currently has CSM. Some give up on UEFI and just use CSM.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
Windows 7 also could be installed in UEFI mode, so your system may have used UEFI or CSM/BIOS.

---

### Post by erehwon2 on 2020-06-03
I did manage to move from MBR to GPT on a previous installation and then my new Windows installation was able to use GPT.  But it is an early version of UEFI so may not be perfect.

But I still keep thinking that I did have Windows and Linux (Elementary) previously installed.  I'm ever hopeful!

---

