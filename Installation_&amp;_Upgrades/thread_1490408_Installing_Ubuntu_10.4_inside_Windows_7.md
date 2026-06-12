---
title: "Installing Ubuntu 10.4 inside Windows 7"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by n0ryu on 2010-05-22
I am at a lost here. I am trying to install Ubuntu inside Windows 7 without the hassle of creating a partition. 

Here's what I have done: I downloaded the ubuntu-10.04-desktop-amd64.iso and then burned it onto CD. Ran Wubi from the CD. Selected "Install inside Windows". Waited for the Ubuntu installer to finish and then rebooted. Selected Ubuntu. Ubuntu starts to load and all. Then it ask me to pick which partition where to install Ubuntu. Why am I asked this? Am I missing something? I don't want to create a partition to install Ubuntu. I want it inside Windows. Please help. :confused:

---

### Post by darkod on 2010-05-22
If you left the cd inside when you rebooted maybe it booted from the cd.

For wubi (because that's what you are installing), you don't even need the cd, just download and run wubi.exe which I think is downloading all the files from the internet.

Anyway, take the cd out and reboot. There should be entry for wubi (ubuntu) in your windows bootloader.

But you are aware wubi is just for a short try and it was never meant to be a long term installation right? You say it avoids hassle but in fact it creates more hassle down the road later just when you've started to use it.

Usually you don't install OS inside an OS, just like you didn't install windows inside another OS. Don't blame ubuntu if problems start, it's not easy to make linux work inside windows.

---

### Post by n0ryu on 2010-05-22
I did remove the disc before rebooting. Ubuntu is one of the entries in  the boot loader. I am only testing this function. It should've worked without asking to select a partition. 

I am not blaming anyone or anything. Sorry if I sounded like that. ^_^

---

### Post by darkod on 2010-05-22
> **n0ryu said:**
> I did remove the disc before rebooting. Ubuntu is one of the entries in  the boot loader. I am only testing this function. It should've worked without asking to select a partition. 

I am not blaming anyone or anything. Sorry if I sounded like that. ^_^

No it didn't sound, sorry if I was unclear. If it starts having some issues in future of course you won't be happy with it (who would be). And I just wanted to point out that even the wubi developer has said it is not designed for long term use.

Back to your problem. Yes, you are right. It shouldn't ask you for a partition. However, because I don't use wubi, I can't remember the whole process right away.

At one point it will ask you for a partition (drive) where you want to install the ubuntu folder. That is perfectly normal because it needs to know where to put the files. If this is what you are talking about, than it's not an error. You need to select on which partition you want the files, and how much size to allocate to it.

---

### Post by deesto on 2010-06-04
I just wanted to second the fact that there seem to be multiple problems with this release of wubi+ubuntu+windows.  I am running the latest wubi (which downloads ubuntu 10.4 desktop) in Windows 7 64-bit.  When the installer starts up, it keeps complaining about a missing disk, and it does so many, many times.  But once the installer appears, it seems to go through all the motions, creates a c:\ubuntu folder, copies the installation disc there, and tells me to reboot.  So I reboot, choose "Ubuntu" from the Windows boot loader, and I see this:
```
Try (hd0,0): NTFS5: No wubildr
Try (hd0,1): non-MS: skip
Try (hd0,2): EXT2: No wubildr
Try (hd0,3): Extended:
Try (hd0,4): EXT2:
```
... and there it hangs.
AFAIK, these are the partitions the installer should care about:
2,1: Win 7 64
1,1: Win XP

It looks like the installer is (mis)reading disk 1, which has the following partitions:
1: Win XP
2: OSx86
3: ext boot partition (Fedora)
4: ext root partition (Fedora)
5: Linux swap partition (Fedora)
6: ext home partition (Fedora)

Why is it doing this?  How can I get it to work properly?

---

### Post by imipolex-G on 2010-09-12
I have the same problem as above, and it is preventing me from installing on the (single laptop) hard disk. It seems that the Ubuntu installer has a garbled view of the disk partitions (partition 3 lists as much smaller than reality, and partition 4 much larger, with neither showing the correct partition formats or labels). Oddly, if I boot Ubuntu from a USB drive, it has the correct data for these partitions.

Any ideas what might be "fooling" the installer's partition manager? My suspicion is that this has something to do with Win 7 "dynamic disk", but then why can a normal Ubuntu instance get it right?

---

