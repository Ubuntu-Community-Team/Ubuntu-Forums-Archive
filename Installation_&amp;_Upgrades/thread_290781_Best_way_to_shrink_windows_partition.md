---
title: "Best way to shrink windows partition?"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by carlos1 on 2006-11-01
So, I'm about to install Kubuntu Edgy on a new box I just got. 
It's preinstalled with XP Media Center. 
I've done this plenty of times in the past, but I always completely re-installed windows first, on a smaller partition to leave room for Linux. 
This time, I don't want to have to re-install XP, just shrink its partition before I install my preferred O/S. 
Can anyone give me the simplest way to do this? I can't find any utility to do this from Windows, the only think I've found is to download the Knoppix live CD and use QTParted from that. 
Is is possible to do this as part of the Kubuntu install and save time? (Of course, I'll back up my data first!)
Many thanks for any suggestions.

---

### Post by bulldog on 2006-11-01
Download the gparted live cd and you can shrink windows.
Just before you do that,defrag windows to the bones.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Kateikyoushi on 2006-11-01
You can do it from the ubuntu live cd, backup all important data just in case and defragment the windows partition.
Then follow these installation instructions. [LINK]("http://www.psychocats.net/ubuntu/installing")

---

### Post by markymark on 2006-11-01
should be because that also uses gparted as the partitioner
within the installer

my personal favourite is to use the gparted live cd, which is only
a small download from 
 [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by az on 2006-11-01
> **carlos1 said:**
> 
Can anyone give me the simplest way to do this? 

You boot the live cd, run the installer and when it gives you the options at the partitioning step, pick the one where you shrink an existing partition to create free space.  Pick your windows partition and move the slider to the left.

---

### Post by bsussman on 2006-11-01
step 1: backup what you cannot afford to lose.

step 2: defrag your partition using the native (win) tool(s).

step 3:
> **azz said:**
> You boot the live cd, run the installer and when it gives you the options at the partitioning step, pick the one where you shrink an existing partition to create free space.  Pick your windows partition and move the slider to the left.

---

### Post by carlos1 on 2006-11-01
Thanks to all, this is really helpful.
When you say the Ubuntu "live" CD, I assume you mean the install cd - in other words I do it as part of the standard install from CD process?

---

### Post by carlos1 on 2006-11-01
Bump. 
I'm about to install - can someone tell me if I can do this from the normal install CD, or if I need a special "live" CD? Thanks.

---

### Post by bsussman on 2006-11-02
> **carlos1 said:**
> Bump. 
I'm about to install - can someone tell me if I can do this from the normal install CD, or if I need a special "live" CD? Thanks.
The standard ubuntu cd is fully capable of doing this easily.  Just be careful with the manual partitioning screens and the gparted step(s)

---

