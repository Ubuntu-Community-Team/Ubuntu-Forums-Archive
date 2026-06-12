---
title: "Ubuntu trial on USB memory stick as a 'recovery' tool?"
date: 2021-03-23
forum: Installation &amp; Upgrades
---

### Post by aj34 on 2021-03-23
If, in the process of converting my Windows10 PC to a clean install dual boot (Ubuntu + W10) machine, I **** up and the PC won't boot, can I insert my Ubuntu trial memory stick to get the PC running so I can at least access the Internet for guidance? Or does it depend on how badly I **** things up? Thanks.

---

### Post by C.S.Cameron on 2021-03-23
You should be able to use the Live USB to boot your computer and access it's files as long as you did not overwrite your Windows partition.
In that case some people have had luck with Linux data recovery tools.
I had to break down and use EaseUS for my overwritten Windows drive.

---

### Post by guiverc on 2021-03-23
Just ensure you have fastboot or form of hibernate off on windows 10.

---

### Post by CatKiller on 2021-03-23
Yes. It's a great diagnostics & troubleshooting tool to have to hand. You're booting into a fully-functional full Ubuntu environment. 

Before you do the install, though, I'd recommend trying out live USBs of the different flavours for a bit first to see which one you like the most. 

> **guiverc said:**
> Just ensure you have fastboot or form of hibernate off on windows 10.

Also this.

---

### Post by oldfred on 2021-03-23
Years ago, I would install Ubuntu with every 6 month release. Usually in another small root partition.
I would make new bootable CD for many repair/recovery tools, gparted, Knoppix, parted rescue, Supergrub and a few others as well as new & older Ubuntu CD, then DVDs. Lots of CDs as each typically also had an update every 6 months, so another set created.

I now have several flash drives, with multiple repair ISO that I can directly boot. And they then can be updated since flash drive.
I also have an old tiny flash drive with rEFInd which worked great for UEFI boot when I had an issue. I think Supergrub would have also worked.

Some UEFI settings can make a difference also. Note that fast boot is an UEFI setting that assumes no system changes. Since changing system, it needs to be off. Windows fast start up sets hibernation flag and prevents Linux NTFS driver from seeing the NTFS partitions which creates issues.

---

### Post by The Cog on 2021-03-24
Yes you should be able to boot the USB stick and access the internet for help, although some WiFi adapters don't provide Linux drivers so you may need to use wired internet. Those "difficult" WiFi adapters can usually be got working later, but not easily from a live USB.

As you see from the above posts, accessing your files from the live USB may depend on whether Windows was configured for fastboot, or on whether the Windows filesystem has been damaged by the failed install.

---

### Post by aj34 on 2021-03-29
Apologies for ignoring this thread - I didn't receive the usual email notification when someone replies. And I can't find the option to "thank" individual replies to this thread. Oh well, so much I fail to understand about computing that it's a wonder I've managed to achieve what I have...

...which is: I've carried out a clean install of Windows 10 Pro 64bit to replace a troublesome W10 Pro 32 bit installation. I'm amazed to say that the clean install went perfectly (never before has anything involving W10 gone perfectly) and W10 is now working quicker than ever (not really surprising). My desktop PC contains 2 physical HDD's. I installed W10 on HDD0 and I intend to install Ubuntu 64bit on HDD1 but having read the installation guidance:

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

(and other guidance too), I'm a bit concerned that the Ubuntu installation, from a pre-prepared USB memory stick, may not offer me this choice of installation on HDD1. Guess I'm about to find out.

Anyway, thanks for your guidance and suggestions about UEFI, wifi connectivity, fastboot and recovery advice.

---

### Post by CatKiller on 2021-03-29
> **aj34 said:**
> I'm a bit concerned that the Ubuntu installation, from a pre-prepared USB memory stick, may not offer me this choice of installation on HDD1. Guess I'm about to find out.

The default option is nuke-and-pave, and the second option is to shrink an existing OS install to make space for the new one. There's a fully manual option (which used to be called "Something Else," but I don't know if it still is) that will let you set partitions where you like, mounted however you want. You can reuse the existing EFI partition on your first drive for the bootloader (which is the default, and a bug meant that it still happened even if you told it not to).

---

### Post by aj34 on 2021-03-30
> **CatKiller said:**
> The default option is nuke-and-pave, and the second option is to shrink an existing OS install to make space for the new one. There's a fully manual option (which used to be called "Something Else," but I don't know if it still is) that will let you set partitions where you like, mounted however you want. You can reuse the existing EFI partition on your first drive for the bootloader (which is the default, and a bug meant that it still happened even if you told it not to).

Yes, the third installation option is still "something else" and it's the option I chose. However, I then faced a bewildering array of (I imagine?) partitions and stuff so I had no idea how to select the partition or HDD, that I wanted to install Ubuntu on (i.e. the second HDD). Ubuntu seems to present HDD and partition options (and whatever else I saw on the page) in a way I've not seen before. Very confusing. I had to bail out at that stage as I didn't want to risk ruining a perfectly good, and very recent, W10 install on HDD0.

My second HDD has numerous partitions, an old Windows OS and lots of personal folders. I don't want any of this anymore. I currently have Macrium Reflect on trial. Would it be simpler for me to wipe the second HDD completely to leave just one giant partition? Is that even possible? Doing so might make my Ubuntu installation choices understandable (he says in hope!).

