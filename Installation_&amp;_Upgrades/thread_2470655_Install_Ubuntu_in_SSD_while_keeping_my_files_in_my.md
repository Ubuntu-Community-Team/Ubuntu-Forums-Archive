---
title: "Install Ubuntu in SSD while keeping my files in my HDD"
date: 2022-01-06
forum: Installation &amp; Upgrades
---

### Post by hcmendez on 2022-01-06
Hello, I'm thinking on trying Ubuntu for my work and daily use PC, and I would like to ask you for guidance on if it is the right move.

I'm a Graphic and Web Designer/Developer, and the software I use is mainly Adobe Software: Photoshop, Illustrator, XD, Dimension. I also like to play videogames in my spare time, in addition I will be studying we development to a full stack level.

Do you think is the best option to move to Ubuntu from W10? I'm really bored of Windows and would like to make the jump.

I have tried Ubuntu before, long time ago, but as Dual Boot, I really liked it. Now I'm thinking on replacing my complete OS.

As storage, I'm using 2 drives, an SSD and HDD. My W10 OS is running on the SSD, a Kingston SSD SATA A400 M.2 240gb ([link]("https://www.kingston.com/es/ssd/a400-solid-state-drive?partnum=sa400m8%2F240g")), and all my work, personal, music, and game files are storaged in the HDD, a Seagate Barracuda 1TB ([link]("https://www.geektopia.es/es/product/seagate/barracuda-1-tb/")).

What I'm worried about is if my current files would be deleted, the HDD files. I'm fine with formatting the SSD and using it for Ubuntu, but:

- Will the HDD files be deleted or corrupted? 
- Will I be able to see those files and open them using something like Wine (most of my files are .rar .zip .doc .xls .pdf .dwg, Adobe files)._
- Will I be able to install other windows specific software using wine? (Archicad, AutoCAD, Lumion)
- Will I be able to install Steam, Battle.net, and stand alone games?
- Will I be able to install Videoconference and chat apps like Zoom, RingCentral, Telegram, Skype?
- And finally, would it be possible to go back to W10 if I need to?

Can you please help me with this and give me some advice?

Thank you in advance.

---

### Post by Impavidus on 2022-01-07
> **hcmendez said:**
> - Will the HDD files be deleted or corrupted? 
No, not if you're careful, but it's easy to make a mistake. Furthermore, I assume the HDD is currently formatted as an NTFS partition, which is the native Windows filesystem. Ubuntu can read and write on NTFS filesystems, but cannot defrag them or fix them if damaged, so if you remove Windows, you cannot continue to use the NTFS partition forever. Changing to a native Linux filesystem requires formatting, so all files will be lost.

> - Will I be able to see those files and open them using something like Wine (most of my files are .rar .zip .doc .xls .pdf .dwg, Adobe files)._
For some file types, there are Linux alternatives. Opening .pdf or .zip is no problem, .doc and .xls usually work fine (although there may be problems with some macros and the layout of documents may get damaged a bit). But if no Linux tool exists for some filetype, you need the Windows software. Adobe doesn't provide Linux versions of its software.

