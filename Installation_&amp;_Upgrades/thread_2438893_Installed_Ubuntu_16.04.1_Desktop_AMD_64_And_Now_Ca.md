---
title: "Installed Ubuntu 16.04.1 Desktop AMD 64 And Now Can't Boot To Hard Drive"
date: 2020-03-19
forum: Installation &amp; Upgrades
---

### Post by racerxsixtynine on 2020-03-19
I have a brand new motherboard, ASUS Prime Z370-AII, Intel Core i5-8400 CPU @ 2.80GHz x 6 core, 64gigs of RAM, and a 1 terabyte hard disc. I run the installation from a DVD, and when it says it has successfully installed it needs to reboot. So I reboot the machine, and it wants me to remove the installation disc and hit any key to reboot.

Hitting any key does nothing, hitting enter causes a cursor to return down the left side of the screen. So I remove the disc and hard boot the machine. When it reboots it says:

Reboot and Select proper Boot Device
or Insert Boot Media in selected Boot Device and press a key_

If I reboot and enter the BIOS, without the install DVD in the drive, I can see the hard drive listed in the BIOS but not available as a bootable drive option.


I restart the machine again, and enter the UEFI BIOS, and the only boot options are:

SATA6G_2: ASUS  DRW-24B1ST

UEFI: ASUS DRW-24B1ST j(1443MB)

I select one for first and the other for second.

I restart the machine again, and am presented with the choice to try Ubuntu without installing, Install Ubuntu, OEM Install and Check the disc. If I select the first choice Ubuntu runs from the installation disc. I can see the hard drive with the recently installed operating system, but cannot find any options to select it as a bootable drive so I can reboot the machine and boot to the hard drive.

If I select the second choice, I am cautioned that there is already an operating system installed, and do I want to overwrite it, or install alongside it in another partition. Choosing the overwrite option tales me down a never ending circle of install, over and over again. Choosing the second doesn't make any sense, as ultimately I will run out of room to install parallel operating systems.

I'm not an OEM, so the third choice is a non starter.

The check disc option ended when after several hours of it running I pressed the power button until the machine shut down and went to bed.

This is frustrating.

No, this is maddening.


I tried searching this problem and all I find are people who have tried installing Ubuntu alongside of Windows 10 (yuck!) or in top of it. I have not done either of these things, as I refuse to move from Windows 7 Pro on my other computers. 

Can someone here please help me figure this out?

Thanks in advance,
Racer

---

### Post by CatKiller on 2020-03-19
Your UEFI settings are the likely culprit.

Two likely candidates are the boot mode of your install media, or your drive settings.