Is there an installation/setup guide with screenshots? Any pointers or guidance most welcome, thanks.

---

### Post by CelticWarrior on 2021-03-30
First of all, do NOT create partition(s) to install Ubuntu outside from the installer (or a Linux tool like Gparted). There's absolutely no need.

Secondly, not knowing a few things is not an option. You need to familiarize yourself with your hardware (drive) in order to be able to recognize them in the manual installation dialog ("something else"). Namely you need to be able to identify which drive contains the Windows installation that you want to keep. This is probably the same one containing the ESP (EFI System Partition) that you want to keep, obviously, and must also select for use as "EFI" for the Ubuntu installation irrespective of this OS being installed in a different drive. Then, also in the same dialog you can select and remove all the unneeded partitions in the second drive where you want Ubuntu installed and create at least one to be used as root (/). You can also have a separated /home if you want and even create a traditional swap partition (not required because Ubuntu uses a swapfile by default now). More complex partitioning & encryption is an option but better not go there if you're already struggling with the basic stuff.

In a nutshell you only need a (new) root partition and select the pre-existing ESP in order to install the dual-boot.

---

### Post by aj34 on 2021-03-30
> **CelticWarrior said:**
> First of all, do NOT create partition(s) to install Ubuntu outside from the installer (or a Linux tool like Gparted). There's absolutely no need.

Secondly, not knowing a few things is not an option. You need to familiarize yourself with your hardware (drive) in order to be able to recognize them in the manual installation dialog ("something else"). Namely you need to be able to identify which drive contains the Windows installation that you want to keep. This is probably the same one containing the ESP (EFI System Partition) that you want to keep, obviously, and must also select for use as "EFI" for the Ubuntu installation irrespective of this OS being installed in a different drive. Then, also in the same dialog you can select and remove all the unneeded partitions in the second drive where you want Ubuntu installed and create at least one to be used as root (/). You can also have a separated /home if you want and even create a traditional swap partition (not required because Ubuntu uses a swapfile by default now). More complex partitioning & encryption is an option but better not go there if you're already struggling with the basic stuff.

In a nutshell you only need a (new) root partition and select the pre-existing ESP in order to install the dual-boot.

Thanks for your reply. I broadly understand what you're saying but some terms are alien to me. Thing is, I do understand my two HDD's, the partitions and what's on them when I view them in Macrium. Problem I have is that Ubuntu presents installation options like it's a foreign language. Is there guidance somewhere that explains the Ubuntu installation language? Thanks.

---

### Post by oldfred on 2021-03-30
Your question is about using USB flash drive as a recovery tool in Installation & Upgrades part of forum.
If you do not at all understand installing, it may be better to ask a new question in the Beginner Area on installing.
Best to understand partitions as Windows calls partitions drives, but Linux only uses drives for physical devices.

Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Shows Windows screens
[https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi) 
Linux on UEFI: A Quick Installation Guide

---

### Post by aj34 on 2021-03-30
> **oldfred said:**
> Your question is about using USB flash drive as a recovery tool in Installation & Upgrades part of forum.
If you do not at all understand installing, it may be better to ask a new question in the Beginner Area on installing.
Best to understand partitions as Windows calls partitions drives, but Linux only uses drives for physical devices.


Thanks for the advice. I'm checking out various online Ubuntu installation guides at present in an attempt to find one that makes sense to me. If I need to come back to Ubuntu Forums, I'll post as you suggest, in the "New to Linux" forum.

---

### Post by CatKiller on 2021-03-30
> **aj34 said:**
> Problem I have is that Ubuntu presents installation options like it's a foreign language.

Back in the day (I haven't used Windows for a *long* time) I used to use Partition Magic. The gparted interface used by the Ubuntu installer was very familiar.

You'll want to be aware of the concept of partitions. That's pretty basic knowledge that you can pick up anywhere.

The Linux-specific bit is that (unlike Windows, which calls partitions "drives" and gives them a "drive letter") any filesystem on a local machine (or on a completely different machine) can be **mounted** anywhere (the "mount point") in the filesystem tree, which starts at /. You can use as many or as few as makes sense for your own usage, and you can use whatever filesystem makes most sense for what you're going to use it for.

At minimum you'll need a filesystem to be mounted at /. Locations in the filesystem tree that aren't mount points for a different filesystem will be directories in this one. ext4 is the default choice for that, and is a sensible one. On a UEFI system you'll also need a FAT-formatted ESP to hold the bootloader. You'll be reusing the one that you have for Windows (on your existing drive) for that.

A partition for /home is something that people sometimes like to have. If you do that, your / partition will only need to be fairly small - on the order of a few dozens of GB - and the /home partition would be big. Your /home partition holds each user's settings and data - music, videos, Steam games, and whatever. This would also need to be a Linux-native filesystem like ext4. 

You can also choose to mount non-Linux filesystems somewhere, like a directory under /mnt, if you want to transfer data between your Linux and Windows installs. If you're using a Windows filesystem for that, like NTFS, you'll want to use Windows tools to administer it. They don't support permissions and they need things like defragging, so they aren't good for usage, but they're fine for data sharing. Any Windows-native filesystems will "disappear" if you let Windows hibernate, which Windows will choose to do after updates.

---

