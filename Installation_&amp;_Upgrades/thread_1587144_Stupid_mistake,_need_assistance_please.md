---
title: "Stupid mistake, need assistance please"
date: 2010-10-03
forum: Installation &amp; Upgrades
---

### Post by aEx155 on 2010-10-03
*[solved]I'm sure I'll have to edit the title to say solved, but whatever, here it is. This thread is my account of the ordeal I went through when I tried to install linux on an old desktop that doesn't like CDs. It's a great read if you like crappy stories about technology failures. Enjoy.*

Hey everyone, I'm new here, so sorry if this sounds really dumb:

I have an old Dell desktop computer that I wanted to install linux onto and be able to dual boot with WinXP. I've run into so many problems I registered and came here for help.

(skip down for the actual problem unless you want to read through my story)

- - - - - Background - - - - -

I downloaded the 10.04.1 iso from the main downloaded page and burned it with brasero on my laptop, and used that to try and install. Unfortunately, both its CD and DVD drive are really sketchy, so it stopped about 1/4 through giving some kind of "Input /output error". The message said something about burning a new disk so I did that, and got a slightly different result: It booted up into some kind of text interface, and I think the prompt said "(initramfs)" or something, not what I was hoping for.

*(Before I go any further, let me just say that, it was a real lottery getting the LiveCD to boot into linux correctly, and that was with a 15 min wait time each try, with a power cycle in between each time...)*

I even tried using a USB drive, with the Universal USB installer program from Pendrive linux: the computer recognizes that something's different when the USB drive is inserted, but it never does anyhitng after I select "Boot from USB"

Eventually I ended up looking up how to install Ubuntu without burning a CD, and got [this]("http://ubuntuforums.org/showthread.php?t=28948") page. I had a lot of trouble with that just because of Windows compressing the files, and directories and all that other stuff, but I eventually got it working.

I restarted, and got a nice text installer. Unfortunately, I'm horrible with text installers. I believe I went through, and accidentally hit enter at one point, and I never installed any desktop environments.

When I started into linux the first time I was disappointed to end up with a text environment. Like I said, I was horrible with text environments, and at the time, I didn't know how to install one from whichever place it is (and I still don't). So, I started up the LiveCD again and used gparted to delete the linux installation I had just installed, planning to just try again and not skip the desktop environment option.

Guess what happened when I booted up my computer without the CD in it.

Grub didn't like having an entire partition missing:"partition not found"

- - - - - Actual Problem - - - - -

I ended up a "grub rescue>" prompt that didn't recognize "help" as a command, and a hard drive full of XP that needed to work.

What I'm trying to do is a)get rid of GRUB or b)put back the linux partition and the data associated with making GRUB work

The only LiveCDs I have to work with are the two I burned.

a)I have tried running (from the LiveCD) "sudo dd if=/dev/null of=/dev/sda bs=446 count=1" to no effect. (I stuck sudo in there as it didn't have permission without it)

b)The install from LiveCD still stops at the same point with the same error. The installation continued enough to make the partitions in the unallocated space, so now grub gives "file missing" (or something to that effect).

The unfortunate thing is the fact that the only way I currently have to install linux is to get back into windows, but to do that I need to install linux again, and so on...

- - - - - - - - - -

It's sometime around midnight and I'm in need of a lot of help, so thank you in advance to anyone who can instruct me on fixing this.

- - - - - Epilogue - - - - -

An ending to come soon. I need some sleep.

---

### Post by krishnandu.sarkar on 2010-10-03
First repair windows by putting in the windows cd and booting from it. Go to recovery console and use fixboot and fixmbr. These two commands would bring back your XP to normal. Then burn the ISO and install Ubuntu.

Well you should burn the ISO at 8x.

---

### Post by aEx155 on 2010-10-03
> **krishnandu.sarkar said:**
> First repair windows by putting in the windows cd and booting from it. Go to recovery console and use fixboot and fixmbr. These two commands would bring back your XP to normal. Then burn the ISO and install Ubuntu.

Well you should burn the ISO at 8x.

> The only LiveCDs I have to work with are the two I burned.

I don't have the original Windows CDs.

The problem is with the drive, not the CDs.

---

### Post by krishnandu.sarkar on 2010-10-03
Ohh so can't you get it from friends..?? Well in that case try this link to recover grub [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by sikander3786 on 2010-10-03
> **aEx155 said:**
> I don't have the original Windows CDs.

The problem is with the drive, not the CDs.
So you don't have a Windows Disc, Ubuntu Live CDs don't work, infact the CD Drive doesn't work. The USB flash drive doesn't seem to boot. And you are stuck at the Grub > prompt. Right?

You have got access to your Laptop with UNR?

