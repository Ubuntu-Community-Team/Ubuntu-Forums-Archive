---
title: "CD Boot problem"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by Albaster on 2005-10-16
Hi,

I'm a newbie.

I've downloaded the Ubuntu 5.10 image and burned it on a CD.
System says that it's not a systems disk at boot stage.I'm trying to install on a PC running Win 98.
What am i doing wrong?
This all sounds weird, but i have gone over the FAQ's and the forums.
No one seems to have the same problem.

Please help.

---

### Post by JimH on 2005-10-16
Yes, I have the same problem.  After reading pages and pages of instructions, I can't find the answer to what is probably very simple.  "Where's the 'start' button?"  Seriously, I'm waiting for some help, too.

---

### Post by SilentCacophony on 2005-10-16
It sounds to me as if you burned the .iso as a *file* onto the disk, rather than as an *image* (using track-at-once.) Depending upon what software you used to burn the cd, it can be less than obvious which burn options to use. For example, the built-in Windows XP burner will not burn it in the correct manner.

If you insert the disc and examine it within whatever OS you currently have, you should see several directories and a couple of files. If you see simply the .iso file instead, you burned it incorrectly.

---

### Post by Albaster on 2005-10-17
[QUOTE=SilentCacophony]It sounds to me as if you burned the .iso as a *file* onto the disk, rather than as an *image* (using track-at-once.) Depending upon what software you used to burn the cd, it can be less than obvious which burn options to use. For example, the built-in Windows XP burner will not burn it in the correct manner.

If you insert the disc and examine it within whatever OS you currently have, you should see several directories and a couple of files. If you see simply the .iso file instead, you burned it incorrectly.[/QUOTE]

Hi, I downloaded the .iso and unzipped it to a folder, then burned it to the cd.
What strikes me is that the ubuntu file has a zero length.
Any other advice to make the cd bootable. It's as if the oem does not kick in.
Really stranded. thanks for your help in any case.

---

### Post by taygan on 2005-10-17
don't unzip the .iso, but rather use a cd burning program (I used plex tools, I'm sure Nero would work too) to burn the .iso image (or disk image).

Don't just copy the files to the CD.

---

