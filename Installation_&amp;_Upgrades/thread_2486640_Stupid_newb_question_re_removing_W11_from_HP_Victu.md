---
title: "Stupid newb question re removing W11 from HP Victus"
date: 2023-05-07
forum: Installation &amp; Upgrades
---

### Post by nowindows2 on 2023-05-07
First, thanks to all who donate their time on this forum.

Short version:
Can I completely remove Windows 11 from an HP Victus and install Ubuntu? No dual boot - just Ubuntu alone. No gaming, no downloads, no surfing, no movies, no wifi. I just need to access the Internet.  Thanks!

Long version: 
I'm a Linux newb. My daily driver is a still a Windows 7 desktop, but w/o browser upgrades I'm having trouble accessing my regular sites. Tried W10 a few year ago, hated it and went back to W7, but W7 just simply isn't an option anymore. 

Bought a cheap Chinese NUC with Ubuntu pre-installed and so far so good but there's a bit of a learning curve, so as as a crutch I bought an HP Victus base model desktop running Windows 11.  Windows 10 was bad, but Windows 11 is an outrage!!!! Hopefully I can remove W11 and use Linux instead.

Victus by HP 15L Gaming Desktop TG02-0013w PC
    
[LIST]
[*]Motherboard description
 HP name: Erica8 SSID: 89D8 
[*]8 GB memory; 512 GB SSD storage 
[*]AMD Ryzen&#8482; 5 5600G (up to 4.4 GHz max boost clock, 16 MB L3 cache, 6 cores, 12 threads) 
[*]AMD Radeon&#8482; RX 6400 Graphics (4 GB GDDR6 dedicated) 
[/LIST]

Thanks again!

---

### Post by oldfred on 2023-05-07
I would still suggest dual boot.
And a full backup of Windows. We get many users posting they deleted Windows & then want it back for one game or one appliation. I need it for Tax Software. Also some decide to later sell system to upgrade to a newer system and then need Windows on it to sell it.
Back when systems were primarily HDD, one user posted he removed Windows HDD, put in new SSD and used system for a year or two. Then restored unused HDD & sold system. 

Dual boot will prove Ubuntu works & does everything you want.
Some things like UEFI firmware update are easier in Windows. HP does not seem to support user UEFI update with Linux. It does now have a few commercial systems.
Devices using LVFS for firmware updates, I suggest only buying systems on this list.
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

At least make sure UEFI firmware & SSD firmware are fully updated. Even new systems may have updates.

Windows NTFS partitions really like 30% free and you may need some room for updates, if you keep it.
So shrink Windows NTFS a lot using Windows tools & reboot so it can run chkdsk and make unallocated space.
You will need fast startup & bitlocker off in Windows.

