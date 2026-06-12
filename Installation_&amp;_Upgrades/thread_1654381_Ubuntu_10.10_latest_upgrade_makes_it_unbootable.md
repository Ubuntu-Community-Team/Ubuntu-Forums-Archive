---
title: "Ubuntu 10.10 latest upgrade makes it unbootable"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by zeiger on 2010-12-28
Hey guys,
I am a Linux newbie.
I have a Dell Studio 15 and I used dual booting to run Ubuntu 10.10 on it.
Last night I installed the updates which showed up in the Update Manager. Today when I started my laptop and selected Ubuntu as the OS, I get the GRUB command line and not the usual listing of kernels that I can select. From the GRUB Command Line, I don't know how to boot Ubuntu.
My Windows still boots fine, but I want to work on Ubuntu,

See the attached snapshot of what I can see once I click on Ubuntu as the OS that I want to load.

Can you help me out?
Thanks,
Zeiger

---

### Post by dino99 on 2010-12-28
type:

sudo ap-get update
sudo apt-get install -f
sudo dpkg --configure -a

sudo update-grub

reboot

---

### Post by zeiger on 2010-12-28
From this command line, I cannot use sudo or ap-get etc.

> error: unknown command 'sudo'

---

### Post by dino99 on 2010-12-28
have you tried to boot on "recovery mode" ?

then "repair packages", then "continue normal boot"

---

### Post by Rubi1200 on 2010-12-28
If you installed Ubuntu using Wubi, see here:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

problem #2, solution #1 is probably best in this situation.

Good luck!

---

### Post by zeiger on 2010-12-28
Thanks Rubi1200,
Problem #2 Solution #1 worked and now I Ubuntu loads :D

---

### Post by Rubi1200 on 2010-12-28
> **zeiger said:**
> Thanks Rubi1200,
Problem #2 Solution #1 worked and now I Ubuntu loads :D
You are more than welcome :D

The next time you boot into Ubuntu, apply the Permanent Fix to prevent this happening again.

Enjoy!

---

