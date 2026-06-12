---
title: "BIOS will not detect boot drive (Dell Precision 7910 and hardware raid)"
date: 2020-03-25
forum: Installation &amp; Upgrades
---

### Post by racedog on 2020-03-25
Hi, I'm having trouble installing Ubuntu on my refurbished Dell Precision 7910 Workstation.  It has a hardware RAID controller.  I went into the raid controller and created and formatted the logical volume.  The controller also reports:

[LIST]
[*]Slots 4 and 5 are configured for raid disk drive and status is ok
[*]Sas topology: flagged logical volume as boot device
[*]Adapter is enabled
[*]Boot order for device is 0
[*]Boot support enabled for BIOS and OS
[*]
[/LIST]

Booting into the live USB, I can do the following:

lspci reports -> 01:00.0 Serial Attached SCSI controller: LSI Logic / Symbios Logic SAS3008 PCI-Express Fusion-MPT SAS-3 (rev 02)

I am also able to view and  mount the partition and see a fully installed Ubuntu filesystem.

The partitions visible are a 1 mb grub partition, a swap partition and the main raid volume.

The BIOS screen still says no boot device found.

What could I be missing?  Any help is greatly appreciated!  Thanks!

---

### Post by aljames2 on 2020-03-25
It could be a Legacy mode vs. UEFI boot issue.  It sounds like Ubuntu was installed in Legacy BIOS mode while your BIOS is booting in UEFI mode.  If Ubuntu were installed in UEFI mode you would normally see a separate fat32 partition labeled EFI for UEFI booting.  You may try and look for an option in the BIOS to boot in Legacy mode and see if that works.  

What I typically do on fresh Ubuntu installs on my UEFI mobos is before starting, use GParted to create 1 fat32 partition (550 MB) and label it EFI and tag it as boot/esp.  Then I run the installer USB.

Not sure if this is your issue, but worth a look.

---

### Post by dragonfly41 on 2020-03-26
[COLOR=#000000]> What I typically do on fresh Ubuntu installs on my UEFI mobos is before starting, use GParted to create 1 fat32 partition (550 MB) and label it EFI and tag it as boot/esp. Then I run the installer USB.

I am on Dell, triple boot with internal and external Ubuntu. Win 10 sleeping.

Just to expand on above tip I create a boot partition on external drive (SSD) using Gparted - but also add boot flags.  This allows the option of external drive to boot up if internal drive is power cable removed (in an emergency). [Another approach I have read]("https://forums.linuxmint.com/viewtopic.php?t=287353"), avoiding the need to dive inside to disconnect internal drive, is to use Gparted (from LiveUSB) to remove boot flags (as a temporary measure) in internal Win 10 drive.  The principle is that this forces external Ubuntu only to boot ignoring the now "boot disabled" Windows. I am guessing that this approach might be used in a single internal drive with multiple EFI partitions (I understand from reading many threads that this is possible, but I now aim to place Windows and Ubuntu on separate drives).  Clearly you need a working LiveUSB to recover boot scenarios.

Also I now install rEFInd as a supplementary boot loader which nicely coexists with default Grub2 system.[/COLOR]

---

### Post by racedog on 2020-03-26
OK so sadly I tried creating a fat32 partition but to no avail.  I am definitely using legacy boot mode.  Not sure how to set it to UEFI mode.  The short term fix was to install Fedora Workstation.  I am now up and running on this.  Not sure what that installer did that Ubuntu did not.  I do have a separate boot partition where ubuntu did not.  I will attempt again shortly.  Thanks for the suggestions.

---

