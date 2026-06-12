---
title: "missing file \ubuntu\winboot\wubilder.mbr"
date: 2014-09-17
forum: Installation &amp; Upgrades
---

### Post by jackmccaskill on 2014-09-17
I have, or have tried, to install 14.04 from cd disk, as a duel boot with Windows 8.1.  the install indicated "installation complete", however, when I attempted to login 

I got the following message "Missing file \ubuntu\winboot\wubildr.mbr" !

How do I obtain missing file and once obtained how do I proceed?  I thank you inadvance for any help but i must say that the is on of the most frustrating exercise I have ever participated in and sincerely wonder if it is worth the effort!

                thank you, Jack

---

### Post by yancek on 2014-09-17
The page below explains that the 'wubi' installer will not work with windows 8.  If you want Ubuntu, you will need to use some other method such as installing to its own partition.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by oldfred on 2014-09-17
If you have a new Windows 8 computer it uses the new UEFI replacement for BIOS which also uses gpt partitioning as the replacement for the 35 year old MBR(msdos) partitioning.

If a new UEFI system many useful links are in the link in my signature below.

What brand & model computer and what video card/chip?

---

### Post by hakuna_matata on 2014-09-17
> **jackmccaskill said:**
> 
I got the following message "Missing file \ubuntu\winboot\wubildr.mbr" !

wubildr.mbr works with Windows 8.1 but it doesn't work in UEFI mode. The problem is that preinstalled Windows 8.1 are always installed in UEFI mode.

_Recommendation:_
Don't use Wubi with wubildr.mbr and install Ubuntu to its own partitions.

If this recommandation is _not_ what you want, maybe [this]("http://ubuntuforums.org/showthread.php?t=1639198&page=121&p=13121598#post13121598") could be interesting for you.

---

