---
title: "Dual Boot Win7 problem"
date: 2015-12-14
forum: Installation &amp; Upgrades
---

### Post by ray9 on 2015-12-14
I tried to use "Boot Repair" to detect Win7 on my other drive.  I get this error--"Please use this software in a live-session(live CD or live USB)  This will enable this feature."  I have never seen this before.  I work follow thru to detect 7.  (Ubuntu 14.04 LTS)

---

### Post by Dreamer Fithp Apprentice on 2015-12-14
Explain the background please. Why are you using boot repair? Did you install ubuntu on a system Windows was already on and now it boots straight to Ubuntu without giving you a choice? In general, you can't expect much help unless you start at the beginning, explain exactly what you did and exactly how things began to go wrong. Exactly. In detail. To hell with the forest, we need to see the trees.

Can you boot the machine in question at all? In what OS? Can you determine if, in fact, a Windows partition (well, 2 Windows partitions if it is a recent version of Windows) still exists? If you can boot Ubuntu and the Windows partition is still there you should be able to force grub to rescan the partitions. I believe the command is "update-grub". But it sounds like the problem is you aren't seeing the grub menu. You might try holding down the shift key as the machine is booted. Is it possible you choose the option in the installation process to install Ubuntu over windows and wiped it out? If you did, that would account for not seeing a menu. If so, ASFAIK, you're SOL. Maybe your machine came with one of those hidden "uh oh" partitions that lets you reinstall Windows as shipped? Or if not, maybe you have installation media? 
> **ray9 said:**
>  I work follow thru to detect 7.  (Ubuntu 14.04 LTS)These 2 sentences overloaded my English parsing module and my brain crashed.

---

### Post by oldfred on 2015-12-14
If you can run Boot-Repair in either your install or live installer, post the link for the Summary Report it creates.

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by ray9 on 2015-12-14
I have 2  drives, Win7 on one and Ubuntu on the other. It boots straight to Ubuntu.  I've used boot-repair in the past to accomplish this but now it doesn't work.  It also asks me "Is sda 500GB a removable disk?"  The sda is Ubuntu.


On edit:  "Update-Grub" worked great.  Thanks.  Sorry about the typo.  Cordless keyboard sometimes skips letters.

---

