---
title: "Problems during update from 8.04 LTS to 10.04 LTS"
date: 2010-08-19
forum: Installation &amp; Upgrades
---

### Post by hoschti on 2010-08-19
Hi all!
I tried to update my ubuntu from 8.04 to 10.04. Because I couldn't find the update in the update manager I started the update with the following:

---
<Alt> <F2>
update-manager --devel-release
---

After checking for packages to update I first updated all the programms listed in the update manager. After this I started the update of the OS. After some checks the download of the new files started. It took appr. 2 hours. After this I got he message about some applications, which are no longer supported. 

So far no problems. Than I started the update of the system. After some further preparartions the update stopps with the following error message:

---
Die Aktualisierungen konnten nicht installiert werden
Fehler beim Anwenden
'E:Couldn't configure pre-depend jre for openoffice.org-writer2latex, probably a dependency cyle.'
Ursprünglicher Systemzustand wird wiederhergestellt
---

I tried a restart of the update as well as a rebboot of the system and restart of the update. Both failed with the same error.

My system:
AMD64 (ubuntu 32 bit version)
Grub with 'Ubuntu' and Windows XP

For me the only way to get Ubuntu 10.04 running seems to install it from CD/DVD.
Any other idea for finishing the update?

Thanks for help!
Hoschti

---

### Post by mörgæs on 2010-08-19
Hi, welcome to the forum. 

> **hoschti said:**
> For me the only way to get Ubuntu 10.04 running seems to install it from CD/DVD.

Yes, that is a good first try. Before doing this it is best to boot with the live CD to verify that everything works.

---

### Post by hoschti on 2010-08-19
Hi[FONT=Arial] Mörgaes[/FONT][U][FONT=Arial],

[/FONT][/U][FONT=Arial]thanks for your idea! My system is still working (8.04). Because I don't want to update all my stuff, I would prefer the update rather than a blank system install. But if nobody can give me a hint to reactivate (or reset) the broken install I will have no other chance to get a new OS version.[/FONT][U][FONT=Arial]
[/FONT][/U]

---

### Post by arpanaut on 2010-08-19
Did you remove all ppa's and third party repositories before your attempted upgrade?


take a look here:  [https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

---

