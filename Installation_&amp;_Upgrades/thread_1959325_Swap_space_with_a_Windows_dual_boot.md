---
title: "Swap space with a Windows dual boot?"
date: 2012-04-15
forum: Installation &amp; Upgrades
---

### Post by raen on 2012-04-15
Potentially stupid question here, but I figure it's better to ask and receive confirmation than not ask and do it wrong.

I'll be getting a custom-built computer system soon and I plan to dual boot Windows 7 Professional with Ubuntu 12.04 LTS Precise (once it's fully released out of public beta).

I'm building this myself from the ground up, something I've never done before. I've also never set up a dual boot before. Thus I'm slightly confused, and I haven't even gotten started yet. I've already asked other questions [in a different thread]("http://ubuntuforums.org/showthread.php?t=1946332") but now I'm looking for clarification on a different point.

I'll be getting two 1.5TB HDDs. Per advice, I'll install Windows on the first and Ubuntu on the second, with the other HDD disconnected while installing the respective systems.

This seems to imply to me that each system will have its own swap setup. Will Ubuntu, like Windows, manage that automatically, or should I manually set it when I install Ubuntu? I'm getting 8GB of RAM. Or, once both drives are connected, will I be able to play around with the partitions and set up a common swap partition in much the same way I'll be setting up a common NTFS partition? Or is that a bad idea/not feasible?

I've never dealt with partitions before, so any advice and/or explicit instruction will be greatly appreciated.

Thank you.
raen

---

### Post by Herman on 2012-04-15
> This seems to imply to me that each system will have its own swap setup.  Will Ubuntu, like Windows, manage that automatically, or should I  manually set it when I install Ubuntu? I'm getting 8GB of RAM.When you are installing Ubuntu you will have a choice of letting the installer automatically partition a disk to install Ubuntu in or you can choose to do it manually.
If you choose automatic, the Ubuntu installer will make a partition for the operating system and a small swap area.
If you chose manual, you can create your own swap area or not, it's up to you, and the size to make it will be up to you too. 
If your new machine will have 8 GB of RAM, Ubuntu probably won't need to actually use the swap are much at all while it's running. From my own observations though, I have the feeling that Ubuntu works a lot better if I even make a very small swap area, just to keep the kernel happy.
Your Ubuntu would not actually need to use very much swap if you decide to hibernate rather than shutting down your computer.
The old rule of thumb was to make swap about twice the size of RAM for hibernating, but I don't know if that's still true now or not, since more PCs have such large amounts of RAM. Probably you won't need anywhere near it, and it likely depends on how many programs you want to be able to leave open.

> Or, once both drives are connected, will I be able to play around with  the partitions and set up a common swap partition in much the same way  I'll be setting up a common NTFS partition? Or is that a bad idea/not  feasible?I haven't heard of any Windows having a separate swap area per se, but I have recently read of someone who said their PC had a hibernation partition for Windows. Windows normally has a 'page file' and no separate partition for swap.
I don't think it would be a good idea to try to share a swap area if you want to use it for hibernating and I don't know if a swap area can be shared between Windows and Linux. I know that it is perfectly feasible to have a shared swap between many Gnu/Linux installations, but only if you don't hibernate your computer. If you do they might overwrite each others files I imagine.

It is always possible to play around with things and experiment later, but I'd say at install time I'd be just installing both operating systems in their own drives and keeping things as stock-standard as possible for the initial install at least.

While Ubuntu will automatically manage its own memory and swap area while it is up and running, there are optional settings you can make to tell the kernel how much to favor the swap area and how much to prefer to use the RAM as a percentage. It's called 'swappiness'. By default it's 60/40, but I found by trial and error that my favorite settings are 90/10 in favor of heavier use of the (faster) RAM. Any more than that and my system seems to slow down rather than speed up. The sweet spot likely varies with different hardware and different users.

---

### Post by oldfred on 2012-04-15
I always suggest users review these instructions by Herman for installing on two different drives. He has a lot of detail. And versions of installs are not a lot different so his screenshots apply across many versions of Ubuntu.
If you do not disconnect Windows drive you have to use manual install or Something Else and be sure to pick the correct drive to install grub2's boot loader to.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

If you use the auto install of just Ubuntu into a drive somewhat over 1TB it will auto convert to use gpt.  You do not have to use gpt unless drive is over 2TiB or 2TB unless new system is booting with UEFI not BIOS. Windows will only boot with gpt if you are in UEFI mode, but it will read data in gpt partitions. You can have MBR for Windows and gpt for Ubuntu(thats what I have had), but if in BIOS mode you also have to create a small 1MB bios_grub (flagged) partition.

GPT info
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

