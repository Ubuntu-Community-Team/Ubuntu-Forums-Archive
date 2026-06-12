---
title: "passwords don't match .... match what???"
date: 2012-09-21
forum: Installation &amp; Upgrades
---

### Post by jemvyc on 2012-09-21
I have a new laptop running windows 7.  I am trying to install Ubuntu 12.04LTS.  I chose the install alongside windows option. 
The system restarts windows and the install Ubuntu box appears.  Username is already selected to match windows username.  It needs a password to continue.  I put in everything I can think of.  The response is "passwords don't match"  On my first attempt windows did not have a password.  I went back and put in a windows password.  Still I get the same result.  All it does is hang on "passwords dont match" no matter what.


BTW I saw a post which seemed like this and the response was that it wants you to put in a password in and then put in the confirm password.  There is no confirm password space in the install Ubuntu box!


How do I get this to run?

Thanks

---

### Post by darkod on 2012-09-21
That doesn't sound like the ubuntu installer at all. In fact it sounds very weird.

The linux OS doesn't care about the windows username, why would it make it to match automatically?

Try to boot with the cd and see if it works in live mode first (Try Ubuntu). If that works OK on your hardware you can do the install. If your whole hdd is taken by windows make sure you shrink one of the partitions first to make unallocated space for ubuntu. Do this with Disk Management in windows, don't let the ubuntu installer do it.
Also make sure you already don't have all 4 primary partitions used. That's the maximum on msdos disks.

If the cd doesn't work OK in live mode, it might have been corrupted during download or burning. Try to burn another cd at low speed (8x or 10x) or even do a new download.

One thing is for sure: in dual boot setup the OSs don't care about each other too much, so anything you see that appears like one of them is trying to match any username to the other OS, should not happen. You should be able to select the username you want to use.

---

### Post by JKyleOKC on 2012-09-21
You asked "match what?" and the answer is "match each other." The purpose of making you type it in twice is to prevent you from having a wrong letter in it. I've done that in the past, hitting a "d" instead of an "s" BOTH times and then later wondering why my password to that web site did not work. Only when I examined it in my browser's password file (where I had stored it automatically the first time I logged into the site) showed me what I had done.

However, in general having you type it twice cuts way down on such errors.

As for automatically filling in a user ID for you, did it put in your first name? Last time I installed a *buntu package, it asked me for my full name and then used my first name, converted to lower case, as its suggested user ID (which I changed immediately).

---

### Post by jemvyc on 2012-09-21
I don't think these replies have encountered the Ubuntu 12.04 LTS install options on a system with windows 7 installed.  There are 3 options presented.  Install alongside windows, take over the whole disk, and other.  Other is the old standard where you individually select partitions to use and boot with grub.

I don't want to switch the whole computer to ubuntu and repartitioning a windows 7 hard drive is very dangerous.  I chose the install alongside windows option and the installer puts a little program in windows startup which puts up a ubuntu install panel.  In that panel are username and ONE password entry space.  Every password I have entered results in "passwords don't match"  There is no place to enter a second try at a password.  Thus my question "match what?"

---

### Post by darkod on 2012-09-21
You are wrong. Install along win7 means exactly that, it will resize (shrink) the win7 partition to make space for ubuntu and install it on separate partition along side windows. Repartitioning a windows drive is not more dangerous than any repartitioning. Why would you think that?

In fact, what is more dangerous is using the ubuntu installer to resize the win7 partition because win7 sometimes doesn't like other tools touching its system partition. Hence the advice to do it in windows Disk Management which is its own tool.

And just for information, the third option, Something Else, is not "the old way" but is the manual install option which is always preferred since it gives you best control over what goes where.

I am not sure if you have in mind a wubi install inside windows, but the proper ubuntu installer never puts a small program on the disk. Where will the OS be running from if only a small program is put on the disk?
The cd is usually used to install the OS, not to just put small programs that will then start the installer. The installer already starts by booting with the cd if you select the Install Ubuntu option.

---

### Post by Petro Dawg on 2012-09-21
> **jemvyc said:**
> I don't think these replies have encountered the Ubuntu 12.04 LTS install options on a system with windows 7 installed.  There are 3 options presented.  Install alongside windows, take over the whole disk, and other.  Other is the old standard where you individually select partitions to use and boot with grub.

I don't want to switch the whole computer to ubuntu and repartitioning a windows 7 hard drive is very dangerous.  I chose the install alongside windows option and the installer puts a little program in windows startup which puts up a ubuntu install panel.  In that panel are username and ONE password entry space.  Every password I have entered results in "passwords don't match"  There is no place to enter a second try at a password.  Thus my question "match what?"

Ok, so you are dealing with the Wubi installer, does the message box look anything like this one...

[ATTACH]224508[/ATTACH]

or does it look like this one...

[ATTACH]224507[/ATTACH]

or does it look different than either of those?

---

### Post by jemvyc on 2012-09-21
It's the one on top.  Six boxes, what disk drive, how much hd space, which ubuntu, language, username (already filled in with the windows username), and password.

