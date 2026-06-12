---
title: "Firefox won't run after Upgrade"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by jda8818 on 2010-08-17
10.04

Ran suggested upgrades today, firefox won't run.  I'm on a windows machine to access the forum.  

Get message in tray "Starting Firefox', but the process just dies and the mouse arrow reappears.

Really need to use the web with this machine.  As always, comments and suggestions are appreciated!

JA

---

### Post by wojox on 2010-08-17
Try #4 from here [4 - Problematic/corrupted user profile]("http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html")

---

### Post by jda8818 on 2010-08-17
Wojox!  Thank you for your interest!

firefox -P returns "Segmentation fault"

JA

---

### Post by lovinglinux on 2010-08-18
> **jda8818 said:**
> Wojox!  Thank you for your interest!

firefox -P returns "Segmentation fault"

JA

Then try:

```
sudo apt-get install --reinstall firefox
sudo apt-get install --reinstall xulrunner-1.9.2
```

---

### Post by jda8818 on 2010-08-18
Attempting to follow your instructions, lovinglinux, machine became extremely unstable.  Rebooting by itself, messages about processes that unexpectedly terminated, and finally quit entirely.  No boot processes at all.

Since there was a "Segmentation fault" message at one point, I swapped the memory modules (2 GB ea) side to side and after a couple of disk errors messages on boot up, poof, everything works.  Including firefox.  Linux has apparently healed itself after a hardware problem that i hope i have corrected!

go figya

methinks I'm going to check for bios upgrades

Thanks for your support!

JA

---

### Post by lovinglinux on 2010-08-18
> **jda8818 said:**
> Attempting to follow your instructions, lovinglinux, machine became extremely unstable.  Rebooting by itself, messages about processes that unexpectedly terminated, and finally quit entirely.  No boot processes at all.

Since there was a "Segmentation fault" message at one point, I swapped the memory modules (2 GB ea) side to side and after a couple of disk errors messages on boot up, poof, everything works.  Including firefox.  Linux has apparently healed itself after a hardware problem that i hope i have corrected!

go figya

methinks I'm going to check for bios upgrades

Thanks for your support!

JA

You might want to test your memory modules. The segmentation fault and this apparent self-healing could indicate an issue with your RAM. Nevertheless, it could be simply a memory module badly fixed on the slot.

---

