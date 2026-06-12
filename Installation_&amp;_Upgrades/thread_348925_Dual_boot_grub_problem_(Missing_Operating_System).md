---
title: "Dual boot grub problem (Missing Operating System)"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by astrashe on 2007-01-29
I'm setting up my laptop with XP and Edgy, using the same scheme I've used for years.  For some reason it's not working this time.  I'm getting a "Missing Operating System" error.

Ordinarily, I keep XP in the first partition (hda1), and keep MS's bootloader in the MBR.  I install grub to hda2, with a menu that will let me boot into either windows or XP.  Then I set partition 2 as the active one.

This means I get the typical grub boot menu, but I can make the machine look and act like a normal XP box by setting the first partition active.  It also means that I can go back to a fairly stock XP box by simply setting partition 1 as active and nuking the linux partitions.

It's not working on the laptop.  If I set partition 1 as active, XP boots fine.  If I set partion 2 as active, I get an error about there not being a bootable OS.

I don't use XP very often, and in the past I've tended to set up small partitions for it.  This might be the first time I've given it more than 32G -- would that create the problem?  I was under the impression that was an old lilo problem that went away a long time ago.

Also, I used to set up a /boot partition as ext3, and a big / partition in reiserfs, because I thought grub had trouble with reiser.  This time hda2 is one big ext3 fs that mounts at ./.  I don't think that would cause a problem, but I figured I'd mention it.

I know I can solve this by installing grub to the MBR, and if that's what I have to do, I will.  It's not that big of a deal.  It just bugs me when I can't bend the computer to my will :)

---

### Post by astrashe on 2007-01-29
A couple of updates:

I should have mentioned that this is a Lenovo 3000 C100 laptop.

The Grub FAQ says that you should update your BIOS if you're having trouble beyond 32G.  

The Lenovo web site sends you a dead page on the IBM web site for support and downloads, which I found to be extremely lame.  But a google search gave me the cached page from IBM, and the FTP link for the BIOS still worked.

It didn't fix the problem, though.

---