---

### Post by Petro Dawg on 2012-09-21
> **jemvyc said:**
> It's the one on top.  Six boxes, what disk drive, how much hd space, which ubuntu, language, username (already filled in with the windows username), and password.

Its possible that your wubi installer download was corrupted if the two password fields do not appear.

The first thing I would try to do...

While running windows click this link ([http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)) and try to download the executable installer program directly from the Wubi site.  Don't bother with using any installation disks (remove any from the computer if you have not already) as it appears you may have an issue with the one you have.

If you have any problems or encounter the same results using this installation method, then let us know.

---

### Post by jemvyc on 2012-09-21
It is fixed.  I'm not sure why, but with your help it is fixed.  I'll mark the thread solved.

---

### Post by BlinkinCat on 2012-09-21
> **jemvyc said:**
> It is fixed.  I'm not sure why, but with your help it is fixed.  I'll mark the thread solved.

You can mark thread as solved using thread tools on top of page - :p

---

### Post by jemvyc on 2012-09-21
I now have a dual boot system with Windows 7 and Ubuntu 12.04.  It does not look like I have broken anything.

My beliefs about Windows 7 and Ubuntu came from a post on this category by pgmer6809.  His "How to Make a Dual Boot Ubuntu Windows 7 Setup" is very thorough and helped me with the trouble I was having to understand the hard drive on my new Windows 7 system.

His comment that doing a Ubuntu install on a computer with Windows 7 preinstalled the way we have all done in the past could wind up with a machine that is unbootable at all gave me pause.

Thanks to all for the help.

---

### Post by Petro Dawg on 2012-09-21
Wubi installation is the way to go (and the way I first started off)  if you are uncomfortable with messing with partitions, but in the long run it is subject to the same fragmentation issues Windows experiences as it is stored in the same partition.  Eventually it may start to run slower.

---

### Post by JKyleOKC on 2012-09-21
> **jemvyc said:**
> His comment that doing a Ubuntu install on a computer with Windows 7 preinstalled the way we have all done in the past could wind up with a machine that is unbootable at all gave me pause.

Thanks to all for the help.While it's remotely possible for that to happen, it's extremely unlikely. What **is** likely, though, is that a bug currently present in the installer itself can lead to a situation that **looks** unfixable.

I ran into it myself earlier this month when I bought a new HP desktop on which I installed a fresh download of 12.04.1, following a how-to I found on another web site. Unfortunately that how-to was unaware of the potential problem, and made it even worse.

The root cause of this problem is that most if not all of the machines currently being sold use the relatively new UEFI-gpt bootloading system, while most of the how-tos and the people giving advice are only aware of the classic MBR Legacy system -- and the two are totally incompatible. When you dual boot, both operating systems installed must use the same bootloading system. And since most Win 7 installations use UEFI, that means the Ubuntu installer must install Ubuntu using UEFI.

The 32-bit versions do not have UEFI, so you must use the 64-bit versions. But that's not the bug. The bug is that the installer often fails to detect that Win7 is using UEFI, and so installs Ubuntu to use MBR Legacy.

The result is that you see only the usual grub menu, and Win 7 is unable to boot.

For full details you can go to [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and learn how to force things to be correct. If you get caught in the problem, you can install Boot-Repair into a session launched from the Live CD (or Live USB) and get it automatically repaired. This repair has worked for every instance of the problem that I have seen reported here, except for one in which the victim was using a RAID array and the repair could not locate a place to put the fix. That one is still being worked on, though, and we've not yet given up hope.

Having been bitten by this I've tried to keep on top of the problem and help those getting hit by it. Hopefully, your wubi installation is solving it for you, and if it works to your satisfaction that's great. However if you decide you want to try a real side-by-side installation later, just yell. You'll find lots of help here.

---

### Post by darkod on 2012-09-22
No, you don't have a dual boot system, it only looks like that. Wubi is in a way virtual ubuntu inside windows, it resides in a file on the ntfs partitions.

And after a while it will start making issues because it was only developed to be a short test, to try it out, not as a long term install. While it can run long time without seeing issues, also they can start happening very soon, especially when doing an upgrade to the next version for example.

When you want to use two OSs, a proper dual boot on their own partitions is always the way to go, not virtual one OS inside the other.

The final decision is always up to you, but you seem too afraid of understanding and partitioning your disk. You need to understand partitioning even when running only one OS, not only for a dual boot. But unfortunately the fact is that Microsoft got used many people to let windows use the whole disk in one single partition, sort of don't think about anything and don't use your head, we'll do everything for you, you don't need to know anything about this.

I always had two partitions in windows, long before I ever discovered linux. That helped me to keep important data on the second and when windows messes up and wants to be reinstalled, I don't lose barely nothing when formatting C: and reinstalling. All data is on the other partition.

I definitely recommend you consider a proper dual boot. Also, these days the built in tool in Disk Management is very good resizing partition, something that didn't exist in XP for example. You had to use a third party software. So resizing to make space for ubuntu is very easy and safe to do now.

---

