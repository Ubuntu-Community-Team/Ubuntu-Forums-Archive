---
title: "Install to Hard Drive"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by wmn on 2008-04-15
Install to Hard Drive
I Have: OS Microsoft Windows 98SE W/upgrade to OS Microsoft Windows XP Home Edition Version 5.1.2600 - Shuttle mb - AMD Athlon ~1668 Mhz - HD free space  65GB - Memory 511.48 MB.
I have Ubuntu 7.10 CD Live and ordered external modem for internet connect.

I want:
to install Ubuntu to hard drive. 
Any repercussions by doing so? 
Will Ubuntu automatically provide partition on HD as XP install did with 98? 
I have no problem w/format and reinstall of windows xp if required. Really don't want to format entire drive, but will if I have to.

---

### Post by logos34 on 2008-04-15
Take a look here:
[http://apc.simbient.com.au/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apc.simbient.com.au/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)
[https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo](https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo)

Good luck with the modem.

---

### Post by wmn on 2008-04-17
Next question...
I did get Ubuntu installed on the hard drive. My understanding was that Ubuntu would create a separate partition and retain Win XP. But the Ubuntu install evidentially removed Win XP and it's partition, at least I cannot or do not know how to find it, as only Ubuntu boots up.
Now, how do I now remove ubuntu and reinstall WinXP?  
I now know why you wished me luck on the modem.
 
I have read the forum posts onreinstall of XP,  but they seem piece-meal or relate to dual boot which I do not seem to have. Can I just toss in my Dell restore disk and return it to it's original state?

---

### Post by logos34 on 2008-04-17
Post the oputput of 

sudo fdisk -l

That will show whether windows partition is still there.  Hopefully it is and ubuntu simply didn't detect it/add it to the menu.

Modems are a pain (especially winmodems).  But if yours in an external serial modem you'll have a better chance of getting it working.

---

### Post by wmn on 2008-04-17
Sounds like a good idea. Where do I find "sudo fdisk -1" ?
I did 2-3 searches and nothing sudo comes up.
To simplify for me, perhaps this way as done with Windows starting at desktop: (>=go to)

Click My Computer>Control panel>Administrative Tools> etc> etc>

---

### Post by logos34 on 2008-04-17
Appliations>accessories>terminal.

Type:

**sudo fdisk -l** (small L)

Post you fstab too:

cat /etc/fstab

There should be a line in there for xp.

---

### Post by wmn on 2008-04-18
Applications>Accessories> **No such thing as Terminal**
Tried, Disk Usage Analyzer. Scanned everything there....nothing.

NEXT?
btw.. Do have serial modem, and good thing I have 3 other computers with Win..to contact forum with. :)

---

### Post by logos34 on 2008-04-18
it's gotta be somewhere in your menus.

or press

**alt+F2**

type **gnome-terminal**

---

### Post by wmn on 2008-04-19
4-19-08 06:20 AM
logos34 writes	Re: Install to Hard Drive
it's (terminal) gotta be somewhere in your menus.
or press alt+F2
type... gnome-terminal
Reply:
alt+F2 brought up a search/run menu, typed gnome-terminal.
I got a pop-up stating: "The location or file could not be found (gnome-terminal)"

Are we sure we're working the same page? :) Ubuntu 7.10?
wmn

---

### Post by wmn on 2008-04-19
04-19-08 3:30 pm PDT 
OK logos34, I finally located "terminal" here:
system>preferences>main menu>accessories>terminal  (whew)

Typed in sudo fdisk -l and got:
Disk/dev/sda: 40gb.
255 heads,63 sectors/track,4864cyl
units=cyl of 16065 * 512

Device   boot start    end   blocks       ID    System   
/dev/sdal *     1     4701  37760751     83    linux
/dev/sda2      4702   4864  13092974+     5    extended
/dev/sda5      4702   4864  1309266       82   linux swap/solaris

---

### Post by logos34 on 2008-04-20
Not sure what the deal is here...You said at the top that your HDD has 65 GB free space, but fdisk shows the hard disk as a 40 GB.  If fdiskis correct and you don't have a second one not being detected, then windows is gone.  Linux overwrote the entire disk.

---

### Post by wmn on 2008-04-20
> **logos34 said:**
> Not sure what the deal is here...You said at the top that your HDD has 65 GB free space, but fdisk shows the hard disk as a 40 GB.  If fdiskis correct and you don't have a second one not being detected, then windows is gone.  Linux overwrote the entire disk.

Terribly sorry, I had opted to install Ubuntu on another of my computers at the last moment. 40 GB is correct.  I was unable to locate ,(I have to resort to Windows term) C:\ in Ubuntu . 
I want to thank you though for your assistance.  I believe I found my answer quite simple.
I am told that my Dell XP restore disk will offer to restore the HD(C:\) to one(NTFS) partition for/and reinstall XP. 

I did say , I believe,  "My understanding was that Ubuntu would create a separate partition and retain Win XP. But the Ubuntu install evidentially removed Win XP and it's partition, at least I cannot or do not know how to find it."

In any case, I think , hope , problem solved, and thanks to you I did learn something from this attempt at Linux.

---

### Post by logos34 on 2008-04-20
> **wmn said:**
> Terribly sorry, I had opted to install Ubuntu on another of my computers at the last moment. 40 GB is correct.  I was unable to locate ,(I have to resort to Windows term) C:\ in Ubuntu . 
I want to thank you though for your assistance.  I believe I found my answer quite simple.
I am told that my Dell XP restore disk will offer to restore the HD(C:\) to one(NTFS) partition for/and reinstall XP. 

I did say , I believe,  "My understanding was that Ubuntu would create a separate partition and retain Win XP. But the Ubuntu install evidentially removed Win XP and it's partition, at least I cannot or do not know how to find it."

Good thing you have that Dell restore cd!

Your windows partition is normally safe if you choose the options 'guided install' (which then asks you how much you want to shrink your ntfs partition to make room for linux) or 'use largest continuous free space'.  But something happened and linux ended up using the entire disk.

Good luck to you and enjoy ubuntu!  It's simply the best linux distro.

---

