---
title: "Need advice on what order to install things :S"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by lsk3993 on 2009-11-28
At the moment I am running Windows XP 32bit dual booted with Ubuntu via Wubi. 
I have 4Gb of RAM and I think this is making XP unstable since it isn't 64bit and so it doesn't use the whole 4Gb.

As much as it pains me to say it, it looks like I'm going to have to use Windows 7 soon because I've been told XP 64bit isn't too good either and I won't even consider using Vista.

I want to install Ubuntu properly using partitions too but have no idea how to do so. I have the Karmic LiveCd but I wasn't sure which option to choose in the partition manager and whether I should wait until I get Win7 before I install it.

I also have things on both Ubuntu and xp that I want to back up. What do I do? (noob standard explanation needed)

Thanks in advance and hopefully my problem makes sense

---

### Post by phillw on 2009-11-28
> **lsk3993 said:**
> At the moment I am running Windows XP 32bit dual booted with Ubuntu via Wubi. 
I have 4Gb of RAM and I think this is making XP unstable since it isn't 64bit and so it doesn't use the whole 4Gb.

As much as it pains me to say it, it looks like I'm going to have to use Windows 7 soon because I've been told XP 64bit isn't too good either and I won't even consider using Vista.

I want to install Ubuntu properly using partitions too but have no idea how to do so. I have the Karmic LiveCd but I wasn't sure which option to choose in the partition manager and whether I should wait until I get Win7 before I install it.

I also have things on both Ubuntu and xp that I want to back up. What do I do? (noob standard explanation needed)

Thanks in advance and hopefully my problem makes sense


A great set of tutorials to hold your hand & explain about partitioning can be found here -->  [http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)


Basically ?.... follow the instructions to the point of putting in the LiveCD and then follow the LiveCD

/edit -- for backing stuff up - I'd need to know a bit more about your computer.  As you have 4GB of RAM - You'll need a 4GB swap area. Yes, you can use smaller -- but it's really advised.
Knowing if you have a 64 bit processor would also help

Regards,

Phill.

---

### Post by lsk3993 on 2009-11-28
> **phillw said:**
> A great set of tutorials to hold your hand & explain about partitioning can be found here -->  [http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)


Basically ?.... follow the instructions to the point of putting in the LiveCD and then follow the LiveCD

/edit -- for backing stuff up - I'd need to know a bit more about your computer.  As you have 4GB of RAM - You'll need a 4GB swap area. Yes, you can use smaller -- but it's really advised.
Knowing if you have a 64 bit processor would also help

Regards,

Phill.
The problem is I don't know which option to choose from the LiveCD...
And 4GB swap area? What does that mean?
Anyway, I have a 3.2GHz Phenom II X4 955 BE

---

### Post by darkod on 2009-11-28
For the backup, probably external usb hdd is the best option. Just copy everything you need from both windows and wubi.

For the dual boot, if you decide to remain with XP for a while, boot the computer with the ubuntu cd and select Try Ubuntu. Then go in System -> Administration -> Gparted and use Gparted to shrink the XP partition. Depending how much space you want to keep for XP and how much for Ubuntu, shrink it according to that. If you are not too use about the partition sizes, Gparted will show you the partitions you already have.

Next: boot XP few times, let it do any disk checks if it asks, see if it's working fine.

Next: How do you want to install Ubuntu depends on you. There are many tutorials to read to undestand Ubuntu better. You don't need too much knowledge to set up partitions manually. If you don't feel like doing that, you can always instruct Ubuntu to use the Use Largest Continuos Free Space option, and it will use the unpartitioned free space you created with shrinking XP partition.

---

### Post by lsk3993 on 2009-11-28
Ok... I now have Windows 7 in a partition and XP in another with Ubuntu as a "program" within it.
I intend to backup everything from XP by simple drag and drop to an external HD.
Just need to get into Ubuntu now to backup the files from there.

Next I'll format the XP partition and simply install Ubuntu in there. That's ok isn't it?

---

### Post by darkod on 2009-11-28
Formatting your XP partition from win7 will not help. You will need todelete that partition to create unpartitioned space for ubuntu.
Finish the backup and then probably easiest is to start win7 and delete the XP partition in Disk Management. Do not create any partition in that space, not from windows.
Then boot with ubuntu CD and either create manually the partitions for ubuntu or let it use the empty space. Your choice.

PS. Also if Win7 added XP to the windows bootloader you might need to sort it out later. By installing ubuntu grub2 will overwrite windows bootloader anyway, and by that time XP will be gone, so it might not matter.

---

### Post by phillw on 2009-11-28
When u delete your XP area - Make sure Win is happy to boot - it may want to do a file system check (or several) - When you're installing Ubuntu it should ask you the size of swap, tell it that you want 4GB.

Regards,

Phill.

---

### Post by oldfred on 2009-11-28
Win7 installed its boot loader into the XP partition and as soon as you delete the Win7 partition you will not be able to boot win7. I also hope you installed Win7 in a primary partition, If not you will never get it to work, it only works now if it is in a logical partition is because it boots via the XP partition. That has nothing to do with Ubuntu but is just the way windows is.

You should delete the XP partition but before you install Ubuntu run the repair from the Win7 disk to get it working again, It will save a lot of grief later. Once Win7 boots ok then go back and install Ubuntu.

Vista (and win7) copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing]("http://members.iinet.net/%7Eherman546/p15.html#BOOTMGR_is_missing")
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

---

### Post by lsk3993 on 2009-11-29
Sorry I'm really confused... I hope I haven't messed anything up.
Basically I used a partition maker in XP to split my disk in half and then installed Win7 into the newly made partition. I don't understand why simply formatting the XP partition and installing Ubuntu in there from the LiveCD won't work.
I need really basic explanations...
Thanks for the help though

---

### Post by oldfred on 2009-11-29
No you should be fine, unless you have a lot of hidden partitions which some systems have and they consume the available 4 primary partitions or 3 primary and one extended.

When you boot windows you are given a choice for XP or Win7. That choice and some essential boot files from Win7 are in the WinXP partition. So when you delete the XP partition Win7 will not boot and you will blame Ubuntu. Just run the Win7 repairs from the Win7 disk in between the delete of the XP partition and the install of Ubuntu. Otherwise you will still have to run the repair of Win7 which overwrites grub and then you have to reinstall grub. Not the end of the world to reinstall grub there are many instructions on how to do and sometimes when we are reconfiguring our systems we do that anyway.

---

### Post by lsk3993 on 2009-11-30
> **oldfred said:**
> No you should be fine, unless you have a lot of hidden partitions which some systems have and they consume the available 4 primary partitions or 3 primary and one extended.

When you boot windows you are given a choice for XP or Win7. That choice and some essential boot files from Win7 are in the WinXP partition. So when you delete the XP partition Win7 will not boot and you will blame Ubuntu. Just run the Win7 repairs from the Win7 disk in between the delete of the XP partition and the install of Ubuntu. Otherwise you will still have to run the repair of Win7 which overwrites grub and then you have to reinstall grub. Not the end of the world to reinstall grub there are many instructions on how to do and sometimes when we are reconfiguring our systems we do that anyway.
Ah ok, thanks for that.
I think I know what I'm doing now, marking thread as solved

---

