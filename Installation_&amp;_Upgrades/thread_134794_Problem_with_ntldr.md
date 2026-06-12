---
title: "Problem with ntldr"
date: 2006-02-22
forum: Installation &amp; Upgrades
---

### Post by cholopepper on 2006-02-22
Hey guys, I do have installed Kubuntu 5.10 and it works great, no problem with that...
The thing is that I need to install windows so my brother can play a few games, I'm tired of listening to him asking me to install the freaking Unoperating System...
Anyway, I had windows installed but it was full of viruses and was working like sh... so I decided to reinstall... I installed it, but whenever I try to access the machine says ntldr missing or simply freezes with no response (just leaves a blank screen)
I have no problems when I access Kubuntu. I had to reinstall Grub and had no problems with it...
I just can't access windows.
Can anybody help me? Thanx a lot guys...
Javier, from Argentina.

---

### Post by djur on 2006-02-22
You need to tell us more about the drives you have the operating systems installed on.  It sounds like you're either missing a boot record for windows, or missing some crucial system files.  If you have a windows install CD you can take it to a recovery terminal.. and type help..  I believe there are a couple utilities there such as "Fixboot" and another one that will write a MBR and system files for you.  If you have two seperate drives, a fresh install of windows should install all of this information..  Then you would just need to add an entry in GRUB...  You may need to use features such as "hide" or "swap" which can be tricky.. Do not use hide unless you unhide..  Anyway, give us more information, but that should be enough to get you started.

---

### Post by cholopepper on 2006-02-22
First of all thanx for the help, I'll try the first option since I'm trying to install windows in the same hard disk that Kubuntu is... I did try with another hard disk, but it didn't work.
Anyway, I have a 120 Gb hard disk with an ext3 partition (kubuntu), a fat32 partition (for common use), and a NTFS partition (for windows)... and a Swap...
I have another hard disk, a 40 Gb one, which I connected just to try to install windows like a stand alone win machine, but it didn't work, so, I don't know if it's a hard disk problem.
Anyway, I will try with the first option (fixing the problem with de windows cd) and I'll let you know.
Thanx...
Javier.

---

