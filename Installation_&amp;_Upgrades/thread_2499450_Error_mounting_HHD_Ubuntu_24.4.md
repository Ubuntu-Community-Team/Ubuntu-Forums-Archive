---
title: "Error mounting HHD Ubuntu 24.4"
date: 2024-07-27
forum: Installation &amp; Upgrades
---

### Post by Angel130000 on 2024-07-27
Hello! I am experiencing a recurring problem when trying to mount any storage device in my Ubuntu 24.4 installation. This issue has been present in my installations since 2016, despite using Ubuntu since 2004. Although many resources point to a possible hard drive error, I am sure that is not the cause, as the same devices automatically mount in other systems.


I am looking for a solution that will allow me to avoid having to resort to the terminal to mount devices and that I can apply permanently for future operating system updates.


Furthermore, I have noticed issues with mounting Pendrives, especially with formats like ext3 and 4, fat, and ntfs. Every time I upgrade to a new LTS version of Ubuntu, I feel like I am going back in time, facing challenges with Snap that always fail to update and even mouse configuration... come on!

This is the error that pop's up "**wrong fs tupe, bad option, bad superblock on /dev/sdc1, missing codepage or helper program, or other error**"


I appreciate any help or solution you can provide to resolve this issue, as I find it frustrating to adapt to the new features of Ubuntu. Thank you and regards!


PS: I have been trying to get used to the new version of Ubuntu for a week now, and I find it challenging, even with simple tasks. I appreciate any assistance you can offer.

---

### Post by TheFu on 2024-07-27
So, after re-re-reading your post, what I know is that 
a) you have always struggled with mounting nearly any file system.
b) you've been a user nearly 2 decades
c) you want to avoid ever needing to do anything on a new install - it should "just work", regardless.
d) claims that "my hardware is good", but no proof of that.

What I don't know is 
* exactly what you've tried? 
* which tools were used?
* if there are any logged errors?
* for the specific error show, which file system is being used?
* if there are other computers using the same storage from time to time?
* if there's any dual boot happening?

Help us to help you by answering all those questions.  I look forward to a complete answer. Once all the questions are addressed, we can try and figure something out, but I doubt there is a "it will work on any new install without any configuration" solution.  It is certainly possible to mount things automatically, which specific, required, mount options, to specific locations, so you don't blow your security at all.

BTW, if you use foreign file systems (exFAT, NTFS, FAT32), then the automatic mounting methods tend to have really bad performance, if they work.  Also, MSFT has changed how they deal with mounts, so while it seems like a Linux issue, in some situations, it is really caused by MSFT not properly closing the file system.  Nobody here can force MSFT to do better. We get to live with their choices and sometimes that means creating work-arounds. Some of those workarounds are handled in MS-Windows and some can be handled in Linux with customized solutions.

---

### Post by Angel130000 on 2024-07-28
Thank you very much for the prompt response!


It is true that it's the first time in a decade that I seek help here on the forum, I have always found it elsewhere. Just that this time, as it is something so recurrent, I thought there must be many out there who are going through the same.


I will be answering your questions one by one:


*What have you tried exactly?*

I have tried manual mounting. I created a folder named TOSHIBA and then in the terminal, I entered the following commands, replacing the X with the corresponding letter according to each mount.


**sudo mount -t ntfs-3g /dev/sdX1 ~/TOSHIBA**


This is what is currently helping me, but as it is somewhat tedious, I would like to fix the problem from the root cause, so I don't have to waste time mounting and unmounting each HDD I work with one by one.

[I]
What tools were used?[/I]

**The terminal.** Copying and pasting commands from pages with solutions to similar problems to mine. This has led me to reinstall the operating system several times this week because somehow I have messed up the distro. Well, when you start, you know when you start, but never when you finish solving the computer problem.


I chatted with different AIs to find a solution, but in the end, everything pointed to supposedly the disk being improperly formatted, and I am certain that the disk is perfectly fine.


