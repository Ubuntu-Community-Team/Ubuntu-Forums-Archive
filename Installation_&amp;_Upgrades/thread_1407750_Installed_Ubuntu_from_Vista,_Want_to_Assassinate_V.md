---
title: "Installed Ubuntu from Vista, Want to Assassinate Vista and Install XP in its Place"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by enjoytrees on 2010-02-15
I have the Windows Boot CD.

Everytime I try to boot it after a restart, it goes through the setup process until it reaches the following blue-screen error message:

"A Problem Has been detected and windows has been shut down to prevent damage to your computer".

AGHHHHHHH.

oh btw, I am DEF keeping Ubuntu as my primary. I just want to have XP (Not Vista) for things that Ubuntu can't do (or can't do as effectively with my level of user ability -- yet :)).

haylp?!!

---

### Post by darkod on 2010-02-15
If you installed ubuntu from inside vista (in other words wubi) as your title says, installing XP over vista will destroy your wubi too.
When wubi is installed inside windows overwriting windows will destroy it too.
Only if it's on a dedicated partition as full installation, you can overwrite vista partition with XP and ubuntu will remain on its own partition.

---

### Post by enjoytrees on 2010-02-15
I'm sorry I meant to say I installed Ubuntu from a boot-disc, but after Vista had been my OS for a few months. (came preinstalled with my machine). Don't know if that changes anything. 

Basicall I want to wipe the Vista partition entirely, keep the Ubuntu partition, and set up an XP partition instead.

---

### Post by darkod on 2010-02-15
In that case, since your vista partition is already ntfs, just tell XP to install onto that ntfs partition and that's it.
You will need to reinstall grub to the MBR of the hdd after that, just follow the instructions here and make sure you use 9.10 cd for grub2 (if your ubuntu is clean install of 9.10) or 9.04 cd for grub1 which is used on version 9.04 and before.
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

