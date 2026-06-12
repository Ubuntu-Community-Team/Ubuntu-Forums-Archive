---
title: "Configuring grub-pc"
date: 2024-11-24
forum: Installation &amp; Upgrades
---

### Post by peyre on 2024-11-24
My laptop was running on a 128GB SSD, and it was getting a little full - but I came into a 250GB SSD.  So I used Clonezilla to transfer to the bigger drive.  It booted up, so I rebooted to a live DVD and used gparted to expand the partition out to use the whole disk.  It booted successfully, everything's great, and I have lots of free space now.  Before shutting down I thought I'd check for the latest updates.  I didn't pay much attention to what needed updating, but now I'm faced with a dialog I've never seen before.  (I wish I could post a screenshot.)

Title bar says **Configuring grub-pc**.  It says GRUB install devices:  and the options are:
/dev/sda (250059 MB; Samsung_SSD_850_EVO_250GB)
- /dev/sda3 (249519 MB; /)

What in the world?  Sounds like it's asking where I want to install the grub bootloader?  Why is it asking this, and why choose between the drive itself and a specific partition on it?  And which should I choose?  I have to admit I'm very shaky on the details of Linux booting.

---

### Post by peyre on 2024-11-24
Ok, so I selected both (since the help dialog recommended doing so if you weren't sure).  Then it comes back to the same **Configuring grub-pc** window, but instead of offering drives it has only a checkbox for "Continue without installing GRUB?"  The Help button brings up a window that LIES to me.  It says "You chose not to install GRUB to any devices."  No you stupid installer, I told it to install to *both* devices, just like you recommended. 

So I said to go ahead and not install GRUB, since it doesn't offer to.  Then it did its thing and came back to the same window again, offering:
/dev/sda2 (537 MB; /boot/efi) on 2550059 MB Samsung_SDD_850_EVO_250GB

I selected that, and it came back to the same window again with only "Continue without installing GRUB?" available.  It went back and forth between these last two several times, then finally ended saying it didn't install successfully, then "The software on this computer is up to date."

This has to be the strangest thing I've seen with a Linux update anywhere.

---

### Post by 1fallen on 2024-11-24
Can you show us this peyre
```
[FONT=monospace][COLOR=#000000]sudo update-grub[/COLOR]

[/FONT]
```[FONT=monospace]
[/FONT]

---

### Post by tea for one on 2024-11-24
> **peyre said:**
> Title bar says **Configuring grub-pc**.  It says GRUB install devices:  and the options are:
/dev/sda (250059 MB; Samsung_SSD_850_EVO_250GB)
- /dev/sda3 (249519 MB; /)
You should always choose the disk not the partition.
/dev/sda in your case.

---

### Post by peyre on 2024-11-24
Sure.  It says:

```
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.11.0-9-generic
Found initrd image: /boot/initrd.img-6.11.0-9-generic
Found linux image: /boot/vmlinuz-6.8.0-47-generic
Found initrd image: /boot/initrd.img-6.8.0-47-generic
Found memtest86+x64 image: /boot/memtest86+x64.bin
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done

```

---

### Post by peyre on 2024-11-24
> **tea for one said:**
> You should always choose the disk not the partition.
/dev/sda in your case.

Good to know, thanks!

---

### Post by 1fallen on 2024-11-24
> **tea for one said:**
> You should always choose the disk not the partition.
/dev/sda in your case.
+1 I guess I could/should have led with that.

---

### Post by grahammechanical on 2024-11-24
> You should always choose the disk not the partition. /dev/sda in your case.

Excuse me, but ... On a BIOS motherboard we install to the Master Boot Record (MBR) of **a drive**. But with a UEFI motherboard and GUID Partitioning Table (GPT) we install to the EFI System **partition**. Is this not correct? Open the Disks utility and see. On my machine I would re-install Grub with this command:

```
sudo grub-install /dev/nvme01n1p1
```

  = first **partition**.

When installing Ubuntu and choosing the Interactive install option and then Manual install option we eventually get to see a partition layout if the drive is already partitioned. We select a **drive** to install Grub. If there is an already existing EFI System partition then that **partition** is selected to be /boot for the new OS.

This user cloned a drive so he/she has Grub in two partitions. One on each drive But with the configuration files of the smaller drive. What she/he should have done on that first reboot was to grub-install to the EFI system partition on that larger drive and then booted into the original drive and then ran grub-install on that smaller drive as well. If os-prober had not been disabled then he/she would be able to boot into either OS whatever drive had the boot priority in the UEFI settings utility.

Earlier on today I installed Ubuntu 25.04 development version on a SATA drive that already had Ubuntu 24.10 on it. I did what I have just written. As the SATA drive is in an USB drive enclosure and will not always be connected to the laptop I did not need to grub-install on either the external drive or the internal drive. 

Regards

---

### Post by tea for one on 2024-11-25
@grahammechanical

I read your reply with interest and I’m pretty sure that both commands will work.
Although, if installing Grub to a partition during a running session (not a live session), the user will have to be completely sure of the target partition. 
Just to add more confusion, the image in the Ubuntu tutorial below shows sda2 as the ESP (as opposed to sda1)

When installing to a disk (nvme0n1), [COLOR="#0000FF"]grub-install[/COLOR] somehow “knows” that an ESP is present and manages to find it and complete the command.
I tried to find definitive proof for my thoughts but failed dismally.
The Grub and UEFI manuals make my eyes glaze over.

Also, when you reach the page for installing the bootloader during the Ubuntu 24.04 installation process, the default destination is the disk rather than the partition.
Type of Installation > Manual Partitioning from [https://ubuntu.com/tutorials/install-ubuntu-desktop#6-type-of-installation](https://ubuntu.com/tutorials/install-ubuntu-desktop#6-type-of-installation)

Anyway, during a normal booted session, I tested my theory and your theory and both worked – see below.

```
redact@gmktec:~$ sudo grub-install /dev/nvme0n1
[sudo] password for redact: 
Installing for x86_64-efi platform.
Installation finished. No error reported.
```
```
redact@gmktec:~$ sudo grub-install /dev/nvme0n1p1
Installing for x86_64-efi platform.
Installation finished. No error reported.
redact@gmktec:~$
```

---

### Post by grahammechanical on 2024-11-25
@tea for one

That is an interesting experiment. I am forced to go back in time to when I had a BIOS motherboard and a SATA (sda) drive that had an MBR partition table. I then fitted a second SATA drive with GPT partition table. What command did I use to install Grub? I have checked my ancient idiot's sheet and it was either /dev/sda or /dev/sdb depending on which install of Ubuntu on which drive I wanted to be in charge of the Grub menu.

It seems that the Grub developers are smart to code Grub so that it installs in the appropriate partition. Of course for a MBR drive the Grub files go into the Master Boot Record and not a partition. And then on a GPT drive in a BIOS motherboard Grub goes into the first partition which is the Bios Boot partition. With a UEFI motherboard the Grub files go into the first partition - EFI System partition.

Regards

---

