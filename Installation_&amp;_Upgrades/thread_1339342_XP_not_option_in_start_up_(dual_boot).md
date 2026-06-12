---
title: "XP not option in start up (dual boot)"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by ((sbi.23)) on 2009-11-27
Ok, heres my problem. So I installed Karmic, then decided i wanted to dual boot Win XP for a couple reasons. I got through the whole partitioning and all that stuff and installed XP successfully. yay =].

But here is where i am stuck.

How would i go about making the Win XP appear as an option to boot, when starting up the laptop? Because right now it just boots straight into Karmic.

Any help?

---

### Post by phillw on 2009-11-27
> **((sbi.23)) said:**
> Ok, heres my problem. So I installed Karmic, then decided i wanted to dual boot Win XP for a couple reasons. I got through the whole partitioning and all that stuff and installed XP successfully. yay =].

But here is where i am stuck.

How would i go about making the Win XP appear as an option to boot, when starting up the laptop? Because right now it just boots straight into Karmic.

Any help?


Fixing and altering boot stuff for Win and Ubuntu is covered here -->  [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

That'll get you up and running :-)

Regards,

Phill.

---

### Post by darkod on 2009-11-27
First thing to try is updating grub2, it will automatically add any detected OS in the grub menu. In terminal do:
sudo update-grub

---

### Post by ((sbi.23)) on 2009-11-27
> **darkod said:**
> First thing to try is updating grub2, it will automatically add any detected OS in the grub menu. In terminal do:
sudo update-grub

That did the trick =] Thnx a lot, such a simple answer ^.^

---

