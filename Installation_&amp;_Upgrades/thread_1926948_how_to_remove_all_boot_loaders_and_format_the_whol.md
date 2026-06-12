---
title: "how to remove all boot loaders and format the whole disk?"
date: 2012-02-17
forum: Installation &amp; Upgrades
---

### Post by esalehi on 2012-02-17
Hi guys,

I had openSuse on my laptop and tried to install Ubuntu 11.10 alongside it using a bootable CD. It stopped while copying files for about an hour, file 55/117, and I was forced to shut it down by the power key :(
Created a bootable flash memory and installed again, everything went well unless there is no boot menu in the startup. I formatted the partition which had Opensuse and still I have opensuse boot option and no ubuntu.
The only way to go through my laptop is using a bootable CD/USB OR install Mandriva. Even OpenSuse cannot be reinstalled.

Is there any way to remove ALL boot loaders from the disk so I can reinstall Ubuntu? I have a full backup of the system. 
I'm in deep **** and really appreciate your help.

---

### Post by darkod on 2012-02-17
If you already installed ubuntu and only the bootloader (grub2) is missing, you can add only grub2. No need for new reinstall.

Can you run the boot info script from the link in my signature and post the results as explained there? It will show more details.

---

### Post by stn21 on 2012-02-17
> **esalehi said:**
> Is there any way to remove ALL boot loaders from the disk ...

Bootloaders can be in the MBR and in the bootrecords of each partition.

To erase all of them try to boot ubuntu live and then use gparted to create a new partition table. That should overwrite the MBR and erase all partitions. After that the disk is completely empty and all bootloaders should be gone.

"Only" erasing any bootloaders might be more difficult. The only way I can think of is to use a hex-editor on each partition. You would have to research the structure of boot-records first.

---

### Post by ottosykora on 2012-02-17
>to create a new partition table. That should overwrite the MBR <

not exactly, partition table yes, but this is not the mbr yet

---

### Post by esalehi on 2012-02-17
> **darkod said:**
> If you already installed ubuntu and only the bootloader (grub2) is missing, you can add only grub2. No need for new reinstall.

Can you run the boot info script from the link in my signature and post the results as explained there? It will show more details.


The result was so huge, It is attached as RESULTS.txt

---

### Post by esalehi on 2012-02-17
> **stn21 said:**
> Bootloaders can be in the MBR and in the bootrecords of each partition.

To erase all of them try to boot ubuntu live and then use gparted to create a new partition table. That should overwrite the MBR and erase all partitions. After that the disk is completely empty and all bootloaders should be gone.

"Only" erasing any bootloaders might be more difficult. The only way I can think of is to use a hex-editor on each partition. You would have to research the structure of boot-records first.

Running in live USB I went to GParted then Device and created new partition table, selected the default one which was DOS compatible partition table and it warned me of erasing the whole disk, I accepted and finished. Unfortunately nothing good happened and the bloody OpenSuse bootloader still has embraced my disk and there is no ubuntu boot option.

---

### Post by stn21 on 2012-02-17
> **esalehi said:**
> Unfortunately nothing good happened and the bloody OpenSuse bootloader still has embraced my disk and there is no ubuntu boot option.

Can you at least boot OpenSuse ?

---

### Post by stn21 on 2012-02-17
> **ottosykora said:**
> >to create a new partition table. That should overwrite the MBR <

not exactly, partition table yes, but this is not the mbr yet

You are right, I was not precise. The next thing I would have suggested would have been to overwrite the mbr, for example with ```
install-mbr /dev/sda
```But erasing all partitions should have already solved the problem at hand.

It did not solve it though. I don't think the MBR is the problem here. IMHO the problem simply is that there are two harddisks and the harddisk that boots was not the one erased. So the boot-process is still messed up. Not sure of course because a second harddisk was not mentioned, except in RESULTS.TXT.

Also it seems that booting still brings up a Suse-bootmenu. That does not sound like an erased harddisk to me.

Erasing the first hdd too should reset the system so that it can be reinstalled. Explicit overwriting the MBR should not be necessary because installing grub in the MBR during installation will do that anyway.

Not sure about all this, would have to check with [esalehi]("http://ubuntuforums.org/member.php?u=1554906") first...

---

### Post by darkod on 2012-02-17
> **esalehi said:**
> Running in live USB I went to GParted then Device and created new partition table, selected the default one which was DOS compatible partition table and it warned me of erasing the whole disk, I accepted and finished. Unfortunately nothing good happened and the bloody OpenSuse bootloader still has embraced my disk and there is no ubuntu boot option.

The results say you have GPT table on the hdd. Did you write a new MSDOS table after that?

In the results, you are using two fairly new options, GPT table on the disk and EFI boot. I don't use neither.

There have been a number of problems reported and I am not sure if the combination GPT + EFI works out of the box.

Unless you really have a reason to use gpt, I would recommend writing a new msdos table (maybe you already did that), and also changing in BIOS to use standard BIOS boot, not EFI boot.

Personally I don't see any advantage in gpt or efi in a single OS system and you seem to want to install only ubuntu. I would stick to the older, proven options, msdos table and bios boot.

If you intend to continue with gpt + efi, google around for a solution. The issue lies there.

---

### Post by esalehi on 2012-02-22
Here is how the problem fixed:

1- install Mandriva 2010 32bit 
2- Installed Ubuntu 10.04 32bit alongside Mandriva
3- Upgrade Ubuntu (if you want newer version)

everything works fine :)

---

