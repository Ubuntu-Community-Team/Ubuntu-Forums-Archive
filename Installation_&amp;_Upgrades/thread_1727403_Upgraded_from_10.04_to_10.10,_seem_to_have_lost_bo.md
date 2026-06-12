---
title: "Upgraded from 10.04 to 10.10, seem to have lost bootloader?"
date: 2011-04-12
forum: Installation &amp; Upgrades
---

### Post by ruaraidh on 2011-04-12
Hi guys,

I'm dual-booting Windows 7 and Ubuntu (10.04 installed using wubi). I just tried to upgrade to 10.10 which didn't go smoothly. I followed the updater instructions to the letter, then rebooted as required. When I was presented with the Windows bootloader offering me a choice of the two OSes I picked Ubuntu. Normally I'd get GRUB after that, but instead the computer hung for a moment then restarted itself. I presume that GRUB has been deleted somehow, but I don't understand the technicalities of bootloaders.

Windows still works fine, so nothing's too messed up. I'm a little nervous about trying simply to reinstall GRUB without advice in case I do something silly and lose Windows too.

All help much appreciated!

---

### Post by bcbc on 2011-04-12
That's good that you are nervous about installing Grub. It will make things worse on a Wubi install and prevent Windows from booting.

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) See problem #2, solution #2 and the Permanent Fix

---

### Post by ruaraidh on 2011-04-12
Fantastic, thanks very much for your help. :) I will report back after I've made a stab at fixing it.

EDIT - Used Solution #1 of Problem 2 on the aforementioned page to fix it. Thanks again!

---