---

### Post by aEx155 on 2010-10-03
> **sikander3786 said:**
> So you don't have a Windows Disc, Ubuntu Live CDs don't work, infact the CD Drive doesn't work. The USB flash drive doesn't seem to boot. And you are stuck at the Grub > prompt. Right?

You have got access to your Laptop with UNR?

I have access to a laptop with WinVista and Linux Mint. (I also have a few external hard drives laying around, with maybe 10-20 GB free space if needed to transfer files)

The LiveCDs will boot into Ubuntu, but getting them to do so without being temperamental is hit or miss. It's gotten better since I opened up the drive and gave it some TLC with an air duster, though. Installation throws an I/O error 1/4 way through.

I have a Vista Disc, will that work?

---

### Post by aEx155 on 2010-10-03
Update: I'm not sure what caused it (most likely after trying "sudo dd if=/dev/null of=/dev/sda bs=446 count=1"), but Ubuntu/Disk Util is no longer recognizing the main WinXP partition as a mountable partition. gparted still recognizes it as NTFS.

---

### Post by sikander3786 on 2010-10-03
> **aEx155 said:**
> I have access to a laptop with WinVista and Linux Mint. (I also have a few external hard drives laying around, with maybe 10-20 GB free space if needed to transfer files)

The LiveCDs will boot into Ubuntu, but getting them to do so without being temperamental is hit or miss. It's gotten better since I opened up the drive and gave it some TLC with an air duster, though. Installation throws an I/O error 1/4 way through.

I have a Vista Disc, will that work?
Have you got the Ubutnu .iso image on your netbook? If yes, first of all check the MD5SUM.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the hashes match, burn it to the USB drive and use unetbootin this time.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

You can continue the installation of Ubuntu and once it is successful, you will be dual booting XP and Ubuntu. If you don't want to install Ubuntu for now, just want to restore Windows, follow the following link and install Grub. You will need to boot into the Live USB.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


[COLOR="Red"]**EDIT:**[/COLOR]

> I have a Vista Disc, will that work?

If your CD Drive is out of order, I won't recommend that.

---

### Post by aEx155 on 2010-10-03
> **sikander3786 said:**
> If the hashes match, burn it to the USB drive and use unetbootin this time. ... You will need to boot into the Live USB.


If your CD Drive is out of order, I won't recommend that.

My computer won't boot from USB; I've already tried it multiple times.

My drive throws an I/O error for installation but doesn't fail when just running as LiveCD. Is using the WinVistaCD it an option?

---

### Post by sikander3786 on 2010-10-03
> **aEx155 said:**
> My computer won't boot from USB; I've already tried it multiple times.

My drive throws an I/O error for installation but doesn't fail when just running as LiveCD. Is using the WinVistaCD it an option?

_IF YOU ARE SEEING THIS MESSAGE I AM STILL CHECKING THIS THREAD EVERY 5 MINUTES_
The error your USB was throwing could just be caused by the program you used to create the Live USB, Thats why I suggested unetbooting. There is nothing wrong in giving it a go.

Google for restoring XP bootloader from Vista disc. Actually I don't know. I am also doing a bit of research. Will let you know if I find anything.

---

### Post by aEx155 on 2010-10-03
> **sikander3786 said:**
> The error your USB was throwing could just be caused by the program you used to create the Live USB, Thats why I suggested unetbooting. There is nothing wrong in giving it a go.

Google for restoring XP bootloader from Vista disc. Actually I don't know. I am also doing a bit of research. Will let you know if I find anything.

My USB drive wasn't throwing any errors; the computer fails to do anything after I select USB device in the boot menu. I will give unetbootin a try.

My big fear is that whatever the VistaCD sets the MBR to will be Vista-specific and non-compatible with XP...

---

### Post by sikander3786 on 2010-10-03
> My big fear is that whatever the VistaCD sets the MBR to will be Vista-specific and non-compatible with XP...

I hope the same from Vista.

---

### Post by mdflynn on 2010-10-03
> **aEx155 said:**
> Update: I'm not sure what caused it (most likely after trying "sudo dd if=/dev/null of=/dev/sda bs=446 count=1"), but Ubuntu/Disk Util is no longer recognizing the main WinXP partition as a mountable partition. gparted still recognizes it as NTFS.

This is most likely caused by the partition not unmounting cleanly, there are tools that can fix this within a linux environment and it is possible to force it to mount but the best approach is to just use chkdsk on windows.

