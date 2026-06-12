---
title: "Dual boot no longer the default for gutsy?"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by GoneSouth on 2007-10-01
Hi Folks,

I installed gutsy beta on my Dell E1505 laptop a few days back. I've had both dapper and feisty running decently on this same laptop at various points in the past. But as it happens, the recent gutsy install was over a clean xp install. 

I was surprised to find that windows xp did not come up as a boot option under grub ?? Especially since at install time, I was asked what % of my hd I wanted to allocation to ubuntu - this lead me to believe it was setting up for dual boot.

Is dual boot windows / ubuntu no longer the default grub configuration? Hopefully I just need to go in an edit the grub menu to pick up xp - I sure hope my xp installation wasn't clobbered.

  - GS

---

### Post by Pumalite on 2007-10-01
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by GoneSouth on 2007-10-02
Solved - my windows xp partition was intact, I just needed to add xp as a boot option in grub.

My question still stands though. Was this a bug, or did the ubuntu install intentionally leave the xp partition intact but not add an xp boot option to grub?

---

### Post by Pumalite on 2007-10-02
I have had no problems.

---

### Post by cmacdonell on 2007-10-02
Installing gutsy from the CD removed Vista from my grub.  I had to add it back manually as well.

Cam

---

### Post by dinub1 on 2007-10-02
> **GoneSouth said:**
> Hi Folks,

I installed gutsy beta on my Dell E1505 laptop a few days back. I've had both dapper and feisty running decently on this same laptop at various points in the past. But as it happens, the recent gutsy install was over a clean xp install. 

I was surprised to find that windows xp did not come up as a boot option under grub ?? Especially since at install time, I was asked what % of my hd I wanted to allocation to ubuntu - this lead me to believe it was setting up for dual boot.

Is dual boot windows / ubuntu no longer the default grub configuration? Hopefully I just need to go in an edit the grub menu to pick up xp - I sure hope my xp installation wasn't clobbered.

  - GS

Nope. I had the same problems. It is there. You just need to configure your /boot//grub/menu.lst file to show the grub multi menu.  I am going into the menu.lst right now to tell you exactly.

in paragraph "hiddenmenu" Comment the line "hiddmenmenu". This is hidden by default in Gutsy, You need to unhide it. By placing an "#" in front of the "hiddenmenu" command will do it. 
If Windows XP menu is not there, you then need to add it to the menu list. 
e.g (mine):

## Windows XP Home
title		Windows XP Home
root		(hd0,1)
makeactive
chainloader	+1

On the "root" line your configiration may vary, on mine is on /dev/hda2 (2nd partition) therefore "root    (hd0,1)". Your may be different.

Then save your boot/grub/menu.lst file and reboot. You will be ble to boot again into the MS Windows.

I hope you did not erase or overwrite the partition with Windows XP. Becuase if you did, then Windows XP is lost.

---

### Post by otaviofcs on 2007-10-02
I've updated by update-manager -d, but everything looks fine. Even the Vista partition...

---

### Post by dinub1 on 2007-10-02
> **otaviofcs said:**
> I've updated by update-manager -d, but everything looks fine. Even the Vista partition...

Then you need to edit your menu.lst file in order to add the paragraph for Vista. Instead of the "title  Windows Home" type "title   VISTA" and then select the correct root where your boot MBR files are typically (hd0, 0 or 1). The other commands should be in place (see my previous post). The save the menu.lst file and reboot. Does this help?

---

