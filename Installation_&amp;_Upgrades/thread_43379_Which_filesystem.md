---
title: "Which filesystem?"
date: 2005-06-21
forum: Installation &amp; Upgrades
---

### Post by mrtaber on 2005-06-21
Tonight I'm getting ready to do a clean Ubuntu Hoary install on my home workstation, and I'm wondering now, which filesystem?  I'll be doing the usual things (web browsing, e-mail, writing documents), but I'll also have a very large number of music files (all legal, I might add--I ripped-and-encoded my 700+ CDs).  

I know that ext3 is the default, it's journalling, and it's the safe choice.  But I've heard good things about ReiserFS, and, for large files, XFS.

Opinions?

Thanks,
Mark

---

### Post by Lunde on 2005-06-21
[QUOTE=mrtaber]Tonight I'm getting ready to do a clean Ubuntu Hoary install on my home workstation, and I'm wondering now, which filesystem?  I'll be doing the usual things (web browsing, e-mail, writing documents), but I'll also have a very large number of music files (all legal, I might add--I ripped-and-encoded my 700+ CDs).  

I know that ext3 is the default, it's journalling, and it's the safe choice.  But I've heard good things about ReiserFS, and, for large files, XFS.

Opinions?

Thanks,
Mark[/QUOTE]

I'm not an expert on this, but I would recommend splitting in several partitions. I would choose ext3 for running the system, safe and clean. Then mount another partition for the home folder where you can use ReiserFS.

---

### Post by byen on 2005-06-21
i was out looking for a similar solution be4 installing ubuntu...and ended up on ext3 after finding out that this was the most stable as the other file systems ..though had good features had equally complicated backdrops. I was a newbie so i went the safe route...well...lemme see if i can find the link which classifies all the available file systems based on features. goodluck.

---

### Post by mrtaber on 2005-06-22
Well, I'm typing this from my fresh Ubuntu install.  I went conservative--ext3.  Thanks for the input, all.

Mark :)

---

### Post by luca_linux on 2005-06-22
I'd suggest ReiserFS for the / partition and ext3 for /home.

---

### Post by az on 2005-06-22
Unless you are running a server and need to squeeze every ounce of power out of your machine, you will not see a difference.  In that case, ext3 has a better stability record than the others.

---

### Post by juantxorena on 2005-06-23
If you are a normal user (won't use linux as server, 3D, digital video, etc), ReiserFS and Ext3FS are very similar, but:
ReiserFS is very fast with small archives, and goes slower as the size of the archive grows (the curve Slowliness vs. Size grows exponential)
Ext3FS doesn't mind the archive size when talking abour speed (the curve Slowliness vs. Size grows linear).
I have 5 partitions (LinuxSwap, /boot, /usr, /home and / ). LinuxSwap is LinuxSwap. /home, /usr and / are in Ext3. /boot is in ReiserFS, because boot archives are usually small.
P.D. Sorry for my english.

---

