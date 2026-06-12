---
title: "Unable to boot Ubuntu server from USB HDD. &quot;Non-system disk or disk error&quot;"
date: 2022-06-13
forum: Installation &amp; Upgrades
---

### Post by gabi16062 on 2022-06-13
I started this thread at Ask Ubuntu, but I had no luck, so here are the details so far:
I tried installing Ubuntu Server to a USB drive, because I want to use all four internal HDDs (that's the maximum) as part of a RAID5 array. This is a home server, so buying an expensive hardware RAID controller is not an option.
Here's what I tried so far:
 - a 320 GB Samsung S2 Portable external HDD,
 - a 500 GB Seagate drive in latter one a cheap enclosure
 - a 32 GB Sony USB drive
 - 18.04.6
 - 20.04.4
 - 22.04
 - verifying the ISOs before creating the bootable drive

But the result was always the same.

The OS installation was successful (no error messages), but I got a "Non-system disk or disk error" each time. I did a test in VirtualBox, but got to the same the results.

I was able to boot from each drive with each release as a RAW disk, but not as USB (using Plop Boot Manager 5.0.15 in VirtualBox.

Edit: the PC I'm trying to install Ubuntu on does not support UEFI, although I don't see it as a requirement. I also tried 22.04 Desktop, but got the same result.

Edit 2: For testing purposes, I downloaded and installed Deepin 20.5. There were no issues during its setup. It booted from the external HDD on first try.

Edit 3:

 1. I'm trying to install it on an HP Compaq dc5850 mini tower. I
    installed 18.04 on it before - to an internal HDD.
 2. Here's the [(https://pastebin.com/raw/vmcKVaHH)"]list]("http://[https://pastebin.com/raw/vmcKVaHH) of ISOs I tried (with their calculated checksums).
 3. I used Rufus to create the installer USB,
    but I managed to reproduce the issue in VMware Workstation Player and VirtualBox, so I'd rule that out. Also, there were no errors during the installation.
 4. After the first unsuccessful attempt, I disconnected all other
    disks that were not the installer or the target.

Edit 4:
 1. When using focal-legacy-server-amd64.iso, the installer hung after selecting/detecting the keyboard layout. I checked the ISO's checksums and they didn't match, so I re downloaded it and made sure it's not corrupted by comparing the SHA256 and MD5 sums. This time they matched.
 2. Using the mini ISO, I reproduced the original issue. It installed without any errors, I made sure to choose to write GRUB to sda's (the only drive that's not the installer) MBR, but it didn't boot. The system boots in VMware Workstation Player using RAW disk access, but not when used via USB.

Edit 5:
22.04 does not boot even from the internal HDD.

---

### Post by sudodus on 2022-06-13
I could not help you via our conversation at AskUbuntu. I am not sure that I have understood your problem. So in order to make things clear for me and *others* who can help you, please answer the following questions, even though you might find them stupid:

**Can you boot this computer from *any* live Ubuntu system at all?** In that case, which live system or systems?

I mean, that at this stage you don't create an installed system in a USB drive, but 'only' boot a live system, new (22.04 LTS) or old (for example 18.04 LTS) from the USB drive, prepared by Rufus with input from an iso file? Can you boot any Rufus-made USB drive?

Knowing which Ubuntu live system(s) can boot (or none) will give us a starting point from where we can help you. Depending on your answer, people will suggest things to try ...

---

### Post by gabi16062 on 2022-06-13
So far, I managed to boot the following ISOs:
deepin-desktop-community-20.5-amd64.iso
focal-legacy-server-amd64.iso
linux-lite-5.6-64bit.iso
lubuntu-22.04-desktop-amd64.iso
mini.iso
ubuntu-18.04.6-live-server-amd64.iso
ubuntu-20.04.4-live-server-amd64.iso
ubuntu-22.04-live-server-amd64.iso
MX-21.1_386.iso

From these, I was able to install and boot the following:
Ubuntu 18.04 (back in 2018/19, from internal HDD)
Linux Lite (December 2021, from internal HDD | Debian/Ubuntu-based)
MX Linux (December 2021, from internal HDD | Debian/AntiX-based)
deepin 20.5 (May 2022, from USB | Debian-based)

All of these were made with Rufus' default settings. Checking the "Add fixes for old BIOS-es" option makes no difference.
When I connect the HDD internally instead of via the enclosure, I get into grub rescue prompt ( Error: Disk 'hd0' not found..

---

### Post by sudodus on 2022-06-13
Thanks for this list. It makes me think we will solve the problem for you :-)

The first thing I will suggest is boot the computer/operating system (Windows) where you have Rufus

A 'daily' Jammy (22.04) preinstalled server is available for PC computers (**amd64** architecture). You can find it in the following directory

[cdimage.ubuntu.com/ubuntu-server/jammy/daily-preinstalled/current/](http://cdimage.ubuntu.com/ubuntu-server/jammy/daily-preinstalled/current/)

where there is also a SHASUM for it. Please let Rufus check it.

It is easy to install to an external drive directly with Rufus by extraction to the drive. No conventional linux install program will be involved.

It grabs the whole drive (there is no 'install alongside'), which should be OK for your external drive.

Let Windows flush the buffers 'unplug safely', move the external drive to your server computer and try to boot from it. This compressed image is made so that it should boot most PC (amd64) computers both in UEFI mode and BIOS mode (alias CSM alias legacy mode).

I think you have a fair chance to succeed. Otherwise we can listen to good advice and try something else ...

Edit: I think the screenshot can be useful even if the texts are in Swedish. For example, you must select 'Advanced ...' in order to be able to extract to an SSD or HDD (not only simple USB pendrives); The tick symbol in a circle activates the checksum tool; The format settings at the lower part of the Rufus window are not relevant in this case, Rufus will simply extract the compressed image.

---

### Post by gabi16062 on 2022-06-13
In the meantime, I've messed around with Super GRUB 2 Disk and Deepin.
This is what Super GRUB 2 Disk found:
[IMG]https://pic8.co/sh/bUiEHK.jpg[/IMG]

This gave me the idea to run a GRUB update and to install GRUB manually to the MBR of Ubuntu's disk. The grub-install /dev/sda command reported no issues.
[IMG]https://pic8.co/sh/Dvrtkc.jpg[/IMG]

This is Ubuntu's GRUB entry in Deepin's GRUB in the editor:
[IMG]https://pic8.co/sh/0rag3G.jpg[/IMG]

and this happens when I try to boot from it (sorry about the blurry photo):
[IMG]https://pic8.co/sh/oIYFhO.jpg[/IMG]

Finally, this is the message I get when trying to boot from Ubuntu's HDD:
[IMG]https://pic8.co/sh/RJOUYH.jpg[/IMG]

---

### Post by gabi16062 on 2022-06-13
> **sudodus said:**
> Thanks for this list. It makes me think we will solve the problem for you :-)

The first thing I will suggest is boot the computer/operating system (Windows) where you have Rufus

A 'daily' Jammy (22.04) preinstalled server is available for PC computers (**amd64** architecture). You can find it in the following directory

[cdimage.ubuntu.com/ubuntu-server/jammy/daily-preinstalled/current/]("http://cdimage.ubuntu.com/ubuntu-server/jammy/daily-preinstalled/current/")

where there is also a SHASUM for it. Please let Rufus check it.

It is easy to install to an external drive directly with Rufus by extraction to the drive. No conventional linux install program will be involved.

It grabs the whole drive (there is no 'install alongside'), which should be OK for your external drive.

Let Windows flush the buffers 'unplug safely', move the external drive to your server computer and try to boot from it. This compressed image is made so that it should boot most PC (amd64) computers both in UEFI mode and BIOS mode (alias CSM alias legacy mode).

I think you have a fair chance to succeed. Otherwise we can listen to good advice and try something else ...

Edit: I think the screenshot can be useful even if the texts are in Swedish. For example, you must select 'Advanced ...' in order to be able to extract to an SSD or HDD (not only simple USB pendrives); The tick symbol in a circle activates the checksum tool; The format settings at the lower part of the Rufus window are not relevant in this case, Rufus will simply extract the compressed image.

Image downloaded, verified, written to disk and tested in VMware Workstation 16 Player. All working fine. When connected to the PC via USB, it didn't work, but it did when I connected the HDD directly.
I checked the cable, even though Deepin has no problem with it, but it didn't help. Then I swapped enclosures and put the drive into a the natec branded one, that uses the ASMT 2115 controller, instead of the LC Power's generic ASMedia USB 3.0. It didn't work either. 

Edit: Until a solution is found, I'm going to "decrapify" Deepin and install the services I need. It'll be a good temporary fix.

---

### Post by oldfred on 2022-06-13
I have a SATA to USB adapter.
It worked great for an old SSD, but would not work at all for an old HDD. It used USB power which was not enough to spin up HDD.
Is your external USB, USB powered or does it have a separate power connection?

---

### Post by gabi16062 on 2022-06-13
> **oldfred said:**
> I have a SATA to USB adapter.
It worked great for an old SSD, but would not work at all for an old HDD. It used USB power which was not enough to spin up HDD.
Is your external USB, USB powered or does it have a separate power connection?

It's USB powered, but I've been using that HDD and adapter for a while now, without any issues.
But, to answer your question, it is USB powered, but the drive spins up and works reliably in it.
I'd also rule it out because it didn't work with my Samsung S2 Portable either, which is a factory-made USB Hard Drive.
[IMG]https://pic8.co/sh/sEgyt0.jpeg[/IMG]

Mine has a bit more scratches, but still works reliably even today.

---

### Post by sudodus on 2022-06-13
One way to provide more power to the USB system is to **connect the USB drive via a USB hub, that has an external power supply**. It has made some equipment work better or at all for me.

---

### Post by gabi16062 on 2022-06-13
> **sudodus said:**
> One way to provide more power to the USB system is to **connect the USB drive via a USB hub, that has an external power supply**. It has made some equipment work better or at all for me.

I have a USB hub that has a micro USB port for that. I'll check it out on Saturday or Sunday, because I'm working in the next four days the shift + the travel back and forth take up most of my day.

---

### Post by yancek on 2022-06-14
The 3rd image you posted shows Ubuntu on (hd0,gpt3).  Since you are doing a Legacy/CSM install, have you created a 1MB unformatted bios_grub partition on the drive?  This is needed for a Legacy install on a gpt drive.

The 4th (blurry) image shows no such device and is referring to the partition UUID you can see which begins with "25dcead8..".  Run blkid and see if you have that UUID.  Probably not so you need to change it to whatever the UUID is for the 3rd partition on that device.  Do this in grub.cfg and /etc/fstab on the Ubuntu drive after mounting from another OS or live usb..

---

### Post by gabi16062 on 2022-06-17
> **yancek said:**
> The 3rd image you posted shows Ubuntu on (hd0,gpt3).  Since you are doing a Legacy/CSM install, have you created a 1MB unformatted bios_grub partition on the drive?  This is needed for a Legacy install on a gpt drive.

The 4th (blurry) image shows no such device and is referring to the partition UUID you can see which begins with "25dcead8..".  Run blkid and see if you have that UUID.  Probably not so you need to change it to whatever the UUID is for the 3rd partition on that device.  Do this in grub.cfg and /etc/fstab on the Ubuntu drive after mounting from another OS or live usb..
I will be off work this weekend, so I'll have time to experiment.

As for now, I quickly eliminated the external HDD's power issue. The system image that boots when the drive is internally connected, but not via USB refuses to boot from my 32 GB Sony USB flash drive. The indicator LED is blinking rapidly for 2-3 seconds during the boot attempt, then fails with the same "Non-system disk or disk error" message. I even used Rufus' fix for older BIOS-es.
To verify that the system DOES boot, I used VMware Workstation Player and Plop Boot Manager to boot into the OS on the USB drive in a VM. It was not fast, but it did boot BIOS mode.
I will "sacrifice" another USB drive to see if I can replicate this behavior on the real hardware.

Edit:
I didn't have much time to work on this today, but I did the experiment and the results are the same.
1. Ubuntu does not boot from the USB attached HDD.
2. Ubuntu does boot from the same HDD when attached internally (via SATA).
3. Deepin boots from the same USB attached HDD consistently.
4. Ubuntu does boot consistently from USB if launched from Plop Boot Manager.
5. Super GRUB2 Disk does not find any bootloaders on the Ubuntu image's drive.
If we can't find a solution, I'll configure Plop to automatically boot from USB and put it on a floppy (because I still have a floppy drive and a floppy that still works).

---

