---
title: "Deselecting Upgrades"
date: 2015-03-18
forum: Installation &amp; Upgrades
---

### Post by mge56s on 2015-03-18
Two weeks ago, an upgrade for the kernel came along, which I accpeted.  It inatalled x86 64 SMP specific code.  I had 14.04 on an AMD64 machine and I felt the kernel bogged the machine down.  So I installed a clean version of 14.10 AMD 64.  Now I'm getting upgrade notification for the x86 SMP kernel again.  I keep deselecting it in the software update dialog box, and it keeps reappearing as a security upgrade.  I've had similar issues for programs that I have used either Synaptic or Ubuntu Software center to remove.  Is there some arcane magic needed to keep update notifications that I don't want from constantly reappearing?

This is by no means a critical issue, just an annoying one.

Thanks

---

### Post by ian-weisser on 2015-03-18
> **mge56s said:**
>  Is there some arcane magic needed to keep update notifications that I don't want from constantly reappearing?

You have two options:

Easy: Uninstall the package. Do make sure you read the full list of removals before accepting the change, else you may remove applications you wanted to keep. 

Harder: Use apt-pinning. This is how you 'permanently refuse' a specific package upgrade. See [https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto) . Warning - permanent means permanent. Undo the pin before you update to another release of Ubuntu - update failures caused by the pin may break your system.

Most updates in released versions of Ubuntu are usually either security fixes (you want those!) or important bugfixes (you want those, too).

---

### Post by mge56s on 2015-03-22
Thanks for the info.  I think I will probably just keep de-selecting the upgrade every time it pops up, rather than risk losing the kernel.  I don't think I can uninstall that particular package without some adverse consequences.  I will check out the link and see how specific I can get in a permanent refusal process..

---

