---
title: "Grub can't find Windows 7 (no such partition) after Lubuntu install"
date: 2014-02-10
forum: Installation &amp; Upgrades
---

### Post by inq2 on 2014-02-10
I figured it is about time I stopped running in circles. 

Win 7 was installed first, Lubuntu second. This resulted in the Grub prompt and "no such partition". Attempts to use Grub from the prompt were unsuccessful. A simple ls would list the available drives, but attempting to list the contents of any drive would not work and get the "unknown file system" message. After each failure I would boot to the Win 7 DVD so I could use "bootrec /fixmbr" and "bootrec /fixboot" to get my win 7 installation back. I have tried various things with no success so far. In addition to my Lubuntu DVD and my Win 7 DVD, I now have a copy of the Ultimate Boot CD and the Boot Repair disk. I even have Lubuntu on a USB drive ... which was of marginal usefulness. I have tried various things with no success off each of those disks. 

The Lubuntu install and partition is still there. I can see it when I boot to the Lubuntu Live DVD. Using Paragon ExtFS I can access it from Windows and access the files themselves.

Here are two paste.ubuntu snapshots. 

This is prior to the last boot repair attempt:
[http://paste.ubuntu.com/6912546/](http://paste.ubuntu.com/6912546/)

This is after the last boot repair:
[http://paste.ubuntu.com/6912596/](http://paste.ubuntu.com/6912596/)

I had to use bootrec again so I could boot into Win 7.

I have been at this for about a week and a half. This includes a complete wipe of the HD, fresh partitioning, and fresh installs of Win 7 and Lubuntu. Rather than do something drastic to break the circle I figured it was time to seek help here in the forums.

---

### Post by sudodus on 2014-02-11
Welcome to the Ubuntu forums :-)

I don't see any obvious error in the pastebin informtion.

1. Please describe in detail what is happening, when you try (tried) to boot!

2. What is the setting of the BIOS/UEFI? You have an MSDOS partition table, that means you should run in BIOS mode (not UEFI).

3. Which version of Lubuntu are you trying?

4. Please describe the computer:

- Brand name and model
- CPU
- RAM (size)
- graphics chip(card
- wifi chip/card

When we know about these things, it will be easier to give relevant advice.

---

### Post by inq2 on 2014-02-11
I just finished editing the original post for clarity. It was written late at night after hearing some bad news.

To answer your questions ...

When I boot I get the message "no such partiton" and followed by the grub prompt. ls shows the drives but I get "unknowfile system" when I try to list drive contents.

I am using Lubuntu LXLE 64 bit ... 12.04.4

The computer is a "put together" from old parts using an old MSI motherboard from a Medion PC, an MS 7123 ... it is from 2005 (using BIOS date). Programs like CPU-Z and Speccy report the MB as NF-CK804. The BIOS is locked so there are only a tiny handful of settings I have access to. I have a request in elsewhere to unlock it, but not hopeful. Apparently AWARD Bios's are problematic for unlocking. As far as I know the motherboard is BIOS. When Win7 was installed on the cleaned drive, it partitioned with MBR. I have assumed MBR throughout this whole process. The chipset is Nvidia nForce4. 

CPU is an Athlon X2 3800+ and I have 4 Gig ram installed. Graphics card is an Nvidia GeForce 9600 GT. The wireless card appears to be a D-LInk DWL-Ag530. I have had no problem connecting from the Live DVD boot.

---

### Post by inq2 on 2014-02-11
And thanks for the welcome! :)

---

### Post by sudodus on 2014-02-11
For such an old computer I would also try a 32-bit flavour, re-spin or distro based on Ubuntu 12.04 LTS:

LXLE, Bento, Bodhi, or Precise Gnome Classic Tweaks with LTS until April 2017 or Xubuntu with LTS until April 2015.

There might be problems with the Nvidia graphics card, that you might fix temporarily with the boot option **nomodeset**. See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

and then you should try to install one of the proprietary drivers for nvidia graphics, for example 173 or 304

```
sudo apt-get install nvidia-173
```
or
```
sudo apt-get install nvidia-304
```

---

### Post by inq2 on 2014-02-11
Unfortunately I can't do that from the grub prompt. I guess I should also have said that I can't boot into Linux either.;). Right now I can always reverse things enough to boot back into Win 7 (using bootrec), but I lose the ability to boot into Linux. 

