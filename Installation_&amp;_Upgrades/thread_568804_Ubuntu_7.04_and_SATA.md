---
title: "Ubuntu 7.04 and SATA"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by Thomeduk on 2007-10-06
I am trying to get WINXP Pro and SATA to dual boot all without any success. My system comprises two SATA HDDs.  WINXP is installed on one drive and Ubuntu opn the other.  The Ubuntu installation was made with the WINXP HDD disconnected.  Both drives will boot into their respective OSes.

The Ubuntu drive is hd0 and the WINXP drive hd1.  I have added to 'menu.lst' the following
title      Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
chainloader +1

At the 'Grub' menu on bootup I get Error11 Unrecognized device string

I have changed hd1 to hd0 and the converse.  I have change rootnoverify to (hd0,0) and to root, all without result, Error 11 persists.

I have also tried to install Grub using 'WinGrub' but that does not 'work' either.  The Grub Menu only shows 'Windows (0,0).

I have reversed the drives so the WinXP drive is hd1 and the Ubuntu drive is hd0 again without making a difference.

Can any one help?  I have scanned this forum and others and have tried all suggestions that may fit but there seems to be something very basically wrong with the grub menu.lst script but as a 'newbie to linux I really don't know where to start.

---

### Post by tenmillionmilesaway on 2007-10-06
When I was at Uni me and some others tried this.  The quickest way we got it to work was to keep both installs separate and then choose which hdd to boot from on startup.  Not the most elegant solution but it works.

Richard

---

### Post by PmDematagoda on 2007-10-06
Now the problem you have is that both SATA drives each have two boot loaders, this could be causing the main problem, so if you remove the MBR of one drive then most probably your problem will get fixed.

---

