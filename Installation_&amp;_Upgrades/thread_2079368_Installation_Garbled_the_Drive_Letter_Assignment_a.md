---
title: "Installation Garbled the Drive Letter Assignment and Thus I Can't Boot Windows"
date: 2012-11-01
forum: Installation &amp; Upgrades
---

### Post by HolgerBurghardt on 2012-11-01
Hello,

today I installed Kubuntu 12.04 on my PC. But now, ever since installation, when I boot and grub opens, I can chose between Ubuntu and Windows XP (among other options like safe mode and memory test) and if I chose Windows I get back to the grub screen I just left.

Using the Windows Repair Console I can see that the drive letters are all wrong. Windows XP used to be installed on drive G now it's C. I guess that's why grub doesn't find Windows XP anymore. I don't know how that happened nor how I can fix this without reinstalling XP. (By the way, all drive letters have changed.)

I didn't want to use fixmbr or fixboot without being sure that A) it would help and B) there ain't any other way to solve this.

As much I'm glad that Linux is running on my PC - I prefer Windows as my primary OS. So if this would mean that I had to remove Kubuntu so be it. Though I would be happy if we could figure out a way to solve my problem.

Please note that I'm novice to Linux systems and don't know that much about the boot process on Windows either.

So for the time being only Kubuntu 12.04 is running.

I know so far everything I described is hardly precise, so ask away, I'll gladly give you any information you need. Please note that I live in Europe, it's night, so I'll be away now for the next 7 hours or a bit more (I'm lucky enough to be off-duty tomorrow).

Thank you!

----

