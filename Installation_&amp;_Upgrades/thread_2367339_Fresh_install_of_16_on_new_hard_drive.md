---
title: "Fresh install of 16 on new hard drive"
date: 2017-07-29
forum: Installation &amp; Upgrades
---

### Post by gunner220 on 2017-07-29
Folks I've had a few strokes and a lot of computer knowledge has been lost, no recovery software on this one. After the initial install I was able to boot into Ubuntu, do software upgrades and was a happy camper. Shut down computer and when attempting to start I get a blue screen with a still cursor. Every now and again a prompt in very erratic print asks for my password which I provide to no avail. Did I do something wrong on the clean install onto a new HD? I just kept the defaults.

Probably will have to reinstall because I can't access the BIOS. Be gentle here cause I do have a hard time connecting the dots sometimes. :confused:

---

### Post by deadflowr on 2017-07-29
Hmm, can you provide details about the machine?
Since you have your own troubles, perhaps something as simple as just the make and model might help.

Call it baby steps

---

### Post by gunner220 on 2017-07-29
Sorry it's an older Dell I scabbed together XPS 8500,Intel 3.1, 16 MB DDR3 RAM, new WD 1TB HD Seta2, Boot Mode UEFI (secure boot disabled).

Initial boot is very rapid to a purple screen which stays for an instant then goes to a blue screen with nada. Initial install seemed to go well. Thank you so much for your help. Damn it just booted to a functional desktop. Would still appreciate input that you might have.

---

### Post by deadflowr on 2017-07-29
Is it by chance using an nvidia graphics card?
I ask because there seems to be on again and off again issues related to nvidia cards and drivers in recent times.

(But that's been my outsider (i do not use an nvidia card) observation.)


Oh, and I'm sure you meant 16GB of RAM.

---

### Post by oldfred on 2017-07-29
Turn off fast boot in UEFI, so you have time to press keys before system starts to boot.
Fast boot assumes you have made no system changes, so does not scan system and write hardware configuration to hard drive for operating system to use. Often full power down or cold boot will do a full UEFI hardware reconfiguration, so you have time to press UEFI boot or UEFI key.

What video card do you have?
If nVidia, you normally need nomodeset until you install the correct nVidia driver for your nVidia card from Ubuntu repository. Do not install directly from nVidia with a .run file.

If only Ubuntu you have to press escape key (perhaps more than once) after UEFI & before grub starts system. If fast boot on, you may not have time to press key.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

