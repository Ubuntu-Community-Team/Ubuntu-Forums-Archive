---
title: "&quot;error: no such device : &lt;long hex string&gt;&quot; and the grub rescue prompt."
date: 2014-06-17
forum: Installation &amp; Upgrades
---

### Post by Timothy Taylor on 2014-06-17
I had a dual-boot system with the 10.04 LTS and WinXP (both now dead).

I ran the installation from a USB pendrive, initially choosing the "preserve my folders, files and installed applications" option.  This seemed to install fine, but gave "error: no such device : <long hex string>" and the grub rescue prompt.

I repeated the install process, this time choosing to quick-format my HDD and reinstall everything from scratch.
I've just re-booted my PC after this and get the same error and grub rescue prompt.

If I boot off the USB drive, Ubuntu loads OK and I can see the newly written folders & files on my HDD together with my other WinXP HDD.

What am I supposed to do now?
Even Windows doesn't throw this kind of ****...
:mad:

---

### Post by Bucky Ball on 2014-06-17
*Thread moved to **Installation & Upgrades**.*

Please post new threads with descriptive titles in the appropriate forum rather than hijacking other threads. Also, the thread you posted on originally has been moved to a non-support area as the poster wasn't asking for support. Thanks and good luck.

---

### Post by yancek on 2014-06-17
You have xp and Ubuntu 10.04 and are trying to install what??  Newer Ubuntu?  The hex string you are referring to is the UUID which you can obtain by opening a terminal and typing:  sudo blkid and then compare it to whichever device it was referring to.  What exactly are your intentions, your final goal?

---

### Post by Bucky Ball on 2014-06-17
[QUOTE=yancek]You have xp and Ubuntu 10.04 and are trying to install what??[/QUOTE]

^^^
This. If you are trying to reinstall 10.04 LTS it has reached end of life and is no longer supported. Please refer to the link below and upgrade to a supported release, 12.04 LTS or 14.04 LTS advisable, if that's not what you're currently doing.. 

EOL link:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

If you already are attempting to install a supported version, perhaps try Boot Repair and post a link to the bootinfoscript you create here if that doesn't fix. 

Get Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

### Post by Timothy Taylor on 2014-06-17
I should've been more specific - I'm trying to install 14.04 LTS.

Yes, I downloaded Boot-Repair, burned that onto a pendrive and rebooted to sort that little problem out.
If I wasn't an engineer and I didn't have a spare computer with net access, I'd be absolutely ****ed.  How are ordinary folk supposed to cope with **** like this?

I'm still in the process of trying to get files and software restored and my PC set up to something like I had before.
Thankfully I found the MATE desktop, so I have a system I can still use.

All this grief explains why I was still using 10.04: it - worked - and I didn't want to waste days beating my head against arty-farty rubbish, trying to coax it to do what 10.04 could do easily before.

As it is, I've already spent a day mucking around with this and I can see it being the end of the week before I have everything sorted.

:(

---

### Post by Timothy Taylor on 2014-06-17
I thought I'd almost cracked it: I had Evolution and J-Pilot re-installed, almost ready to sync with my Palm PDA...

Except now I cant get J-Pilot to talk to my PDA because the "PalmOS Devices" gnome-pilot conduits have been removed from Software Centre.

So that's it - I'm completely stopped.
Am I now supposed to buy a new PDA / phone / tablet, endure all the associated learning curve grief, all because 10.04 was declared "end-of-life", crucial packages removed from the repository and my working system killed by an update I never asked for.

---

### Post by Bucky Ball on 2014-06-17
> **Timothy Taylor said:**
> 
Except now I cant get J-Pilot to talk to my PDA because the "PalmOS Devices" gnome-pilot conduits have been removed from Software Centre.



So we're now presuming you have 14.04 LTS installed and everything is running except for the PDA issue? If so, please post a new thread with a descriptive title and address that problem as it has nothing to do with the title of this thread or why it was originally started. Thanks.

---

