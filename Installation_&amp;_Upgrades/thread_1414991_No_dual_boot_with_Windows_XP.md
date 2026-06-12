---
title: "No dual boot with Windows XP"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by SFB on 2010-02-24
Hi - I hope you might be able to help. For a couple of years I have wanted to use a version of Linux rather than Windows. I currently use XP and regard myself as a reasonably experienced Windows user.  My current system has two SATA HDDs - roughly 500Gb, the 'D' drive,   and 140Gb, the 'C' drive, and I have 1Gb RAM. 

So I decided to try Ubuntu 9.10. I downloaded the installation file, created the disk and ran it live for a time. Then I decided to take the plunge and install properly.

I created free space on the C drive, around 17 Gb, in which to install ubuntu. The installation into 'the highest amount of free space' seemed to go well but when I rebooted I was given no opportunity to select Ubuntu - it booted straight into XP.

So I tried again. This time I chose to 'install them side by side'. Again the installation went well but again, on the reboot, the system went straight into XP.

I guess I must be missing something - can anyone tell me how to install so that I can boot to either XP or Ubuntu?

thanks.

---

### Post by darkod on 2010-02-24
I guess the install was good the first time. The possible issue with more than one disk is that you have to be careful to check where the grub bootloader will go. It probably went on one disk, and you are booting XP from the other. The XP bootloader can't see linux at all, so it acts like it's not there.
Go into BIOS, and make the other disk first in the hdd boot order, and you should see grub straight away.
If you don't like your disks layout after two installs, you can delete one (or both if 2 exist), and make a new install this time watching out for this issue.

If you want, you can follow these instructions to create a very informative results.txt file and you can even post the content here if you like:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by SFB on 2010-02-24
Hi, excellent, Changing the HDD boot priority did the trick.

Many thanks. (i'd like to put "SOLVED" at the top but I don't know how to yet!)

---

### Post by darkod on 2010-02-24
> **SFB said:**
> Hi, excellent, Changing the HDD boot priority did the trick.

Many thanks. (i'd like to put "SOLVED" at the top but I don't know how to yet!)

Cool, glad it worked. Above the first post on any page of the thread, there are Thread Tools. You can mark your threads as solved there.

---