I also searched for programs in the snap store related to mounting HDDs and pendrives (I don't remember which ones) but they all failed. I thought I might just be missing some specific repositories for it to be resolved, but I still can't find anything.


If there are any errors recorded

The ones I posted at the beginning, that's the error that always appears.


**"wrong fs type, bad option, bad superblock on /dev/sdc1, missing codepage or helper program, or other error"**


*For the specific error shown, what file system is being used?*

**NTFS**


[I]If there are other computers using the same storage from time to time?
[/I]
Yes, I have 3 other computers with Ubuntu 22.4, and they all mount correctly. I have 3 different HDDs, all formatted in NTFS, and they all mount correctly.


FAT pendrives also mount correctly on the other devices, and on this one, sometimes they mount, sometimes not, and sometimes it doesn't even recognize them, as is happening in this current session.


I repeat, it is a clean installation of the new Ubuntu LTS.


*Is there any dual booting happening?*

No, I only use Ubuntu.


What intrigues me the most is that there aren't more people experiencing the same issue. I could even say it's my PC hardware, but this problem has occurred on other devices in the same way.


Ultimately, could it be something related to the BIOS? Unfortunately, I don't have enough knowledge to check all the parameters involved in HDD mounting and BIOS configuration.


The strange thing is that after a while, without having done anything significant, the error resolves itself. This has happened with the latest Ubuntu LTS distros, but not this time.


As the error indicates, it is about **"missing codepage or helper program." **It should be something that some update should resolve, but I have been trying to resolve it for 10 days, without success.


You are my last resort.


I greatly appreciate your help and send you warm regards.

---

### Post by TheFu on 2024-07-28
If you only have Linux computers, don't use NTFS.  For SSD and HDD storage, ext4 is what you want, unless you have a specific reason to use any other file system.

Connections via USB are dependent on the compatibility of the USB chips both inside the computer(s) and inside the storage device.  Sometimes, those just aren't compatible.  For cheap USB flash storage, use **f2fs** if only Linux systems will use it.  If you will plug them into other, random, computers, use exFAT.

A key aspect to being an admin is avoiding issues.  NTFS brings issues.

If you want storage to be automatically mounted and removed, there's a tool for that called "autofs". It has been around over 20 yrs and "just works".  Google will find how-to guides. They all work the same, so it doesn't really matter which release or which Linux OS.  autofs can work with most file system types, since it uses regular **mount** and accepts all the mount options, unlike gvfs and gio which are less great mount tools from Gnome. Best to avoid those, actually, which I suspect you've never heard or been told.  If you point-n-click to mount things (or try to mount things), you are very likely using gvfs.

snap packages have constraints for what they are allowed to accomplish and those constraints cannot be modified or disabled.  Best to avoid them. I'd never expect a snap program to do administrative things.  For partitioning and formating storage, gparted is the tool to use.  For mounting storage, use the /etc/fstab OR autofs methods.

Oh ... and it is best never to mount storage under your HOME directory.  Instead, mount the storage somewhere else, perhaps /d/{LABEL} and create a symbolic link from your HOME to the other location.  There are reasons for this that I learned so long ago, that I've forgotten. 

I won't describe what autofs does. You can look that up. Basically, it will mount only pre-configured storage based on your configurations. Give your file systems unique LABELs to make it easier to control which is mounted, when and where.  Mount the storage to places that no other tool attempting to mount anything will touch. Having two different systems trying to mount things into the same directory is seeking out problems. Best to avoid those.

So, first step is to backup your data that's on NTFS and then format those partitions to ext4.  This removes all sorts of foreign file system issues, like you are seeing.

---

### Post by Morbius1 on 2024-07-28
Looks like a kernel bug with ntfs:

[https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/2062972](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/2062972)

---

### Post by Angel130000 on 2024-07-28
Hello again and thanks for the prompt response.


I have researched how to install and configure autofs in Ubuntu, I even used AI to give me specific parameters, but my Linux knowledge doesn't go that far, and I'm afraid I have messed up the distro again, as usual, and will have to reinstall Ubuntu again.


I've been busy with it all afternoon and honestly, I don't understand much.


I am considering installing Ubuntu LTS 22.4 and then doing a "distupgrade." Since the other distro managed to fix this issue naturally.


The new Ubuntu is complicated for me, not only because I can't mount the HHDs, there are more things I can't configure. But I won't go into detail since they are not important.


Thanks for the advice on not mounting in the /home, I will keep that in mind.


I will try to format the HHDs to ext4 if I don't find another solution.


Thanks again for your kind help.


Best regards.
Mari Carmen

---

### Post by TheFu on 2024-07-28
Did you see that Morbius1 found a kernel bug with support for NTFS?   Be certain to review that link.
Do you have that kernel version?
Does the kernel you use have the same bug?

If so, then NTFS won't be working until a kernel fix comes out and it won't matter which way you try to mount, since it is in the NTFS driver code.

If you are on 22.04, you still have until next April to move to 24.04 before any of the releases starts losing support.  A few flavors (Server and Gnome) will keep standard support for 5 yrs. I think most of the other GUI flavors have 3 yrs of support, so April 2025 is the end of support for 22.04 flavors.  You have time.

BTW, I'm running 20.04 and use **autofs** with NTFS (kernel version 5.15.0-113-generic), so it isn't impacted, except that I wish the other device I need NTFS for, didn't require it. Sigh.  All my other storage uses ext4, f2fs or ZFS.  Only 1 external USB3 SSD uses NTFS and that because it connects to a hardware-only recording device that doesn't support any other file system. In short, I don't have any choice.

autofs can be complicated, especially with foreign file systems that need more options than simple EXT4 requires.

Hint: saying you tried something, but not posted what you tried might help with your ranting/frustration, but it won't get more help. Post what you did and post your autofs config files.  Only then can people actually help.

---

### Post by Angel130000 on 2024-07-30
Hello and thank you for responding.

I apologize if I have sounded too complainy, it was not my intention.

I have just seen the post from Morbius1 and I am studying it.

I also want to tell you that my knowledge of Linux is quite basic, I only manage and still make many mistakes.

I have tried the following:

```
~$ sudo ntfsfix -d /dev/sdc1
[sudo] password for maricarmen: xxxxx
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
Checking the alternate boot sector... OK
NTFS volume version is 3.1.
NTFS partition /dev/sdc1 was processed successfully.
```

But when I try to mount the drive with Nemo or Nautilus, the same problem keeps appearing.

"wrong fs type, bad option, bad superblock on /dev/sdc1, missing codepage or helper program, or other error"

Fortunately, I am reading the posts on the page [https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/2062972](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/2062972)

They are experiencing the same issue and offer several options to solve it, one of them being the one I am applying myself:

```
sudo mount -t ntfs-3g /dev/sdc1 ~/folderX
```

This is not ideal but it's what I have. I still have more to investigate.

Thank you very much for your assistance. I am learning a lot these days :)

Warm regards

---