[COLOR=Blue]**Summary of this solved thread:**
What has happened: [Kubuntu installed as secondary OS for a dual boot but Windows won't start but Kubuntu does]("http://ubuntuforums.org/showpost.php?p=12333174&postcount=5").
Why it happened: apparently grub was installed in the [wrong device]("http://ubuntuforums.org/showpost.php?p=12333847&postcount=9") - it should have been the root sda of the harddrive but was in the root of the Windows partition sda1.
Solution: [install grub to the root sda and fix boot sector of the Windows partition]("http://ubuntuforums.org/showpost.php?p=12334582&postcount=11").
**Please make sure that you have exactly the same problem before trying this solution!**[/COLOR]

---

### Post by HolgerBurghardt on 2012-11-02
Well, I searched a bit and found this thread on the [Puppy Linux Discussion Forum]("http://www.murga-linux.com/puppy/viewtopic.php?t=68133&sid=c5266b4872862d813fa13364881e86dc") but they weren't getting as far as finding an actual solution.

But they started talking of using a Linux-based Windows Registry editor without mentioning how to actually do that, i.e. changing the drive letter. But editing the registry even from within Windows is touchy at best so I'd like to know whether there is no other (safer) solution before trying to edit the registry.

---

### Post by oldfred on 2012-11-02
When you boot Windows it is always the c: drive. If you have multiple installs of Window then the other NTFS partitions will become different letters.

Windows XP is hard coded to a drive & partition, so if those change you may have to update boot.ini.

Best to post BootInfo report so we can see details.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by darkod on 2012-11-02
First of all, the partition letter assignment is a windows thing and doesn't influence grub booting windows. You say that another grub menu shows up when you select XP, so maybe somehow there is a grub installed on the XP partition too (it can be installed onto the Partition Boot Record - PBR, not just the MBR of the hard disk).

If that is really true, you will have to remove it since windows can't work if the PBR is not windows type.

You are right, lets not touch the windows registry yet, especially with linux tools.

If you can, it would be nice to see your bootinfo since it has many useful details. Here are instructions how to run it:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You can do that from ubuntu or from the live mode running from the cd, doesn't matter. For a start, select only to create the bootinfo and post the link it gives you. Don't select the recommended repair although in most cases it can do automatic repairs. Not sure it can help in your case since ubuntu boots and you have windows issues. That's why only create the bootinfo and post the link, lets see more details and decide what's best to do.

---

### Post by HolgerBurghardt on 2012-11-02
Thanks for responding!

Let me try to better describe my problem:

For starters: I've always booted my Windows XP from drive G - it hasn't been C in a long time now (that it's G instead of C has, as far as I remember, to do with a very virulent trojan/virus thingy about two or even three years ago).

Here is my bootinfo: [http://paste.ubuntu.com/1326750/](http://paste.ubuntu.com/1326750/)

The important drive is sda, obviously.

Still I give you here the of my devices at the time:

```
/dev/sda1        G        ntfs       SYSTEM
/dev/sda2        E        ntfs       WDEADS Downloads
/dev/sda5        C        ntfs       WDEADS Workspace
/dev/sda6        49955d1b-0097-41f2-825b-1345dbe84b70   ext4
/dev/sdb5        H        ntfs       WDEARS Storage
/dev/sdb6        I        ntfs       WDEARS Multimedia
/dev/sdc1        F        ntfs       QUANTUM Switch
/dev/sdd1        M        ntfs       SEAGATE Exchange
/dev/sdd5        N        ntfs       SEAGATE Multimedia
/dev/sde1        J        ntfs       WDEACS Video
```I've replaced the UUID from the blkid output with the drive letter as I remember them.

This was the situation when I installed Kubuntu.

But right now sda1 has the drive letter C assigned and the remaining ones seem to be randomly assigned.

When I boot my PC all works well until I get to the grub screen. If I chose Kubuntu or the memory test, everything works as it should. But when I chose Windows the grub screen disappears (as it should), the screen remains black for a short moment (maybe one second or two) than I'm thrown back to the grub screen that I've just left.

I don't think that either Kubuntu nor Grub is the problem but I believe that my Windows expects to boot from the drive G but with the changes in the drive letters there is not Windows to boot on that drive.

---

### Post by darkod on 2012-11-02
OK, here is what I see:
1. As you see at the top, you have no grub on any MBR, on any disk.

2. But you do have grub on /dev/sda1, exactly on the XP partition.

Since the kubuntu installation has only a root partition and no swap, I assume you did a manual partitioning installation yourself. The error was that you selected grub to install on /dev/sda1, the XP partition, instead of /dev/sda, the MBR of the disk. It always goes to the MBR, not a partition.

I think this might influence the letter assignment too, but lets leave that aside and deal with what has to be done.

1. Boot your kubuntu, open terminal and execute:
sudo grub-install /dev/sda

This will install grub2 to the MBR of /dev/sda, where it should have been. You might need to make sure in bios you are booting from sda with so many disks.

2. Boot with a XP install/repair cd, and do only the /fixboot, not the /fixmbr. You only need it to fix the boot sector of the XP partition, not the MBR. If that doesn't work, you can also do it with linux tools but doing it in XP recovery Console might be easier for you.

After that, reboot and lets see how it goes.

---

### Post by oldfred on 2012-11-02
Darko's solutions should work. And may be required if backup is bad.

NTFS partitions do keep a backup of the PBR - partition boot sector. And NTFS partitions have to have Window info in them not grub.

```
sda1: ______________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 1936395352 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos6)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM
```Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:

This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by HolgerBurghardt on 2012-11-02
Hullo,
before rebooting my system (I guess I'll do that tomorrow - it's almost midnight) I've done part 1 of darkod's suggestions, installing grub on sda.

Here's my new bootinfo: [http://paste.ubuntu.com/1327733/](http://paste.ubuntu.com/1327733/)

As for fixboot…

What will it fix? It won't change my drive letters, so what does it and how what that help me?

I did indeed a manual partition installation (automatic didn't work - just wouldn't let me) and as for selecting to install grub to - well, it never asked me or I didn't understand its question.

Unfortunately I don't understand what oldfred's saying. TestDisk does what? I don't have a problem with the partition, or do I? I can access any partition from Kubuntu…

I hope you understand how I appreciate your help, it's just as I said before: I know nothing about booting, no matter what OS is involved. :)

And I'm a little reluctant to do much unless I understand the reason to do it. After all, at the moment at least Kubuntu is running fine.

---

### Post by darkod on 2012-11-02
Windows can't work with the grub in the boot sector of sda1. fixboot will make the boot sector to be type ntfs again.

The same can be done with testdisk in case fixboot doesn't help or if you can't open the Recovery Console because the windows letters are mixed up now.

So, you have two options to remove grub from the boot sector of sda1:
1. XP cd, Recovery Console, fixboot
2. Ubuntu, testdisk, restore Backup BS for sda1

---

### Post by oldfred on 2012-11-02
If you want more info on why PBR is important to Windows, you can review this. It has a lot of detail, but just pictures tell most of the story.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

The Windows PBR - partition boot sector is where Windows has information on the partition size that must match partition table and which boot loader to use ntldr for XP or bootmgr for Vista/7.

---

### Post by HolgerBurghardt on 2012-11-03
Thank you both.

Using both steps described in this thread...

**1. Installing grub to the MBR** using [FONT=Courier New]sudo grub-install /dev/sda[/FONT] in the Linux terminal
**2. Fixing the boot sector of the Windows partition** using [FONT=Courier New]fixboot[/FONT] in the Windows recovery console

Now, after chosing Windows in grub, the OS started finally again. It run chkdsk (twice in my case, so it might do it several times) before finally starting Windows without problems.

So, the problem is solved!

What I'd like to know (also for the benefit of other readers of this thread) is why it happened and how to do prevent that from happening from the start.

I couldn't find a fully illustrated (K)Ubuntu 12.04 installation guide with manual partition mode, the closest I found is on the German ubuntuusers.de wiki: [Kubuntu Installation]("http://wiki.ubuntuusers.de/Kubuntu_Installation").

I did pretty much the same as depicted on the screenshots except that I did not chose a Home and Swap drives and that I chose Ext4 as my file system. It did not ask (as far as I remember) the place where I'd want to install grub to.

Maybe someone can see where a possible source of the problem lies. And finally, while this isn't part of this thread anymore, is it possible to add Home and Swap partitions later on?

Here for checking and comparison is my final bootinfo: [http://paste.ubuntu.com/1328834/](http://paste.ubuntu.com/1328834/)

Thank you.

---

### Post by darkod on 2012-11-03
The Prepare Partitions screenshot in that guide actually hides the option because the Edit Partition window is opened above it.

In the manual partitioning screen, where you setup your partitions, below the list of partitions is the drop down box to select bootloader destination.

By the looks of the original bootinfo, grub2 got installed on sda1 instead of /dev/sda (the MBR). What I am confused about is that you say you never selected anything about the bootloader, and the default value in the drop down would be /dev/sda. So maybe you did change it to sda1 thinking it's asking about the default windows partition.

Otherwise there is no specific question about the bootloader, only that drop down field below the partitions list. Next time you install watch out for it.

---

### Post by HolgerBurghardt on 2012-11-03
Okay, I will, and thank you very much! :popcorn:

---

