---
title: "First install. Stuck at the boot menu"
date: 2013-03-11
forum: Installation &amp; Upgrades
---

### Post by hobbzilla007 on 2013-03-11
Excuse my ignorance, but I don't consider myself extremely tech savvy. I'm trying to install Ubuntu on a spare laptop and ran into a problem.

When I boot I come to the 'Installer boot menu' consisting of-

Run Ubuntu from this USB
Install Ubuntu on a Hard Disk
Test memory
Boot from first hard disk
Advanced options [ nothing under this ]
Help

When I select either run or install the boot menu flashes and returns and nothing happens. I've seen help suggesting the f6 option but this does nothing. I do however have a option to select tab and a small amount of code appears on the bottom of the screen. I'm pretty much lost from here.

Again, excuse my ignorance as I know many will read this and just be frustrated I'm polluting the forum. 

Any help is much appreciated and I hope I posted this in the right section. I thought I would receive more help here than in the newbie forum.

Also, I am not really concerned about keeping my windows os that is currently installed if that makes a difference.


[SOLVED]
Download torrent and worked like a charm. Why does ubuntu provide a bad iso? Thanks for the help.

---

### Post by MrPCSmasher on 2013-03-11
When you say "nothing happens," do you mean it just sits on the menu and stares back at you?

---

### Post by hobbzilla007 on 2013-03-11
Yes, it just stays on the menu with absolutely no activity.

---

### Post by MrPCSmasher on 2013-03-11
Did you try "press F6 and select nomodeset"?

---

### Post by hobbzilla007 on 2013-03-11
I saw those suggestions on other forums. When I press f6 nothing happens. The menu just stays.

---

### Post by MrPCSmasher on 2013-03-11
Ok, check if "Test memory" & "Boot from first HD"  please.

---

### Post by hobbzilla007 on 2013-03-11
Boot from first hd- screen goes black for about 3 seconds and returns to boot menu
Test memory brings up a blue screen. Memtest86+ v4.20 at the top. The rest is just general memory test stuff I assume which is running. It also has controls at the bottom- 
(esc)reboot 
(c) configuration 
(sp) scroll lock 
(cr) scroll unlock

---

### Post by MrPCSmasher on 2013-03-11
So you downloaded the .iso file and created a bootable USB drive. You have booted with the USB drive and get to the menu but cannot get any farther. I would guess there may be a problem with the .iso or something went awry during the setting up of the USB drive. I would suggest trying to recreate the bootable USB drive. Maybe download the .iso again (in case the issue is there). Finally, you might try using the alternate installer, however, it is only available via .torrent and for the 12.04 LTS at [http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)

---

### Post by hobbzilla007 on 2013-03-11
Thank you for your help! I will give that a try.

---

