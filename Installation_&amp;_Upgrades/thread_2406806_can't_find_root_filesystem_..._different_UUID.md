---
title: "can't find root filesystem ... different UUID"
date: 2018-11-26
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2018-11-26
because one of the fans died on my laptop that has been serving me daily for the past 4 years. i obtained another one just like it that had been hardly used.  instead of doing another install and trying to re-do all the changes i've made, i decide to just image the hard drive to the replacement. which has an exactly identical storage device setup with exactly the same size drives (1000204886016 bytes for [FONT=courier new]/dev/sda[/FONT] on both). so i plugged in a USB drive with a substantial amount of free space, and copied an image of the whole /dev/sda compressed with [FONT=courier new]_gzip -1_[/FONT] which occupied about 780MB in one big file.  that same USB drive was also a bootable rescue system, which i booted on the new laptop.  then i uncompressed that big image file and imaged it onto the new [FONT=courier new]/dev/sda[/FONT].  [FONT=courier new]_fdisk -lu /dev/sda_[/FONT] showed me all the original partitions.  sda1 had the full system except /home. sda2 had the swap space.  sda4 was /home (about 85% of the whole drive).

then i rebooted and let BIOS bring up sda, which was the default system.  i then got a text mode error message basically saying it could not find the root file system and displayed a UUID which was hard to read.  i managed to get the last 6 digits from it as "aab8e0".

this was odd to me since the boot loader, kernel, and /[FONT=courier new]etc/fstab[/FONT] were all part of the whole drive image and should still be a match.

i looked closer and found that the sda1 and sda4 filesystems (using [FONT=courier new]_tune2fs -l_[/FONT]) had a different UUID than any listed in [FONT=courier new]/etc/fstab[/FONT].  and none of these had "[FONT=courier new]aab8e0[/FONT]" in them.

1.  **how can these UUIDs not have matches since they were all from the same one big whole device image?**

2.  **what can i do to fix this?**

i did change [FONT=courier new]/etc/fstab[/FONT] to match the file systems.  rebooting to sda got the same error (with a UUID ending in "[FONT=courier new]aab8e0[/FONT]").

i restored [FONT=courier new]/etc/fstab[/FONT] and changed file system UUID to match (with [FONT=courier new]_tune2fs -U_[/FONT]).  rebooting to sda still got the same error (with a UUID ending in "aab8e0").

i looked through all the UUIDs in [FONT=courier new]/boot/grub/grub.cfg[/FONT] and they matched the original [FONT=courier new]/etc/fstab[/FONT].

unless i can resolved this strange error, it looks like i'll need to do a fresh vanilla install and copy tons of individual files to the new laptop and make all the manual changes that don't get carried over in files.

---

### Post by oldfred on 2018-11-26
I do believe in new clean installs. All your user settings & data is in /home. 
Only if server apps are installed that usually are in / like database or web may you also need that backed up. 
It also then is a good test that your backup procedures are valid. And if any data is missing from backup, you still have old drive to go back to to get missing data.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Skaperen on 2018-11-26
i have a login system setup that starts up 12 users automatically.  i need to make sure that is all there.

i have rm'd that big compressed image file and am working on rsyncing everything to that USB drive.  i'll be leaving out, or rm-ing system stuff i don't need to change even though i expect it to be the same.  then after i do the fresh install, i can rsync this over it.

but i am still curious where these extra UUIDs came from. have they start using UUIDs with hardware?  i still remember the old days when /etc/fstab had device names coded in and the kernel could renumber everything.  i remember making my own filesystem finder to get the correct filesystem mounted.  it used a symlink at the top named "__mountpoint__".  but i never did mod the kernel to hunt for  __mountpoint__ -> /

---

### Post by oldfred on 2018-11-26
If new UEFI system, it should be using gpt. And gpt had GUID in partition, primary partition table & backup partition table. They must all match. 
But if restoring a full drive it should be same, but if it is just copying data into new partitions your GUIDs will not match. May be fixable with gdisk or sgdisk.

       repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by Skaperen on 2018-11-26
the original hard drive is a hybrid format with both MBR and GPT (including the backup table at the end of the drive) partition tables.  so the clone will be, too, since it was a full drive image copy, not a copy of individual files.  but i have rm'd that big image file (i'm done trying to make it work), and after some cleanup, have rsync'd the whole laptop#1 file tree to the USB drive.  next, i will install 16.04.5 amd64 via an 8GB minne pinne into partition#1 of laptop#2 followed by an overlay of the file tree from the USB drive to the new system on laptop#2 will running a live Ubuntu (so i'm not modifying a system while it us up) from the same minne pinne.

16.04 LTS will be my system until 20.04.1 LTS comes out.  i am skipping 18.04 LTS (except maybe in a container).

---