> - Will I be able to install other windows specific software using wine? (Archicad, AutoCAD, Lumion)
Some Windows software can be installed on Ubuntu using Wine. Sometimes it works great, sometimes it doesn't work at all. Don't hold your breath. See [https://appdb.winehq.org/](https://appdb.winehq.org/) for other users' experiences with the software you want to use.

> - Will I be able to install Steam, Battle.net, and stand alone games?
There are some native Linux stand-alone games (enough to keep you entertained if you're not too picky), some others may work under Wine, there's also Steam for Linux. Many others don't work.

> - Will I be able to install Videoconference and chat apps like Zoom, RingCentral, Telegram, Skype?
Yes.

> - And finally, would it be possible to go back to W10 if I need to?
You can wipe Ubuntu and reinstall Windows, if you like. You'll need a Windows installation disk and it will wipe your hard drive. Windows cannot access native Linux filesystems.

Looking at all that, it seems you heavily depend on Windows software (Adobe stuff also works on Mac, but not on Linux). Moving to Ubuntu doesn't appear as a logical choice to me. Wine may be acceptable if you occasionally need a Windows-only tool, but if you want a complete Windows environment, stick to Windows.

There are open-source alternatives for much of the software you use (LibreOffice, Gimp, ...), which have versions for both Windows and Linux, but they're not the same and will take time to get used to. If you manage to migrate from the Adobe software to open source, you can consider moving to Ubuntu.

---

### Post by tea for one on 2022-01-07
As you are heavily dependent on Windows for your work, it would be essential to continue using Windows as installed.

Anyway, here's a suggestion:-

Remove your HDD and purchase an enclosure for the drive (to use externally later)
Buy another HDD and install Ubuntu
Each OS on a separate drive is easier to manage

Are you familiar with booting in UEFI mode and choosing the OS via a dedicated boot key?

---

### Post by hcmendez on 2022-01-08
Thanks for your answers, I'll have it under consideration and see if I make the jump.

---

### Post by hcmendez on 2022-01-08
> **tea for one said:**
> As you are heavily dependent on Windows for your work, it would be essential to continue using Windows as installed.

Anyway, here's a suggestion:-

Remove your HDD and purchase an enclosure for the drive (to use externally later)
Buy another HDD and install Ubuntu
Each OS on a separate drive is easier to manage

Are you familiar with booting in UEFI mode and choosing the OS via a dedicated boot key?

I have 2 drives, my SSD is the OS drive only, and my HDD is files only. I only use SSD for OS.

I'm not familiar with booting via a dedicated boot key.

---

### Post by QIII on 2022-01-08
Based on your needs -- which imply the possibility that you will lose your ability to work and make a living -- I am going to echo some of the foregoing with a more direct answer:  Don't do it.

If you would like to use Ubuntu, I suggest doing so in a virtual machine.  This will allow you to keep Windows and not worry about software compatibility or alternatives.  You can have the Ubuntu virtual machine running all the time and switch to it when you want to use it.

I run Kubuntu and have several virtual machines running at the moment, one of which is Windows.  I rdp into it via an alias in .bashrc (that is, I input a short command in the terminal, which I have aliased as rdpwin).  You can do the same thing the other way around with a VM application suited for Windows.

All that said, let me reinforce my advice:  Your livelihood is too important for experimenting with a switch to Linux.  Keep using Windows.

---

### Post by tea for one on 2022-01-08
> **hcmendez said:**
> I have 2 drives, my SSD is the OS drive only, and my HDD is files only. I only use SSD for OS.

I'm not familiar with booting via a dedicated boot key.

The dedicated boot key is a special key specified by the PC vendor.
For example:-
[LIST]
[*]F10 - Intel
[*]F12 - Lenovo
[*]F9 - HP
[/LIST]
If you have attached a USB stick or DVD drive containing an OS, then you would power on the PC, press the dedicated key and select the device you wish to boot.

Also, if you have two (or more) Operating Systems on separate disks, you can boot either OS via the dedicated boot key.

You can remove either disk and the remaining disks should still boot independently (assuming they have been installed as an individual system)

Some info here [https://www.makeuseof.com/tag/how-to-change-the-boot-order-on-your-pc-so-you-can-boot-from-usb/](https://www.makeuseof.com/tag/how-to-change-the-boot-order-on-your-pc-so-you-can-boot-from-usb/)
There are hundreds of websites with similar info but you should have a look at the specific instructions for your PC.

---

### Post by ratty01 on 2022-01-09
This post caught my interest because I have a SSD with Ubuntu on it and two other internal Hard Disks with data. The idea being I can erase the SSD and reinstall Ubuntu when I have issues or want to upgrade.

Now following a recent disaster I have just reinstalled Ubuntu on the SSD and the two HD are visible in files and they sit under media on the SSD. I need to look at how the Ubuntu hierarchy file system works as I'm struggling get the folder path into subsonic.

---

### Post by oldfred on 2022-01-09
@ratty01
Best to start your own thread and post some details of fstab, partitions, etc.

---

### Post by hcmendez on 2022-01-12
I recently tested Ubuntu 21.04 from a USB installer and I couldn't access to one partition of my HDD. Should that be happening?

I have two main partitions on my HDD: Work files (.docx .pdf .psd .ai .xd .jpg .png), Multimedia and Games files (.mp3 .jpg .png), and Ubuntu didn't let me access to the Multimedia and Games partition.

---

### Post by oldfred on 2022-01-12
Ubuntu 21.04 Hirsute Hanimal EoL 2022-01 when you stop getting updates.

Better to use LTS - long term support like 20.04LTS, unless you have very new hardware. Then latest version may work or even need newer kernel & drivers.
22.04 will then be out in April.

Post these, in code tags.
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint
cat /etc/fstab
mount

---

