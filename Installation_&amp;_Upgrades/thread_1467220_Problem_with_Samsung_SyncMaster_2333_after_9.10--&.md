---
title: "Problem with Samsung SyncMaster 2333 after 9.10--&gt;10.04 upgrade"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by pellyg on 2010-04-30
I upgraded my system to ubuntu 10.04 last night. After the process completed, I restarted my system and there were 2 problems:

1. No flash plugin was found and adobe could not find one on their site.*
2. my flatscreen monitor (Samsung syncmaster 2333) was detected, but the display is fuzzy. I have tried lowering the resolution but this does not work. Is there a fix for this?

Alternately, is it possible for me to revert back to 9.10? I am a Linux novice and I'd rather stick with what works, even if it means I am a release behind. 

I am on a thinkpad t60.

Many thanks in advance!*

Thanks
Greg

---

### Post by zhitao on 2010-05-12
I am experiencing a similar problem on my T60 as well, after an upgrade from 9.10 to 10.04. Display is normal on laptop screen, but the external monitor has many ripples. My monitor model is Samsung SyncMaster 960BG.

> **pellyg said:**
> I upgraded my system to ubuntu 10.04 last night. After the process completed, I restarted my system and there were 2 problems:

1. No flash plugin was found and adobe could not find one on their site.*
2. my flatscreen monitor (Samsung syncmaster 2333) was detected, but the display is fuzzy. I have tried lowering the resolution but this does not work. Is there a fix for this?

Alternately, is it possible for me to revert back to 9.10? I am a Linux novice and I'd rather stick with what works, even if it means I am a release behind. 

I am on a thinkpad t60.

Many thanks in advance!*

Thanks
Greg

---

### Post by dino99 on 2010-05-12
may need to adjust the vertical and horizontal freq

---

### Post by Boababa on 2010-05-12
**SOLVED**
Turns out the new kernel enables KMS - a feature of some graphics chipsets that helps increase performance.  Unfortunately, for us with older chipsets this may result in a problem.  The fix is described in 10.04 release notes - i'll summarize here:

In terminal, type: sudo gedit /etc/default/grub
Find the line that says GRUB_CMDLINE_LINUX, and in between quotes insert word nomodeset
Save and close the edited file
In terminal, type: sudo update-grub
On reboot, things should start working again.

Enjoy the upgrade!

-b

--
Same problem.  Different laptop, but probably same Radeon Mobility X1600 graphics chip.  Also different monitor.  

Looks like horizontal is out of sync, but manual adjustments do not help.

Update: issue is related to kernel - even no graphics mode (terminal only) shows the fuzzy monitor.  Dropping down to a 2.6.31 kernel fixed this problem and both screens work fine.  (Of course other things are broken now.)  About to try upgrading to 2.6.33 version - will let you know what happens.

Update: same problem with 2.6.33-3 Lucid

-b

---

### Post by rkeyes on 2010-05-13
Have not yet tried the fix, but have been experiencing the same problem with my Radeon Mobility X1400 and my Samsung SyncMaster 2253LW.

---

### Post by coolboarderguy on 2010-06-23
> **Boababa said:**
> **SOLVED**
Turns out the new kernel enables KMS - a feature of some graphics chipsets that helps increase performance.  Unfortunately, for us with older chipsets this may result in a problem.  The fix is described in 10.04 release notes - i'll summarize here:

In terminal, type: sudo gedit /etc/default/grub
Find the line that says GRUB_CMDLINE_LINUX, and in between quotes insert word nomodeset
Save and close the edited file
In terminal, type: sudo update-grub
On reboot, things should start working again.

Enjoy the upgrade!

-b


Thanks for the fix..worked a charm!

---

### Post by maxvaillancourt on 2010-07-08
> **Boababa said:**
> **SOLVED**
Turns out the new kernel enables KMS - a feature of some graphics chipsets that helps increase performance.  Unfortunately, for us with older chipsets this may result in a problem.  The fix is described in 10.04 release notes - i'll summarize here:

In terminal, type: sudo gedit /etc/default/grub
Find the line that says GRUB_CMDLINE_LINUX, and in between quotes insert word nomodeset
Save and close the edited file
In terminal, type: sudo update-grub
On reboot, things should start working again.

Enjoy the upgrade!

-b

--
Same problem.  Different laptop, but probably same Radeon Mobility X1600 graphics chip.  Also different monitor.  

Looks like horizontal is out of sync, but manual adjustments do not help.

Update: issue is related to kernel - even no graphics mode (terminal only) shows the fuzzy monitor.  Dropping down to a 2.6.31 kernel fixed this problem and both screens work fine.  (Of course other things are broken now.)  About to try upgrading to 2.6.33 version - will let you know what happens.

Update: same problem with 2.6.33-3 Lucid

-b

Thank you very, very much! I am using a HP (Compaq) nw8440 with a Radeon Mobility X1600 graphics chip. My monitor is a 17 in. HP 1740. Thanks again for solving my problem!

---