I have been pondering a few things today. I tried a couple more installs varying where grub was to be installed, and then I did something different. I deleted the Linux partitions and created a new one with a reduced size. The next time I got the grub rescue prompt and did an 'ls' I realized it listed 4 partitions. It finally dawned on me that previously I had seen 2, then 3 partitions, but never 4. That reminded me of a problem between age of the bios the ability to recognize drives greater than ... I think it is about 2.2 Tbytes. That has me thinking about the existing partitions and their sizes. 

I am going to try another install, but I am going to reduce the size of the NTFS partition and make the linux partition smaller too and see what happens.

I'll update you with what happens.

---

### Post by inq2 on 2014-02-11
btw, I just install the 3 Tbyte drive about 2-3 weeks ago when my old 250G drive started to fail. Lubuntu worked fine as a dual install with Win 7 on that drive. The nVidia graphics drivers worked fine under LXLE as well.

---

### Post by sudodus on 2014-02-11
What happens if you make a GPT (GUID partition table) on that drive? I think it can manage larger disks than MSDOS partition tables.

---

### Post by oldfred on 2014-02-11
Some old BIOS may not recognize the very large drive. But you have to use gpt if you want to use the full size as MBR(msdos) only goes to 2TB.

Some old BIOS only boot from the first 137GB of a drive, so I often suggest smaller / (root) partitions of 20 or 25GB. If using gpt and booting with BIOS, you also need a bios_grub partition of 1 or 2MB unformatted with the bios_grub flag. I have gpt but on smaller drives 160GB & 60GB SSD booting with BIOS.

My desktop from late 2006 has Intel CoreDuo with 4GB of RAM and I also have the nVidia 9600GT as my original 7600GS blew out its capacitors (literally).
I use 64 bit Ubuntu but use fallback/flashback not Unity.

Because of the nVidia card I have to use nomodeset on install, and on every boot until I install the nVidia drivers. You can install current, current-updates or even the experimental versions. Do not install the old version like 173 as that is for legacy cards.
My working install has current-updates, but in some of the newer install I have installed experimental & it has also worked.

---

### Post by inq2 on 2014-02-11
I will have to try the GPT thing. I recall converting from MBR to GPT, on the old drive, but I can't remember which program I used for it.

---

### Post by oldfred on 2014-02-11
I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

But I also install gdisk as that is the command line tool for partitioning and listing partitions, etc.
sudo apt-get install gdisk

      
 Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.
