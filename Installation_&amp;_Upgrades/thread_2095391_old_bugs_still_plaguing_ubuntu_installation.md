---
title: "old bugs still plaguing ubuntu installation"
date: 2012-12-16
forum: Installation &amp; Upgrades
---

### Post by NHclimber on 2012-12-16
After working out/contributing to/fixing many of the bugs in my daily desktop (oneiric), I was finally ready to fresh-install quantal.  I use evolution as my mailer and the imap bugs were becoming intolerable (despite cherry-picking the worst offenders and building my own). But the killer was no nouveau backport -- and nouveau on oneiric (even with 3.7.0 kernel or -next) occasionally crashes when glx-gears is running.

But apparently, quantal is not installable -- even though I originally reported the same bugs for precise.

Why is it that Ubuntu desktop ***still*** cannot be installed on fakeraid? If ubiquity knows that it can't handle fakeraid, then it should halt installation.  Providing users with a bunch of bogus partitions is bad news. Please don't bother asking questions about my fakeraid --- go look at [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/973450/comments/12](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/973450/comments/12).

Although I've been working around ubuntu + fakeraid since jaunty, I figured since I debugged the problem with precise and provided explicit developer notes (in bug # 973450), installation would be straightforward. Not to mention countless iso bug reports in the run up to precise release. No such luck.

Why do the quantal release notes state:
"The consolidation of desktop installation media into a single image means that some installation options that were previously available on the alternate CD have no direct replacement on the desktop image.
....
There are several options for installing using software RAID. You can:
..."

and yet ubiquity still tries to install on fakeraid?

ISTM, if ubiquity + fakeraid is broken, then ubiquity should halt with a message about it being broken on fakeraid and refuse to progress.

Laughably, I can't install from mini iso because no input is accepted from my Logitech wireless keyboard (bug# 975198 regression).

Any suggestions?

---

### Post by ronparent on 2012-12-16
I haven't personally been able to sort it all out, but, there has apparently been a regression that doesn't permit either Ubuntu 12.10 or Mint 13 to be straight-forwardly installed to a fakeRAID. And, yes, ubiquity fails with no clue. After pounding away at it for two week I managed to install both U 12.10 and Mint 13 to a fakeRaid0 created by Windows 8. 

Basically you have two problems to straighten out. 1) The grub2 installation fails. 2) Dmraid is not installed. To fix 1) I used to live cd for the applicable install and mounted the install on /mnt and installed grub to /mnt as the --root-directory with the bootloader on the <RAID>  2) I then did a chroot install of dmraid.

ie
> sudo mount /dev/mapper/<yourRAIDinstallPartition#) /mnt
sudo grub-install --root-directory=/mnt/ /dev/mapper/<yourRAIDdrive>

Then I did something like
> sudo chroot /mnt apt-get install dmraid 

I may be foggy on the exact details because I had to work it out for both systems over a two week period. Good luck.

---

### Post by NHclimber on 2012-12-17
I managed to figure it out using a different method but thanks for the suggestions anyway.

---

### Post by ronparent on 2012-12-17
You posted a gripe. Any comments on your resolution?

---

### Post by NHclimber on 2012-12-17
Well, I worked around the lack of hid drivers on the mini iso with an old corded keyboard that I found in the basement  ;)

About installing on an existing fakeraid, it was pretty hairy and I'm not sure I'd want someone trying to repeat by following what will be inadequate instructions. This needs to get fixed in ubiquity.

---

### Post by ronparent on 2012-12-18
Amen to that. I have worked thru every new distro since at least 8.04 to resolve one fakeRAID issues or another to little avail. If it isn't broken at 9.10 then it will be by 10.04 (or as now)! Most users can't begin to cope.

---