If you have a spare computer and bandwidth you might consider doing a network boot and install [http://ubuntuforums.org/showthread.php?t=327597]("http://ubuntuforums.org/showthread.php?t=327597")

---

### Post by aEx155 on 2010-10-03
I did some digging around the various cabinets in my house (not easy to do if you don't want to wake anyone at 1 AM) and I found my WinXPCD. Will post back after I try fixmbr and fixboot.

---

### Post by lkraemer on 2010-10-03
**SUPERGRUB:**
[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)

**DUAL BOOT:**
[http://members.iinet.net.au/~herman546/](http://members.iinet.net.au/~herman546/)

**HOWTO: Create a Bootable SETUPCD From a Windows Pre-Installed System:**
[http://www.howtohaven.com/system/createwindowssetupdisk.shtml](http://www.howtohaven.com/system/createwindowssetupdisk.shtml)

**HOW TO: create a bootable XP SP3 CD:**
[http://apcmag.com/how_to_create_a_bootable_xp_sp3_cd.htm](http://apcmag.com/how_to_create_a_bootable_xp_sp3_cd.htm)

**How to dual boot Windows XP and Linux (XP installed first):**
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Why don't you download the SuperGrub LiveCD, and use it to repair the 
Master Boot Record of XP.  I'd suggest using the Super Grub Disk 0.9799
and be sure to Burn it as Disk at Once (DAO) and at 4x or whatever is the
slowest speed on your Burner.

You also should burn your Ubuntu LiveCD's as DAO and at 4x or the slowest speed.
Plus, Always check the MD5SUM of the Downloaded file against the MD5SUM or
SHA256 hash code of your download.

Once XP's MBR is repaired, you should be back to a working system, then
I'd suggest making a CD so you can rebuild the pre-installed system.

Last thing to do is install Ubuntu, when you have a way to rebuild.....

For dual booting, read Herman's Info..... and there are two good articles
by APC Magazine, as referenced above...

lk

---

### Post by aEx155 on 2010-10-03
> **lkraemer said:**
> **SUPERGRUB:**Why don't you download the SuperGrub LiveCD, and use it to repair the 
Master Boot Record of XP.  I'd suggest using the Super Grub Disk 0.9799
and be sure to Burn it as Disk at Once (DAO) and at 4x or whatever is the
slowest speed on your Burner.

You also should burn your Ubuntu LiveCD's as DAO and at 4x or the slowest speed.  Plus, Always check the MD5SUM of the Downloaded file against the
MD5SUM or SHA256 hash code of your download.

Once XP's MBR is repaired, you should be back to a working system.

lk

I tried the slower burn when I burned my second CD. Didn't work, and I ran out of CDs. Normally I would use DVDs but the drive on my desktop won't boot off of them.

I found my WinXP CD, and was able to run fixmbr. GRUB is now gone. BIOS isn't detecting XP though. Most likely because of the non-mounting error that I talked about earlier. Or, the partition table was destroyed by fixmbr. I don't know.

New plans of action:

a)use gparted to make the main partition bootable and see if I can boot then

b)use linux to transfer files to external drives and reinstall XP

The problem I see with both of these is that it's not coming up as a mountable drive. The data is intact but the fact that it's missing 446 blocks of something in the beginning is throwing off everything. No mount = no data transfer.

Thanks to all who have helped so far.

---

### Post by lkraemer on 2010-10-03
OK, Hang on......Let me find the repair install Info I have bookmarked.
I'll update this post at that time.

Here is the first post:
[http://ubuntuforums.org/showthread.php?p=5082723#post5082723](http://ubuntuforums.org/showthread.php?p=5082723#post5082723)

Here is a second site on making a REPAIR INSTALL:
[http://michaelstevenstech.com/XPrepairinstall.htm](http://michaelstevenstech.com/XPrepairinstall.htm)

Third site - Repairing XP with 8 Commands:
[http://tech.icrontic.com/articles/repair_windows_xp/](http://tech.icrontic.com/articles/repair_windows_xp/)

Read those sites SLOWLY, then proceed with caution.  If you pick
the incorrect route, you won't be able to keep from blowing away
your install and start from scratch.

lk

---

### Post by aEx155 on 2010-10-03
> **lkraemer said:**
> OK, Hang on......Let me find the repair install Info I have bookmarked.
I'll update this post at that time.

Here is the first post:
[http://ubuntuforums.org/showthread.php?p=5082723#post5082723](http://ubuntuforums.org/showthread.php?p=5082723#post5082723)

Here is a second site on making a REPAIR INSTALL:
[http://michaelstevenstech.com/XPrepairinstall.htm](http://michaelstevenstech.com/XPrepairinstall.htm)

lk

> Step 1) Boot into Ubuntu and mount the XP partition.

My XP partition isn't mounting in Ubuntu.

---

### Post by lkraemer on 2010-10-03
Yes, I understand, but read SLOWLY, and keep reading until you get to:
**Detailed Instructions:**
where you will manually try to mount it from a Terminal Console.
If it mounts manually, then you are on your way.  If it doesn't mount,
you must do more reading on the other postings......

It may not mount automatically, but it may manually.  Or there is one
URL that tells about rebuilding the boot sector with testdisk.  Just don't
overwrite anything or WRITE ANYTHING on the Windows Partition unless you
know exactly what you are doing.
 
In fact, go to all the URL's and read through each trying to locate the 
best case, or method that exactly fits your situation.

One method should stick out at you......

Don't just pick the first method and proceed blindly......

OH, and keep updating the page as I keep adding info:

lk

---

### Post by lkraemer on 2010-10-03
It looks to me as if you need to mount the partition, if possible,
then use:
**Step 5: Rebuild the Boot sector of the Windows partition.**
from the first URL.

lk

---

### Post by aEx155 on 2010-10-03
Just tried making a USB drive using unetbootin: didn't work, as expected.

Currently just trying to get my LiveCD to work correctly. 2:12AM right now, hoping to get some good result by 3.

Thanks for all the help.

---

### Post by aEx155 on 2010-10-03
LiveCD is working again, for now.

plan C-
first:
sudo fdisk -l
returns:
dev/sda1 ... Dell Utility
dev/sda2 ... HPFS/NTFS

then:
sudo mount /dev/sda2
returns:
mount: cant find /dev/sda2 in /etc/fstab or /etc/mtab

did plan A: used gparted to set the boot flag on XP partition

---

### Post by lkraemer on 2010-10-03
I'm afraid I've run out of suggestions.......just proceed with caution.
You should be able to rebuild your system, and make it bootable with the
information you now have.  Just read everything first.......then proceed
slowly, logically, and with caution.

Good Luck.

lk

---

### Post by sikander3786 on 2010-10-03
You need to specify the mount point.

```
sudo mount /dev/sda2 /mnt
```

Are you planning to reinstall Grub2?

---

### Post by aEx155 on 2010-10-03
> **lkraemer said:**
> I'm afraid I've run out of suggestions.......just proceed with caution.
You should be able to rebuild your system, and make it bootable with the
information you now have.  Just read everything first.......then proceed
slowly, logically, and with caution.

Good Luck.

lk

My luck seems to have run out. The fact that linux can't mount the XP partition means that Windows can't either, and so, I am going to try an alternate approach: bootcfg

Thank you for sticking with my through this.

---

### Post by lkraemer on 2010-10-03
Are you sure you can't mount the partition?
Open a Terminal Console:
```

cd /
cd /mnt
sudo mkdir mywin
sudo mount /dev/sda2 /mnt/mywin

```
Then when you are finished:
```

sudo umount /mnt/mywin
cd /
cd /mnt
sudo rmdir mywin
exit

```

lk

---

### Post by aEx155 on 2010-10-03
Scratch that about my luck running out; A MIRACLE HAS JUST HAPPENED!

In my previous post I said I would try bootcfg; unfortunately, it would not recognize my XP partition, and I really thought I was going to have to do a complete re-installation.

Good thing I had an idea.  

Originally when I posted about trying fixmbr and fixboot, I was able to remove GRUB with fixmbr but fixboot would not run.

I'm assuming my change with gparted to make my XP partition have the bootflag changed that, as when I tried fixmbr and fixboot again, both executed perfectly.

I am now back into Windows, which may seem weird on an Ubuntu forum, but is a wonderful thing as this is a family computer that also acts as an XP print server.

It is hard to express my gratitude towards lkraemer; your links and comments helped me through this and I really wish I could pay you back in some way. Thank you so much.

Tomorrow (which is actually today) I will append an epilogue to my story in my first post, to finish up my story. I hope maybe the makers/users of Ubuntu will use this thread as a learning tool to inform users trying Ubuntu, or those who find themselves in the same predicament as me.

So everyone, I bid a final good night/morning and again, thank you.

---

### Post by lkraemer on 2010-10-03
GREAT!  

Your payback is to HELP Others here on the Forum.  ie.  Pay it Forward...

lk

---

### Post by DeanG on 2010-11-23
I have a problem that is real close to what is being discussed here but I am so new to the forum business that I don't know if this is the place to post the question. If it isn't someone please stomp on me and point me in the right direction

---

### Post by sikander3786 on 2010-11-24
> **DeanG said:**
> I have a problem that is real close to what is being discussed here but I am so new to the forum business that I don't know if this is the place to post the question. If it isn't someone please stomp on me and point me in the right direction
Go to the Installations & Upgrades sub-forum and start a new thread. Give as many information as possible and we'll catch up there ;-)

Good Luck!

---

