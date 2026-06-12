---
title: "Dual boot PC - Windows 7 and Ubuntu"
date: 2020-10-03
forum: Installation &amp; Upgrades
---

### Post by aj34 on 2020-10-03
Would really appreciate advise on my forthcoming upgrade to a dual boot desktop PC...or even a tri-boot PC

I've seen guides/instructions on how to set up a dual-boot system but none with the same starting point as me.

My desktop PC has a 64bit processor. I currently run Windows 10 Pro 32bit which I find abhorrent and don't wish to use it - although I'm unsure I should wipe it completely. My PC has two physical hard disc drives, both large enough and quick enough for anything I want to do. I currently don't have any files I wish to keep on the second HDD - it came from my previous PC. The first HDD contains all my files (which I wish to keep) and the Windows 10 OS (which I don't wish to use but, hedging my bets, could I be greedy and set up a tri-boot system, i.e. Ubuntu, W7 and W10? This could be useful as I offer basic PC support (incl. remote control) to another person who runs W10 so it would keep my W10 knowledge current).

I have been trialling Ubuntu from a USB memory stick. I like it and want to install it. I also liked Windows 7 and wish to have a dual (or possibly tri) boot system with Ubuntu. I appreciate Microsoft support for Windows 7 has ended. I have a networked NAS onto which I recently carried out an image backup of my first HDD.

I originally installed Windows 7 from a DVD - which I still have - but it's years old now so won't have several years of updates on it and I don't know if updates would still be available over the Internet. I *should* have a backed up Windows 7 on my NAS from earlier this year (I say *should* because when I look at the NAS image backup, I can't understand what I see) and there are folders, named "Windows.old", on both HDD's (although the folder on the second HDD is so old - 2015 - it may be Windows Vista). I note that the more recent "Windows.old" on my first HDD only contains User folders, so probably not W7 OS?)

From my viewpoint (i.e. a novice), it seems logical to place one OS on one HDD and the second OS on the second HDD (don't know where a third OS should reside?) but, obviously, I'd like both (or all three) OS's to have access to my files which are all currently stored on one HDD. Maybe this is a problem?

My question is: Is a three OS boot PC even possible? In what order do I carry this out and can I re-install a version of Windows 7 that would have the final updates? 

Apologies for the long post and thanks for your consideration.

---

### Post by CelticWarrior on 2020-10-03
[https://ubuntuforums.org/showthread.php?t=2448121&page=2&p=13977654#post13977654](https://ubuntuforums.org/showthread.php?t=2448121&page=2&p=13977654#post13977654)

Already explained but apparently ignored.

Please DON'T use Windows 7 connected to the internet. For your own safety and everybody else's. It's just a matter of seconds until your PC is turned into a zombie performing attacks down the line. But there are companies still using? Yes, but they shouldn't. Anyway, it's very different running it behind a corporate firewall managed (hopefully) by competent IT professionals and having running by you at home. Someone with such misconceptions about basic stuff like dual- or multi-booting definitely should NOT be using obsolete OSes.

---

### Post by crip720 on 2020-10-03
Multi boots on one or more drives are quite possible, but all OSs should be setup the same way, legacy bios with MBR or UEFI with GPT drives.  It is a lot easier to do this with empty drives with no data on them.  Any data on drives should be considered might be lost.  Some people will have a drive for data that they can remove when doing any installs to another drive, to protect the data/drive.  People tend to make mistakes.

---

### Post by zebra2 on 2020-10-03
Microsoft discontinued upgrades for Internet Explorer on Win7 which is the backbone for some important software which the newest versions failed to run.  It was a deal killer for me.  Now using Win10 on my dual boot and it is ok with those software products.  I like you am not pleased with the rest of it though.  Interestingly I use a computer at work and the company upgraded my Win7 remotely and I ended up with Windows 10 and a Windows 7 desktop which I happen to prefer to my Windows 10 on my dual boot. Of course the work computer is on a corporate intranet and I don't have to be concerned with the under the hood stuff. 
Bottom line, Win7 can easily become a door stop depending on the software being used. This along with the security considerations which I generally ignore since that doesn't affect my linux install. I may get bashed on that last point but thats my business.

---

### Post by grahammechanical on 2020-10-03
I believe this guide is still relevant. I do not have a UEFI motherboard or Microsoft Windows of any version. So, I cannot speak from experience. But over the last few years there have been a lot of requests for help in setting up a dual boot with Windows. Reading the posts in this forum is an education.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I suggest that first you get the dual boot with Windows 7 & Windows 10 working. Backup any data you do not wish to lose. As I understand things I think that Windows 7 needs to be the first OS on the hard drive. So, you may not be successful in dual booting 7 & 10 on the same drive as Windows 10 is already installed and Windows 7 is not. But you can put Windows 7 & Ubuntu on the same drive. Or, windows 10 & Ubuntu on the same drive.

Use Windows tools to defragment and partition Windows drives and to create unallocated space to install Ubuntu in. Windows 10 is most likely installed in UEFI mode. So, you will have to install Windows 7 in UEFI as well as Ubuntu.

[https://www.partitionwizard.com/partitionmagic/win-7-uefi-install.html](https://www.partitionwizard.com/partitionmagic/win-7-uefi-install.html)

Regards

---

### Post by ajgreeny on 2020-10-03
If for some reason you still feel you really must use Windows-7, and I agree with all those saying it should **NEVER** go on the internet, install it as a virtual machine using something like Virtualbox, VmWare Player, or KVM/Qemu.

That way it will be sandboxed and a great deal safer than using it as a bare-metal system.  You can also create a snapshot of the VM in a known clean state which you can restore if the system gets infected or corrupted. However, the safest and proper way is not to use it at all!

---

### Post by aj34 on 2020-12-12
Been otherwise engaged of late hence the delayed reply.

Decision made: dual boot Ubuntu and W10.

Thanks to all for your advice and guidance - it's been really helpful in clarifying my thoughts. Clearly, keeping W7, including using it for Internet, complicates the issue immeasurably so, reluctantly it has to go. I was reluctant to ditch a good OS (W7) yet keep W10, but I have since gained more experience of Ubuntu and am seriously impressed - even though it's only a USB memory stick trial. Ubuntu will be my go-to OS with W10 utilised as little as possible.

You've given me lots of useful info. and links on the process of preparing a dual boot system ,both in this thread and the previous (linked in post#2) so I feel reasonably confident of achieving this. Just need to wait until I have a few days free when I'm not reliant on being online. Thanks again.

---

