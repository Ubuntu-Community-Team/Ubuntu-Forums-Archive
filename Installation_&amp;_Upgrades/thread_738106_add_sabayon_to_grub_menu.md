---
title: "add sabayon to grub menu"
date: 2008-03-28
forum: Installation &amp; Upgrades
---

### Post by Achetar on 2008-03-28
Okay, I installed sabayon last night without the grub bootloader. Now what do I do to add it to the grub menu? I cannot figure out what I add to menu.lst to run it.

There is a menu.lst in the sabayon install, but it says it's a broken link.

I tried using my old kernel entries and changing the root, but that didn't help, it started to boot, then said it couldn't mount /proc.

I don't have my menu.lst available ATM, but I will post it asap.

My ubuntu install is on hda2 (root) and hda3(home).
I have WinXP installed on hda1
I have Sabayon installed on hda5 (hda4 is an extended partition with hda5 and hda6 beneath it)

---

### Post by wjp.reg on 2008-03-28
```
Title                     Sabayon
Root                      (hdn,n)
chainloader               +1  
```

Is what I use, having installed the any new distro's grub in a separate /boot partition and identified as "Root" above.

---

### Post by Achetar on 2008-03-28
Okay, i told it not to install a bootloader, so i tried to do it. Bad move. Now I can boot sabayon or winxp but not Ubuntu. Should I try to reinstall the Ubuntu grub using an Ubuntu LiveCD?

---

### Post by wjp.reg on 2008-03-28
that may be your best bet, as far as ubuntu is concerned.

---

### Post by confused57 on 2008-03-28
> **Achetar said:**
> Okay, i told it not to install a bootloader, so i tried to do it. Bad move. Now I can boot sabayon or winxp but not Ubuntu. Should I try to reinstall the Ubuntu grub using an Ubuntu LiveCD?
I agree with wjp.reg, reinstall Ubuntu's grub with the live cd, then you might be able to use a configfile entry to boot Sabayon:
```
title  Sabayon
configfile (hd0,4)/boot/grub/grub.conf
```

Here's a guide to booting other linux distros:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---

### Post by zvacet on 2008-03-28
Add to your menu list 

title Sabayon         
rootnoverify (hd0,5)
chainloader +1

**Of course you will replace (hd0,5) with exact partition where Sabayon is.**

---

### Post by Achetar on 2008-03-29
Right now, my Ubuntu distro got pretty much demolished when the rescue failed. I am going to try again. The good side is I still have a working linux install (sabayon). I will try to get this sorted out. I don't want to trade out Ubuntu for Sabayon!

I am going to download the latest hardy LiveCD to attempt to fix it.

---

