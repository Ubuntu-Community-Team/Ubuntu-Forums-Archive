---
title: "Problems with Installation, USB Boot Drive and Boot Priority"
date: 2014-03-16
forum: Installation &amp; Upgrades
---

### Post by claudio7 on 2014-03-16
First time installing Linux. 
I'm trying to install Lubuntu on a old Asus netbook, I can't tell the model right now but it's the classic, plain white netbook with an Intel Atom, running Windows 7.
I downloaded the iso, UNetBootin, flashed a pen drive, made a partition of about 35 gb, and went to install the distro alongside windows 7.
I've had some problems during the boot, even changing the priority into Removable Devices first, it would still load Win7, after some googling I found out that some old PCs see pen drives as HD, so I put HD as top priority in the Boot Priority Menu and changed the main HD to the pen drive. Everything went good, until I wanted to install the OS itself from the "Live" desktop. There was a option that I wasn't aware of: Install Lubuntu alongside Windows 7. I didn't know that was possible, and that the only proper way to keep the two OS in Dual Boot was installing the distro into a manually created fresh partition. I tried it, of course, and the screen would only go black saying that it is terminating all processes before reloading the same Live desktop iwthout actually installing the OS. Sometimes it loaded the Live desktop directly, sometimes it loaded the USB Boot Drive Menu (the one with Help, Try the OS without install, Install the OS, and so on), and even directly choosing Install Lubuntu from the aforementioned menu would do the same thing, black screen, reboot. 
So I tried going old school, I choose Other and it gave me the list of all the partitions in my computer. However, it asked me where to install something called Boot Loader of which I wasn't aware of, and in that drop down menu the 35gb empty partition wasn't even visible! I just turned everything off and went here.
What's the problem? Is it that strange boot priority issue that makes it impossible to install Lubuntu? It's the only way to load the USB Boot Drive, so I really don't know what to think...
Thanks in advance.

---

### Post by claudio7 on 2014-03-17
Bump

---

### Post by ubfan1 on 2014-03-17
First, the standard install will take two partitions, one for root (/) and the other for swap.  Assuming your hard disk has an msdos partition table, you have a limit of four primary partitions.  Unless your Windows and recovery/tools partitions only take two partitions, you will need to make one of the primaries (the empty one you created will be fine) an extended partition.  The extended partition can hold many logical partitions, which Ubuntu is perfectly happy using.  Now the bootloader (grub) should be installed on the hard disk, not a partition, so select the device like /dev/sda, not a partition like sda1.  On reboot of the hard disk, you should be offered a grub menu to choose Ubuntu (default) or Windows.

---

### Post by claudio7 on 2014-03-17
So the bootloader can be freely installed in the default C: location, huh? I thought it was something OS related and installing it in the wrong place would erase Windows. Is the swap space required? I heard it isn't.

And what if I want to stick with that handy default Install alongside Windows 7? Any way to fix that problem I mentioned?

If everything still doesn't work, is Wubi 12.04 recommended?

---

### Post by walterorlin on 2014-03-17
If you need swap may depend on how much ram you have. I have a 4 and a half year old laptop that almost never uses swap even if I have it. The bootloader should be installed to a hard disk as it is at the start of the harddisk that then boots off the different partition. Grub will either start linux off the ext4 partition or it will start the windows loader. Also lubuntu 12.04 is not a long term support realease and is no longer supported.

---

### Post by claudio7 on 2014-03-17
This laptop is old too, it only has 1gb of RAM, so I'll probably think about giving it some swap space. This PC is for my mom, I suffer seeing here struggling with a slowass Win7 that's why I decided to catch two birds with one stone helping her and finally touching some different OS with my hands. Point is, the fact that it is no longer supported isn't an issue.

---

### Post by ubfan1 on 2014-03-17
I always just make my partitions before running install, so I don't know if the installer will recognize an empty extended partition as free space to make logicals (or even if it will make an extended partition in free space if only 3 primary partitions exist).  Wubi will be slow, but I think is still supported for the 12.04 release.  It might be a way to let the user test out the system and see if it's acceptable (other than speed) before committing to a full install.

---

### Post by claudio7 on 2014-03-17
Sorry, but why should it be not acceptable? Again, I'm not looking to some great performance, just something to make browsing easier for my mother. I already tried the Live versione of lubuntu and it runs pretty okay, so why would installing it with wubi cause problems.
I didn't really get the partition part you talked about, it's a bit unclear about what method you're talking about. Wubi doesn't even need an unallocated partition of free space manually created by the user right? It automatically creates it during the installation?

EDIT I'm going to make progress tomorrow, I'm busy today, feel free to post in the meanwhile, 24hrs from now I'll post some results.

---

### Post by Rex Bouwense on 2014-03-17
Wubi will work for Ubuntu 12.04.  It is the last version that it will work for.  However, you have been told that Lubuntu 12.04 is no longer supported.  What that means is no patches are published, no security updates are published.  If you weren't going to get on the Internet, the security updates probably wouldn't be a big problem.  Patches that fix bugs in the system do become a problem unless you are capable of doing work arounds.  Since this is for your mother, I would recommend that you do not use Wubi to install.  Install the current Lubuntu which is 13.10 so that you end up with a true dual boot.  You will be happy with the speed and simplicity.

---

### Post by claudio7 on 2014-03-18
Oh, I guess I'll do it manually then... Still no clue about why the automatic Install alongside Windows 7 doesn't work huh? If I can help with proof or something let me know, because I'm really busy these days and I'd rather not spend a lot of time with the manual installation. Sadly I don't think I can provide screenshots but I can still pull out photos or videos of decent quality with my tablet.

---