[http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)
[http://www.rodsbooks.com/gdisk/advice.html](http://www.rodsbooks.com/gdisk/advice.html)


 [https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

---

### Post by inq2 on 2014-02-12
I apologize. I should have given at least a small update last night. Things got really crazy here for a while yesterday. Right now I am doing a backup before I do anything. Most of that is downloads, but I might as well cut down on my internet bandwidth this time around. Backup includes both windows and linux nVidia graphics drivers as well as the different linux iso's. 

I found the need for nomodeset inconsistent. Before I finally settled on lxle I could boot to some install DVD's without needing it. Others needed me to use it. The same goes for the different tool iso's I downloaded. Most were fine, but not all.

I also realized last night that I had converted from MBR to GPT on the 3Tbyte drive, but that was prior to me flattening it and doing things fresh. I wanted to go with defaults for everything and the Win 7 install went with MBR. I was going to do a conversion from MBR to GPT last night without backing up first when common sense kicked in. Which is why I am backing things up now. I would have done this last night but I had to set up a network drive plugged in to my wireless router. That was a steal I got a couple weeks back, a new 1 TByte WD MyBook Live for $40 :cool: 

I did find a copy of the freeware EasyBCD which lets me work from the windows side of things. It is able to see both Win 7 and lxle installs. But I haven't really poked into it much.

But, it's time to get the kids off to school before I do anything else.

Thanks for your help so far guys!

---

### Post by inq2 on 2014-02-12
To make a long story short, ended up cleaning the HD, windows won't install to a GPT drive, so I fix that and install windows. I then install lxle, watch it do everything, including grub install and update, And when that is done, I reboot hoping to get the dual boot screen ....  and I get the grub rescue prompt. I complete the circle with bootrec /fixmbr and /fixboot. I am now back to where I was when I first started, and when I wrote this email. I have learned a lot over the last few days, but nothing that seems to help me fix this problem. I am in the process of getting the drivers and stuff updated in windows install.

The way things stand, I think my next step will be looking into easyBCD to see whether or not it would be useful to approach the problem from the windows side of the equation. Not sure if I will get to that tonight or not.
 
I am still open to your ideas. I know I can get my windows install back by using bootrec, so fire away, even if I have done it before. It could be that I missed something or did something out of sequence.

---

### Post by sudodus on 2014-02-12
How big is your Windows partition? Maybe the linux parittion (or the /boot directory) is too far away from the drive head for the boot to work. Maybe you can make a small /boot partition right after the Windows partition (and the whole /boot partition should be within oldfred's first 137 GB), or make a small / (root) partition and a bigger /home partition or plan to put data into a separate ***data*** partition, so that the whole root partition of linux can be within 137 GB from the head end of the drive.

An obvious alternative at this stage is to try some other version of Ubuntu or flavor, re-spin or distro based on Ubuntu. LXLE, Bento, Bodhi, or Precise Gnome Classic Tweaks with LTS until April 2017 or Xubuntu with LTS until April 2015. You can also try Lubuntu 13.10, Xubuntu 13.10 or Ubuntu Gnome 13.10.

---

### Post by inq2 on 2014-02-12
I've thought about switching flavours, but I also get really stubborn at times like this and dig my heels in. I haven't exhausted all possibilities yet. The reason I want to keep on going is because on the last install, easyBCD saw my Linux partition. When I added it to its version of Grub, there was a menu that gave me a choice between Windows and Linux. I configured the Linux entry wrong so that it didn't work, but the fact that I had a menu that gave me a choice tells me that dual booting with what I have is still possible.

---

### Post by sudodus on 2014-02-13
What about the position on the disk 'surface', and the 137 GB limit?

---

### Post by inq2 on 2014-02-13
I am actually reading up on the 137 gig limit. That is actually starting to make sense because of a couple of things that have been happening. Using EasyBCD I get a menu, and then when I select Linux, I get cmain() followed by a boot kludge error message with numbers and it stops looking for grub stuff. I will be back after playing with partitions and moving a few things around.

---

### Post by inq2 on 2014-02-13
I am writing to you from within Lubuntu lxle. Before I got there, I got two different grub things from what I got yesterday. One said it was trying to find a file and gave a list, but I suspect it was pointing to a wring drive or directory. The second one I got said it was a limited version of Grub and that I could use TAB to get a listing of commands, etc.

I had tried to use easyBCD but that was not successful at all. I just got a grub prompt. I did the bootrec /fixmbr and /fix boot. I followed that by booting to the boot repair disc, and that did the trick.

It took a little longer than I expected because I didn't resize my partitions properly the first time to get under the 137 gig limit. But even then I got the grub prompt with the explanation about using TAB.

This has been a most interesting journey. I appreciate all the help and suggestions. I have rarely been this stumped by a problem. I will do a quick boot to windows and then come back and mark the thread as solved.

---

### Post by inq2 on 2014-02-13
In windows. I'll mark the thread solved.

---

### Post by sudodus on 2014-02-14
Congratulations :KS

---

