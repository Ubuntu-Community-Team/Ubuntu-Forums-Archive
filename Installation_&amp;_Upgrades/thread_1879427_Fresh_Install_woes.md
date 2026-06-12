---
title: "Fresh Install woes"
date: 2011-11-11
forum: Installation &amp; Upgrades
---

### Post by temporaldoom on 2011-11-11
Currently have a 250 GB drive that  has windows 7 on the main partition a 120GB data partition and 40GB of free space

I've tried Ubuntu 9/10 and 11 live cd's and they all stop at the same point with ubuntu splash screen, if I press escape I can see a miriad of errors.

the last one is kernel panic! I know the cd works as used it to install it on my laptop.

Any ideas?

---

### Post by MickSulley on 2011-11-11
I have had problem installing with Windows if it is fragmented too much.  Try running defrag in Windows a couple of times then try again.

Cheers
Mick

---

### Post by Hakunka-Matata on 2011-11-11
hey guys, this means you are installing Ubuntu via Wubi.exe?

---

### Post by darkod on 2011-11-11
So, you can't even boot the cd in live mode?

When the menu about try or install ubuntu shows up, press F6 for advanced options and look for the option nomodeset. Select it and try to load the live mode. See if that helps.

But take into account that if it does, and if you continue installing, first time you will probably have to do the same in order to boot successfully. Once you are inside your installed ubuntu you will need to make this change permanent.

---

### Post by temporaldoom on 2011-11-12
I'm trying to dual boot them.

I tried the suggestion of F6 and disabling that feature and it still fails

if I press esc on the splash screen I can see most of th errors relating to input/output errors

Where does linux copy itself too when it's loading from the live CD?

---

### Post by Hakunka-Matata on 2011-11-12
It loads itself directly into RAM

---

### Post by darkod on 2011-11-12
You might have a corrupted burnt cd, or the image file got corrupted while downloading. First, try burning a new cd, and at low speed, not more than 8x or 10x. Always burn OS install CDs at low speed.
If that still gives I/O errors, try downloading the image again. I prefer downloading from torrent because the torrent program checks for corruption during download. Then burn the new image on CD at low speed.

---

### Post by mohamedtoma73 on 2011-11-12
this problem is due to hardware incompatibility(espicially graphic card).try safe mode if present.

---

### Post by Hakunka-Matata on 2011-11-12
> **temporaldoom said:**
> I'm trying to dual boot them.

I tried the suggestion of F6 and disabling that feature and it still fails

if I press esc on the splash screen I can see most of th errors relating to input/output errors

Where does linux copy itself too when it's loading from the live CD?

OK: Please answer a few questions and explain what your goal is?


[LIST]
[*]Are you attempting to install Ubuntu as a Wubi.exe install, i.e. inside WindowsOS (Y/N)
[*]if not Wubi, but rather to a partition of it's own,
[LIST]
[*]What's happening when you try to boot to the Ubuntu liveCD/USB?
[/LIST]
 
[*]Please post the output of following commands:```
sudo fdisk -l && sudo sfdisk -luS
```
[/LIST]
**EDIT: **Reread your first post:  If you suspect you might have a corrupt download, or poorly burned image to boot with, redo it all.  Takes a few minutes.  Unetbootin is a proven tool to use for 'burning' a liveCD/USB from an Ubuntu .iso file you've downloaded.  Unetbootin will download it for you too if you wish, but it's slow.

You can always try your liveCD/USB on someone else's computer, (not a good friend's computer)

---

