---
title: "Unable to install Ubuntu on HP Envy desktop alongside Win 11"
date: 2022-01-16
forum: Installation &amp; Upgrades
---

### Post by jloveless on 2022-01-16
I have a new HP Envy desktop It has 2 1TB SSD drives and a spinning data drive. The second 1TB drive was formatted with a 300GB Fat32 partition and a 930GB Ext4 partition. I burned an Ubuntu 21.10 USB using Rufus. I booted from the USB drive and I got the normal install option menu. If I select any of the options a get a scrolling screenful of system instructions and then it stops cold.I need to power off to get back to work. I have tried this as many different ways as I can think off - all with the same results. I called HP support but they refuse to even talk about a Linux install on one of their PCs. I tried copying the ISO file data to the Fat32 partition on the SSD and then booting from that to install but I get the same scrolling list of install instructions and then a lock up. So, I am beginning to think that HP has put some code in their boot process to look for an attempt to install linux/Ubuntu, and then stopping the install. 
Does anyone have a solution? I even tried installing Ubuntu on the drive from my Ubuntu laptop and then moving the drive back to the HP Envy. No love there either. I would love some help and a solution if there is one.
Many thanks.
Jon Loveless

---

### Post by tea for one on 2022-01-16
Did you boot the Ubuntu installer in UEFI mode?
Instead of going straight to installation, did you use a live session via [COLOR="#0000FF"]Try Ubuntu[/COLOR] first?

It looks like you want to install Ubuntu on the [COLOR="#000080"]second 1TB drive was formatted with a 300GB Fat32 partition and a 930GB Ext4 partition[/COLOR]?

De-activate, isolate or physically remove the Windows 11 drive and then try again?

---

### Post by jloveless on 2022-01-16
Yes to UEFI.  The "try first" option was not an option for some reason, so no, didn't try that. Yes to the drive where I want to install. I will try removing the Win drive.

---

### Post by tea for one on 2022-01-16
How did you format your second drive to Ext4 if you had difficulty with the live session?

---

### Post by jloveless on 2022-01-16
I removed the drive. Connected it to my laptop with a USB to Sata cable. Formatted to ext4. Put the drive back in my desktop.

---

### Post by tea for one on 2022-01-16
I see, another device at your disposal.

Did you choose GPT for the partition table?

---

### Post by jloveless on 2022-01-16
Yes. G p t

---

### Post by MAFoElffen on 2022-01-17
One comment about HP Tech Support. Remind them that they do sell HP models pre-installed with Ubuntu Linux. Their company indirectly supports Ubuntu 'as much' as they do Microsoft Windows. That in their "support tier" they support the HP Hardware, and that they refer their Users to others to support the OS'es they sell pre-installed on their hardware. If it was a Windows question, they would refer you to Microsoft... Just saying. Of many things, I am a certified HP Warranty Tech. I have dealt with that.

Un fortunatley, their training and scripts is to refer Users to links for HP Documentation on installing Ubuntu from their OEM media, and/or back to ubuntu.com... [https://support.hp.com/gb-en/document/c00269588](https://support.hp.com/gb-en/document/c00269588) 

Next. many of their Windows machines come with the SATA mode set to "RAID" instead of "AHCI". When in that mode, if Windows was originally installed in that mode, it will not want to boot, if you change the UEFI BIOS out of that mode to AHCI mode. Even though the HP Support Doc's say that their SATA "RAID" mode includes AHCI, I doubt that very highly...

I know that most of the time, a Linux Install will not see the drive oin a Dell, Lenovo or HP machine, it you have the SATA mode set to thier "RAID" modes... So if I was called to replace a drive, I installed the new drives in "AHCI" mode (unless they had OPTANE), to be compliant with the world, instead of just with Microsoft. When the OS was reinstalled, it worked great,

Most of the hardware recommends I have seen recommend that AHCI optimizes performance on SSD's and NVme. Intel says that RAID mode includes AHCI mode, but doesn't mention that OS'es installed in that mode have problems booting in pure AHCI, or might have problems seeing the drives at all... Even some of Dell's warranty replacement drives have problems being recognized in SATA "RAID" mode...

If you have to install Linux in AHCI mode, and Windows 11 doesn't want to boot, there are two options. The first is to change a certain registry setting in Windows that will change/allow it.Then it boots fine. The second option is to re-install Windows 11 in SATA AHCI Mode.

If you are  Windows 11 User right now... And you want to continue using that, get familiar with backups and reinstall's. I had one User, that, while still on warranty, by the time of my onsite warranty service call, had reinstalled Windows 11 five times already... He had it down to an art. It was because Windows updates hosed the OS. They might have worked those out by now... But just be prepared and have a good backup to fall back to.

...And there is no better tool for recovering data and helping to recover "Windows" than Linux... If you do a few things,that are common recommends here. #1 being- Turn the power settings characteristics of Windows to not do FastBoot... Shut down the filesystem, instead of hibernation (which leaves the filesystem open, and then is unrecoverable after a crash.).

Sorry. I see many of these posts, and I have to say something to save you head aches in the long run.

---

### Post by oldfred on 2022-01-18
Which model HP Envy?
We see many users with issues installing to HPs, but they usually can install, just need some settings & perhaps a work around or two.
Also installing Ubuntu to any drive other than first drive also is an issue. Multiple work arounds, often easiest is to only have Ubuntu drive in system. But some UEFI let you turn off or disable a drive in UEFI drive settings. Or temporarily remove boot flag from Windows drive's ESP.
Ubuntu's Ubiquity installer always wants to install grub to first drive's ESP. And UEFI defines first drive. Very old bug.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Also many systems need UEFI update and if SSD, SSD firmware update, even if new system.

And for whatever reason HP's UEFI does not recognize boot order changes made with efibootmgr. When system or grub is installed, it uses efibootmgr to set boot order. Every other brand or motherboard vendor seems to work, although Acer requires added trust settings.
Users then can only change boot order in UEFI settings f10, not UEFI boot menu F9. 
HP - escape + F9 for UEFI boot menu, F10 for UEFI/bios setup

Note that Windows updates typically make Windows first in boot order & turn fast start up back on. So if issues later, you have to redo those settings.
And sometimes an UEFI update resets some of the UEFI settings. My old Asus motherboard has multiple settings I need and after UEFI update I have to redo them. I have to keep a list.

---

