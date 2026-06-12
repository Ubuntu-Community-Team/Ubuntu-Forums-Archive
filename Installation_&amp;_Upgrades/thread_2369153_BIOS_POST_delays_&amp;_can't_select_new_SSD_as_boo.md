---
title: "BIOS POST delays &amp; can't select new SSD as bootable"
date: 2017-08-19
forum: Installation &amp; Upgrades
---

### Post by paulrb on 2017-08-19
Hi everyone,

First of all I should say that this issue may turn out to be nothing whatsoever to do with Ubuntu and everything to do with my motherboard/BIOS. So why post the question here? Well, you know how it is. If you post anywhere else, everyone will assume you are a Windows user and start giving suggestions on that basis. As soon as they find out you are not a Windows user, they assume the problem is Linux related and they know nothing about that.

Currently my self-built (a few years ago) desktop PC is running Ubuntu 14.04. Motherboard is an Asus M4A785TD-M, processor AMD Phenom II X4 905e. Drives: 80GB 2.5" Intel SSD (boot), 250GB 2.5" WD 7200rpm, 5.25" DVD-RW, all attached via SATA. The 80GB SSD is partitioned 40GB for Windows7 (bootable), 40GB for Ubuntu.

What I am trying to do is replace the 80GB SSD with a Samsung 120GB SSD. This will allow me an extra 40GB for Ubuntu.

This is the process I followed:

Attached the new 120GB SSD externally via a USB adaptor (one of those "Drive Dock" things). Booted the PC using the Ubuntu live CD. Copied contents of the 80GB drive to the external 120GB drive using "dd" command. This took many hours over the USB 2.0 adaptor, but appears to have worked perfectly. I then used gparted to extend the Ubuntu partition to use up the extra space.

Next, I opened up the PC and disconnected the 80GB SSD drive, set the BIOS to boot from the external USB device, then rebooted. The PC booted fine (a little slow, obviously) from the externally connected drive. Everything seemed perfect at this point.

Then I removed the 120GB drive from the external USB and connected it directly to the M/B with SATA cable (the old 80GB SSD still disconnected). Rebooted, but during the POST, there was a 20-30s delay during which time the HDD light glowed dimly. The POST messages showed that it had detected two hard disks and the DVD drive, but after the unexpected delay, then went on to list only the 7200rpm drive and the DVD drive. Then the message "3rd Master hard Disk Error, Press F1 to Resume". When you press F1, it enters the BIOS menu.

In the BIOS menus, I can see that the 120GB Samsung SSD has been detected. All its details appear correct. However, when I go to the Boot settings menu, I can't select the new SSD as a boot device in any of the screens.

I then replaced the old 80GB SSD and updated the BIOS to the last available version from ASUS's support pages. (So easy these days! Just dump the un-zipped BIOS file into the Windows partition of the drive, restart, enter the BIOS menu, go to the Update/Flash BIOS page, locate & select the file from the SSD. All done in a minute. Remember the days of having do dig out an old 3.5" floppy drive just to update the BIOS?) Unfortunately, the updated BIOS behaves just the same when the new 120GB SSD is attached via SATA.

So, to summarise, I can boot from the new SSD if attached as an external USB drive, but not when attached via internal SATA cable.

Can anyone please suggest any other tests or solutions please?

Will try to attach some pics in the next post.

Thanks in advance,

Paul

---

### Post by paulrb on 2017-08-19
[ATTACH=CONFIG]276443[/ATTACH][ATTACH=CONFIG]276444[/ATTACH][ATTACH=CONFIG]276445[/ATTACH][ATTACH=CONFIG]276446[/ATTACH][ATTACH=CONFIG]276447[/ATTACH]

---

### Post by oldfred on 2017-08-20
If BIOS will not correctly show drive, then operating system will not see it.

Also best to have drives in SATA port order and not have DVD in middle. Some times booting my second drive I have issues when I had DVD between drives. The grub definition can change.

Since using dd to image drive, you can only have one connected at a time.
You have same UUID in both drive, so system will not work with duplicate UUIDs.

Screen shot #2 says detecting drive, but it does not show details like it does for DVD & other HDD.

---

### Post by paulrb on 2017-08-28
Thanks for replying, @oldfred

To clarify, the BIOS does show the drive (screenshot #4). But it won't let me select it to boot from. The operating system will happily boot from the drive if it is connected via an external usb adaptor.

Thanks for the tip about order of SATA ports. I will try that. However, I have had the drives in that order for years without any issue (SATA1: SSD; SATA2: DVD; SATA3: HDD). I am attempting to replace the SSD with a higher capacity one. 

I am not connecting the old and new SSDs at the same time, so the UUID conflict should not be an issue. I was concerned that the BIOS had a record of the UUID in its CMOS memory, so I cleared that, but it made no difference. Well, I say I cleared the CMOS, but the motherboard jumper is labelled CLRTC, which the quick-start guide describes as "Clear RTC", so maybe it only clears the date/time.

I also noticed that the POST screen does not give the full details of the SSD as it does for the DVD and HDD. And yet it shows the details in full in the BIOS screen (screenshot #4). I don't know what this means.

How can I give the new SSD a new UUID? Does this happen during partitioning or formatting?

Any idea what "3rd Master Hard Disk Error" means?

What I might try next is delete all partition on the new SSD, re-partition, re-format and re-install Ubuntu.

If the BIOS will still not allow me to select the drive as the boot drive, I may try the new SSD in a different PC. If that works, that will lead me to assume there is some incompatibility between my motherboard/BIOS and this new SSD.

---

### Post by ubfan1 on 2017-08-28
The usual hardware, with plugins for four SATA disks was split into two pairs, only one of each pair could be a "Master".  This was determined by a jumper on the back of the disk.  Sometimes, the SATA cable had the capability to select Master (first position?).  If you disks have jumpers, check the docs for what settings are for the Master, and change one if there are 3 Masters.

---

### Post by oldfred on 2017-08-28
Some older motherboard may still use the IDE/PATA nomenclature. SATA drives should not matter.
But make sure BIOS is set for AHCI, not IDE nor RAID.

My systems started at SATA0. And when I have DVD in between drives, and add a flash drive flash drive is seen as hd1 and second drive as hd2 (first is hd0). The flash drive takes the place of the DVD in SATA port order.

Many have had to update BIOS and firmware on SSD to get them to fully work.

---