### Post by oldfred on 2018-11-26
If just running Ubuntu, why a hybrid partitioning system. 
That was more for Mac with older Windows that would only boot in BIOS mode on Mac's gpt drive.

       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

---

### Post by Skaperen on 2018-11-27
i'm not going to just copy files.  what i will be doing is install a fresh new system using the 16.04.5 desktop amd64 iso imaged onto a minne pinne (yet to do but got it downloaded) and having it use existing MBR partions (my laptop is an older system76 model that is not UEFI (plugged in disks with only MBR boot up fine).  if the fact that GPT is also there causes problems, i'll just wipe it off and leave only MBR.  MBR can easily do up to nearly 2TB and with a particular arrangement, up to nearly 4TB.

---

### Post by Skaperen on 2018-11-27
> **oldfred said:**
> If just running Ubuntu, why a hybrid partitioning system. 
That was more for Mac with older Windows that would only boot in BIOS mode on Mac's gpt drive.

       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

no reason for Ubuntu.  it was leftover from testing some of own code.

---

### Post by oldfred on 2018-11-27
I prefer gpt, and you only need MBR if installing Windows in BIOS mode.
And some of the proprietary methods of making MBR work over 2TB do not work with Linux. Most were to make large drives compatible with XP.

But if BIOS boot with gpt, you do need 1 or 2MB unformatted bios_grub partition, anywhere within the first 2TB of a drive for grub to install.

---

### Post by CatKiller on 2018-11-27
> **Skaperen said:**
> but i am still curious where these extra UUIDs came from.

New UUIDs are generated whenever a partition is created.

Don't forget that you would need to run update-grub and update-initramfs to have any effect if you had changed anything about your boot environment.

---

### Post by Skaperen on 2018-11-27
MBR's 2 GB limit applies in 2 ways.  the starting sector of every partition must be below the 2 GB mark.  the size of every partition must less than 2 GB.  if the last partition's size greater than (2GB - start) then the partition will run past the 2 GB mark,  if Linux does this calculation in 32 bit signed int then it will come up with incorrect (negative) position values.  but if it uses 32 bit unsigned or 64 bit, then it can produce valid values for positions.  this means the last partition can run from a starting position below the 2 GB mark to a position *above* the 2 GB mark.  in the most extreme case a partition can run from 1 sector below the 2 GB mark to 2 sectors below the 4 GB mark.  i do not know if Linux can support this.  but since it supports GPT, the structs holding the running partitions can.  it's just a matter of how it calculates the ending position, if it needs that number, or how it validates what it gets.  and i do not know if any existing tools can set this up.  i intend to try it whenever i get a 4 GB or larger storage device.  if no tools can set it up, i may try to write something simple to do it, such as a program with all the MBR fields populated by hard coded values, in either C or Python (the 2 major languages i code in, now).

---

### Post by oldfred on 2018-11-27
I have been using gpt since about 2010 with BIOS on a 160GB drive. Windows XP was on a separate MBR drive.
I just recommend gpt, since MBR is from 1980's and has many kluges to make it work with more modern systems.
       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by Skaperen on 2018-11-28
> **CatKiller said:**
> New UUIDs are generated whenever a partition is created.

Don't forget that you would need to run update-grub and update-initramfs to have any effect if you had changed anything about your boot environment.

got it.  i didn't think about it at the time or else i would have wiped off the GPT tables since all it really needs is the MBR one.  i may try that, anyway, even though i have rm'd the compressed image file from the USB disk that had it (a 1TB unit that has my 32GB minne pinne rescue system imaged on it with an ext4 in partition 3 filling out the remainder) since that laptop's 1TB drive should still have the image on it (i'm back on the 1st one right now).  this time i can just grab one of the 32 GB rescue minne pinnes instead of the 1 TB drive to boot it up enough to wipe off the GPTs.

plan b is to wipe the GPT tables, anyway (to work on just MBR) and do a full fresh install of Ubuntu 16.04.5 (on my 8 GB minne pinnes) and load my original files (now all on the 1 TB USB drive) to it.  then reboot to see if it's good.

---

### Post by Skaperen on 2018-12-05
i gave up and just backed up all the files from the old laptop to a 2TB USB hard drive.  both laptops have sda = 1TB hard drive, sdb = 120 GB SSD, sdc = exact same size as sda.  i install 16.04.5 LTS desktop on each of the 3 devices and overlaid most of the backup files to the sda system (host name lt2a).  i reorganized my system setup so that it doesn't have changes to Ubuntu files and uses lots of sudo (3 scripts are invoked via sudo).  now it's a lot simpler and probably more portable to 20.04 LTS when it comes out.  i'm submitting this post on the 2nd laptop.  with 3 systems on one machine, i can now do things like synchronize the 2 hard drives from a separate system so it can be in perfect sync.

---

