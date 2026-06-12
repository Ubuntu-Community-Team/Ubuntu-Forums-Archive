---
title: "Can't get Ubuntu to boot"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by IsaacJ on 2008-02-21
Hello all. I've been trying to work this problem for the past couple of days, but no changes. Basically, I've dabbled with Ubuntu on and off in the past and decided I wanted to go Ubuntu only for a while and see what I can get it to do without using WinXP as a crutch. But now, I can't get Gutsy or Feisty to boot. It keeps stopping at "verifying dmi pool data...." as others have had.

Am I correct in thinking that I don't need GRUB if I only want to install Ubuntu by itself? Most of the other related threads seem to assume a dual boot with Windows, but I want only Ubuntu.

Here are some facts that might be useful in troubleshooting the problem:

1) I actually have 3 hard drives. 2 SATA and 1 IDE, I thought this could be part of the problem, so disabled all but the first SATA drive and tried installing Ubuntu on that. The results were the same, except I got as far as "update successful" after the "verifying dmi pool data" message. I then tried using the other drives for Ubuntu, still no change. 

2) I have tried changing the BIOS settings to make sure they point to the correct drive to start up. No changes.

3) I tried resetting my BIOS to defaults as other have suggested. Still no change.

4) I tried changing my SATA drives in the BIOS from RAID to IDE. (I'm not using a RAID array anyway) to see if this would affect anything. It didn't.

5) I get the same results in Feisty and in Gutsy.

6) I have successfully dual booted with Ubuntu and WinXP in the past. However, I was using a different motherboard.

7) I just wiped WinXP from the system to install Ubuntu exclusively. WinXP installs okay. But not Ubuntu.

8) I tried checking the "boot flag" of the first partition in the partition editor. It is flagged as boot as I expected.

9) I did try installing Grub (even though I didn't think I needed it unless I was dual booting) and Grub will not install in Gutsy or Feisty.

10) I am using the Live CD to enter this message. :-)

Any ideas or suggestions? I keep thinking this is a bios issue, but WinXP works fine. I would naturally prefer the SATA drives, but I can't even get the IDE to boot with Ubuntu.

Thanks for your help.

IsaacJ

---

### Post by Pumalite on 2008-02-21
[http://support.microsoft.com/kb/287553](http://support.microsoft.com/kb/287553)

---

### Post by Pumalite on 2008-02-21
[http://www.duxcw.com/faq/computer/dmi.html](http://www.duxcw.com/faq/computer/dmi.html)

---

### Post by Pumalite on 2008-02-21
[http://www.computerhope.com/issues/ch000474.htm](http://www.computerhope.com/issues/ch000474.htm)

---

### Post by IsaacJ on 2008-02-21
Thanks for the replies, Pumalite. But I have solved the problem - though I'm still not clear why it helped.

The solution was to use the Alternate CD instead. I see that the Alternate CD used GRUB even though I only wanted Ubuntu on the system, so it seems that GRUB is used no matter what. :confused: The LiveCDs couldn't install GRUB for some reason.

At least it wasn't the BIOS. :) And it works now. I hope to become as good with Ubuntu Linux as I was with Windows.

IsaacJ

---

### Post by Pumalite on 2008-02-21
I'm glad you worked it out. Good luck.

---