Be sure to boot in UEFI boot mode & install Ubuntu.
You will have to go into UEFI settings (not UEFI boot menu) to change boot order to make Ubuntu default.
hp 250 g3  Change boot order in UEFI settings
[https://ubuntuforums.org/showthread.php?t=2467077](https://ubuntuforums.org/showthread.php?t=2467077)

Does not show UEFI or BIOS boot screens and shows LVM which erases entire drive screen, which you may or may not want.
I like to create partition(s) in advance and use Something Else to choose (change) partition to /. You can do that during install.
[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

More general info in link below in my signature.

---

### Post by QIII on 2023-05-07
I'll agree with Fred.  Windows on the desktop is still useful in a world where most desktop users still reside.

I don't like the terms "stupid question" and "newb".  There is no need to demean yourself.  "Newcomer" and "question" will suffice.

---

### Post by Impavidus on 2023-05-08
As you noticed, there's a learning curve. People who switch to Ubuntu only because they hate Windows often find that Ubuntu isn't what they hoped for. But it can be done. I've been on Linux only for about 15 years. First make sure you don't need any Windows-only software. The tools for installing updates to car navigation devices can be problematic, in some countries the tax service expects you to use some Windows software to fill in your tax report, using printers and scanners is sometimes a problem, but usually works fine. If you only want to use a web browser, it shouldn't be too much of a problem.

First make sure that Ubuntu works fine on your hardware. You can test using a live disk. If you need proprietary graphics drivers, you can only install those on a fully installed Ubuntu system, but I don't think you need those. If you're ready, start the installer and tell it to use the whole drive to install Ubuntu. It will wipe Windows in the process. To get Windows back later, you'll need a Windows installation disk.

---

### Post by nowindows2 on 2023-05-08
I appreciate you both taking the time to respond, but I specifically said I  don't want a dual boot system. My concern after removing W11 and replacing it with Ubuntu is whether the drivers/peripherals will still work.

Thanks anyway. I'll just wing it and see what happens. Sucks that it's a brand new computer though - hopefully I won't render it useless.

Thanks for your time :)

@ QIII 
I'm not demeaning myself  - I am a stupid newb when it comes to Linux, but don't plan to stay stupid.

---

### Post by nowindows2 on 2023-05-08
I'm actually looking forward to figuring things out and you folks did an amazing job of making it easy to get started. Ubuntu is way more Window-like than I thought it would be. Bought a couple of books (including 2016 Ubuntu manual) so that should help. 

As mentioned, I only need the computer for accessing 4-5 regular websites (bank, Amazon, etc). All the software is on the W7 machine which I'll keep 'til Doomsday. 

Thanks for mentioning about the Live Disk thing, but I think I'm just going to jump in head first and start swimming - hopefully I won't drown :) 

I bought a hard disk eraser b/c I don't trust MS to allow me to totally delete "their" OS.

Thanks for your time and advice!!

---

### Post by Impavidus on 2023-05-08
Just a few websites should be no issue. One thing is, if this is really new hardware, you may need a very recent Linux kernel. Try Ubuntu 22.04.2, if that doesn't work, try 23.04. 23.04 only has 9 months of support, but it uses a more recent kernel, that will only appear on the 22.04 live disk with version 22.04.3, to be released in July or August. Even then, it may be a big buggy initially. It often takes a year or so before new hardware has good open-source driver support.

Ubuntu has no problem wiping Windows off the drive. Too many people do it accidentally. There may still be a Windows product activation key stored somewhere in a motherboard chip, which can be used to reinstall Windows later. It doesn't sound like you intend to do that.

Some computers take some effort to make it all work. Usually, it will work eventually.

---

### Post by nowindows2 on 2023-05-08
Thanks, and thanks for mentioning about 23.04. 

 I went to download 22.04.2 from [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop) to a flash drive yesterday and it started okay, but after 30 minutes the download failed. Tried again and same thing.

Tried 23.04 and although it took over an hour (not surprising with W7 which probably has usb 1.0),  23.04 downloaded to the flash drive just fine.

I saw there are other option such as torrent, and network downloads, but right now I'm more comfortable with downloading to a flash drive.

---

### Post by yancek on 2023-05-08
Maybe it is a question of terminology but downloading the Ubuntu iso to a flash drive is only the first step as you then need to use software specifically designed for the purpose of writing the iso to a flash drive to make a bootable usb.

---

### Post by sudodus on 2023-05-08
- I suggest that you use torrent, particularly if there the connection to the internet is flaky because the torrent process produces a correct iso file anyway.

- Just restart if there are problems. I also suggest that you download to the 'Downloads' directory on the built-in drive (not into the flash drive).

- When you have the iso file, check the the sha256sum is correct.

- Then use a suitable tool to create a USB boot drive with Ubuntu.
. In Windows you can use Rufus, Ventoy or Balena Etcher.
. In Ubuntu (on the NUC) you can use the Startup Disk Creator (a built-in tool)

- Run live (try Ubuntu without installing) in order to test how it works in your target computer (the HP).

- When you have a version that works well, install it (start the installer from the desktop when booted into the Ubuntu USB drive).

---

### Post by nowindows2 on 2023-05-09
Thanks so much for the info. Yes, the terminology was a bit confusing and I wasn't aware there were additional steps to make it bootable. 

I'll try the Startup Disk creator on the cheap NUC and see what happens, and if everything goes sideways,  I'll start a new thread.

Thanks again!!

---

