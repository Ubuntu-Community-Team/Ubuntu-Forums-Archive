---
title: "How to restore Windows boot loader and remove grub"
date: 2020-11-14
forum: Installation &amp; Upgrades
---

### Post by cspadijer2 on 2020-11-14
Hi,
I have a laptop with Windows 10 on it (Windows 10 is encrypted).
I boot from a USB key when I want to boot Ubuntu.
Just installed Ubuntu 20.10 on USB key and made sure everything to do with grub and Ubuntu was specific to USB key.
Have followed same method many times without issue with previous versions of Ubuntu.. and the boot loader and Windows 10 was not affected on main drive.
Not this time however.  For some reason it tried to install Grub on main drive instead of USB key only.

Windows 10 wont boot now as stand alone drive or from grub menu on USB Key.

I know I know... I should have taken laptop apart and removed internal drive before installing Ubuntu on USB key.

I installed boot-repair and captured boot info here:
[https://paste.ubuntu.com/p/cVy8PMcXBp/](https://paste.ubuntu.com/p/cVy8PMcXBp/)

Hoping I can recover MBR so Windows 10 boots fine again.

Any help appreciated.

---

### Post by oldfred on 2020-11-14
You want grub in MBR of external drive and Windows boot loader in MBR of internal drive.
You needed to use Something Else install option which on partitioning screen allows you to select where to install grub2 boot loader, or install to sdb (not a partition).

It looks like Boot-Repair will reinstall grub to sdb, your external.
Not sure if it is installing syslinux boot loader to sda or not as that is a Windows type boot loader. You may need Boot-Repair's advanced mode or your Windows repair disk.

Grub only boots working Windows or Windows that is not hibernated. And Windows fast start up turns on hibernation flag preventing grub from booting it.
And Windows updates turn fast start up back on.

And with most of grub in external drive, trying to boot without it connected and grub in MBR of internal drive will just give grub error.

---

### Post by cspadijer2 on 2020-11-15
Thanks oldfred.
I did do the "Something else" install option and made sure that grub was to install on the external drive.

I removed the internal drive as a test and reinstalled ubuntu 20.10 to the external drive (its a new external 256 GB SSD USB 3.1 drive).  Grub fails to install to it (when the external is the only drive available).
So I think what happened is it tried to put grub 2.0 on external, failed, and then decided to try on the internal drive (something I wish it didn't try to do).

I am going to analyze the internal drive again.  I think it created a 1 MB partition at the beginning.  The Windows partition "appears" intact based on Boot-repair logs.

My old external USB drive I booted up and still shows Windows 10 in boot menu.  If I select it, it tries to boot Windows but then there are errors it cant find Windows boot files.

---

### Post by oldfred on 2020-11-15
Windows has its boot partition on sda1.
Note that sda & sdb may switch. When I plug in my USB drives that were sdc or sdd, on reboot become sda and every other drive changes one letter. I have to pay attention to device assignment. 

I prefer gpt(GUID) partitioning, but Windows in BIOS boot mode has to have the 40 year old MBR(msdos) partitioning.
I started using gpt with my Ubuntu only drives in 2010 and now all drives are gpt.
But gpt requires bios_grub partition for BIOS boot or ESP - efi system partition for UEFI. 
When UEFI started to become the new standard in 2012, I started putting both the bios_grub for my current system but also added the ESP, so I could easily move drive to newer system. Only one or the other was actually used, but gave me flexibility to convert boot mode without having to totally redo drive.

Often SSD need firmware update, but  not sure if you can do that to external drive. I updated my external SSD when it was still an internal drive.

---

### Post by cspadijer2 on 2020-11-15
So I ran the boot-repair from a ubuntu running from the USB key and it had me uninstall and reinstall Grub 2.0.
This did not solve the main drive damage though.
SDA1 - is a NTFS 500 MB drive (set to Boot) that the encryption software used to mount Windows on SDA2
SDA2 - is an encrypted 465 GB drive (Gparted shows it as "unknown" filesystem... its really NTFS encrypted)

I am downloading a WinPE ISO right now and plan to try using it to put  back Windows MBR... however since Windows is encrypted by 3rd party  software I don't think I will have much luck.
I think Gparted overwrote what the drive encryption software used to mount the encrypted drive.

---

### Post by oldfred on 2020-11-15
If it creates a proprietary MBR, and not just encryption in the boot partition, then the encryption vendor should have a way to recover it.

If gparted cannot see the format of a partition either because its encrypted, unformatted, or hibernated, then it shows as an error or unknown.
Some partitions are required to be unformatted like Microsoft reserved or bios_grub and those show as errors in gparted, but are correct.

---

### Post by cspadijer2 on 2020-11-22
Thanks again oldfred.

I reinstalled Windows with a newer version. New version wouldn't install properly with system in CSM (Legacy) mode so switched to UEFI and it installed fine.
Only issue with this is I then needed a Ubuntu USB UEFI boot media to install Ubuntu 20.10 on my new SSD USB 3.1 USB key.
Had to change a parameter that permits USB Legacy media (the description says its for Floppy disks and other older formats).
Eventually got it working and both are Windows and Ubuntu 20.10 now running in UEFI mode.

I had to use Rufus (a Windows utility) to create the Ubuntu 20.10 UEFI boot media.  I tried a bunch of Linux utilities but they didn't work.
Question: Do you know of any good Linux based UEFI boot media creator that allows you to select GPT and UEFI mode when creating a new Ubuntu install USB?

---

### Post by tea for one on 2020-11-22
> Question: Do you know of any good Linux based UEFI boot media creator that allows you to select GPT and UEFI mode when creating a new Ubuntu install USB? 

One of the best utilities for creating bootable usb devices is [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

However, as far as I know, there isn't **one** application to create UEFI, GPT and Bootable USB in one operation.

For a UEFI install - you have to boot in UEFI mode (i.e. turn off Legacy in your UEFI set up)
Or select UEFI bootable device in your boot menu
You can always double-check that you have booted in UEFI mode via a terminal

```
[ -d /sys/firmware/efi ] && echo "Installed in UEFI mode" || echo "Installed in Legacy mode"

```
For GPT - use gparted - Device > Create Partition Table > Select gpt

---

### Post by oldfred on 2020-11-22
It is my understanding that Rufus lets you choose which way to create USB flash drive. But then it only boots in that one mode.
It calls it UEFI/gpt or CSM/MBR where 
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

Ubuntu live installer is set for both UEFI or BIOS/Legacy/CSM boot modes, but you have to choose which to use in UEFI one time boot menu. 
It should have two entries for USB flash drive one UEFI:xxxx and one just xxxx where xxxx is name or label of flash drive.

---