If your machine is set to boot in UEFI mode rather than Legacy/CSM/BIOS mode (which is likely, since it's new) but your install media was set to boot in BIOS mode (you would get a choice with new USB drives, but not old crappy ones; I have no idea about your optical drive) then Ubuntu will install in BIOS mode, which then won't boot since your machine is booting in UEFI mode.

I think the second is more likely; many manufacturers default to having the drives set as RAID since Windows prefers that. Ubuntu needs the drives to be AHCI.

---

### Post by Impavidus on 2020-03-20
I wouldn't install 16.04.1 on brand new hardware. It has a kernel that's 4 years old. Better try 18.04.4 or 19.10, which come with a kernel only 6 months old.

The check disk option shouldn't take that long, just long enough to read all package files on the live disk. You may have a bad live disk.

Most new hardware (less than ~12 years old) can boot from usb, which is more convenient than dvd.

---

### Post by ajgreeny on 2020-03-20
How did you create the DVD installation disk?
It is, as impavidus said, far easier and quicker to use a USB flash drive and the disk check should take about 2 - 3 minutes only, so I also think your DVD must be faulty.

---

### Post by racerxsixtynine on 2020-03-20
> **ajgreeny said:**
> How did you create the DVD installation disk?

I downloaded the iso, then burned it in Windows.

---

### Post by racerxsixtynine on 2020-03-20
> **CatKiller said:**
>  Ubuntu needs the drives to be AHCI.

So you are saying I should set the drive properties to AHCI in the BIOS then?

---

### Post by racerxsixtynine on 2020-03-20
> **CatKiller said:**
> Your UEFI settings are the likely culprit.

Two likely candidates are the boot mode of your install media, or your drive settings.

If your machine is set to boot in UEFI mode rather than Legacy/CSM/BIOS mode (which is likely, since it's new) but your install media was set to boot in BIOS mode (you would get a choice with new USB drives, but not old crappy ones; I have no idea about your optical drive) then Ubuntu will install in BIOS mode, which then won't boot since your machine is booting in UEFI mode.

I think the second is more likely; many manufacturers default to having the drives set as RAID since Windows prefers that. Ubuntu needs the drives to be AHCI.

So just now I tried to install Ubuntu from the try Ubuntu desktop that runs from the install disc, using  the button on the sidebar. As it progressed this is the message I get:

"This  machine's firmware has started the installer in UEFI mode but it looks  like there may be existing operating systems already installed using  "BIOS compatibility mode". If you continue to install Debian in UEFI  mode, it might be difficult to reboot the machine into any BIOS-mode  operating systems later."

Is this what you are talking about?

---

### Post by CatKiller on 2020-03-20
> **racerxsixtynine said:**
> So you are saying I should set the drive properties to AHCI in the BIOS then?

Yes. 

> **racerxsixtynine said:**
> Is this what you are talking about?

Yes.

---

### Post by racerxsixtynine on 2020-03-20
> **CatKiller said:**
> Yes. 



Yes.


Well thank you. I'll make the change and see how it goes.

Cover me, I'm going in . . . . . .

---

### Post by racerxsixtynine on 2020-03-20
By the way, this machine also has four 4 terabyte drives in it that I plan to use as a RAID array, for backup of my photos and music. Is it a realistic expectation that I can set up the RAID and manage it with the Ubuntu OS?

---

### Post by CatKiller on 2020-03-20
I think that setting is for booting from Optane (which I don't think Linux supports, although it's not something I've looked into, particularly), rather than RAID proper. My understanding is that RAID works fine, and that mdadm is the preferred method. Again, not something that I've played with: I have a NAS but the Synology software takes care of everything without me needing to know the specifics.

---

### Post by racerxsixtynine on 2020-03-20
> **CatKiller said:**
> Ubuntu needs the drives to be AHCI.

> **racerxsixtynine said:**
> So you are saying I should set the drive properties to AHCI in the BIOS then?

> **CatKiller said:**
> Yes. 


> **racerxsixtynine said:**
> Well thank you. I'll make the change and see how it goes.

Cover me, I'm going in . . . . . .

Well that seems to have fixed it. I have booted to the hard drive and shut down successfully several times now.

Thank you for the help!

---

### Post by racerxsixtynine on 2020-03-21
> **Impavidus said:**
> I wouldn't install 16.04.1 on brand new hardware. It has a kernel that's 4 years old. Better try 18.04.4 or 19.10, which come with a kernel only 6 months old.

By the way, after successfully getting Ubuntu to boot from the hard drive, it prompted me to update to 19.10. I went ahead and did that, via the network connection, and all seems OK so far . . . .

Again, thanks to all for the help!

Racer

---

### Post by ajgreeny on 2020-03-22
Great  news.
Please mark as SOLVED from Thread Tools at the to as it's a great help for those searching the forum.

---

### Post by racerxsixtynine on 2020-03-22
> **ajgreeny said:**
> Please mark as SOLVED from Thread Tools at the to as it's a great help for those searching the forum.

Um, I did, thank you.

Yesterday.


[img]https://live.staticflickr.com/65535/49686932152_25e1533c2d_o.jpg[/img]


[img]https://live.staticflickr.com/65535/49686631091_e9fae76013_o.jpg[/img]

Am I missing something?

---

