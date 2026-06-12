---
title: "[SOLVED] GRUB won't load after BIOS update"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by College_Trained on 2008-09-17
Hey everyone,
It's been a while since I checked the forums (because of work and school and such).
I have a problem. I have a dual booted WinXP/Ubuntu Hardy system and I just used Windows to update the BIOS. The problem is, now GRUB won't load. I must use the Ubuntu LiveCD that I keep for, well, situations like these. If anyone could point me in the right direction as to solve this problem, it would be greatly appreciated. I have listed my system specs below.
Thank you in advance for anyone that can help me with this problem.
~Brendan Cook

Lenovo Thinkpad T61p
Windows XP Pro SP3
Ubuntu Hardy Heron 8.04
Intel Centrino vPro
160GB HD

---

### Post by oilchangeguy on 2008-09-17
> **College_Trained said:**
> Hey everyone,
It's been a while since I checked the forums (because of work and school and such).
I have a problem. I have a dual booted WinXP/Ubuntu Hardy system and I just used Windows to update the BIOS. The problem is, now GRUB won't load. I must use the Ubuntu LiveCD that I keep for, well, situations like these. If anyone could point me in the right direction as to solve this problem, it would be greatly appreciated. I have listed my system specs below.
Thank you in advance for anyone that can help me with this problem.
~Brendan Cook

Lenovo Thinkpad T61p
Windows XP Pro SP3
Ubuntu Hardy Heron 8.04
Intel Centrino vPro
160GB HD

i'm guessing you used the winflash utility that's in some computers to "update" the bios. was there a reason you felt the need to update the bios? because if you looked at the date(s) of the update(s) most were probably old and of no real use.

---

### Post by College_Trained on 2008-09-17
I just got the laptop a couple of weeks ago. For some reason I like making sure all updates are installed so I can feel content in knowing that my computer has the "latest" updates available. If it helps, I used the ThinkVantage System Updater. If you have any idea on how to fix this issue it would be a great help.

---

### Post by oilchangeguy on 2008-09-17
are you able to load windows? it looks like you'll probably need to reinstall grub.

---

### Post by caljohnsmith on 2008-09-17
When you updated your BIOS, I would assume all your settings in BIOS were reset back to their default values. Do you remember making any changes to your previous BIOS settings? That would be a good place to start. Look in your BIOS settings for your HDD settings, whether your HDDs are set for LBA mode, etc, and maybe tweak those settings. Also, what happens on start up? Do you get any Grub errors, or doesn't it even make it that far?

---

### Post by College_Trained on 2008-09-17
I got it fixed! I had to reinstall GRUB. I just got a friend to show me how it's done so now I know how to fix it if I ever f*** it up again.
Thanks for all the help and suggestions.
P.S. There was a GRUB error somewhere along the lines of "GRUB geo error" or something to that effect.
I figured I might have had to reinstall GRUB but I wasn't sure how to EXACTLY do it, and I didn't want to screw up my system by doing it the wrong way.
Thanks again everyone.
~Brendan Cook

---

