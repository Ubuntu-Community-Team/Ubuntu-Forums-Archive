---
title: "Lubuntu 15.10 on a Compaq 6715b"
date: 2015-12-14
forum: Installation &amp; Upgrades
---

### Post by asearle on 2015-12-14
Hallo Everyone,

I am installing Lubuntu 15.10 (64bit) on a friend's Compaq 6715b and am having some strange problems:

Under 14.04 LTS everything works like a dream but the Broadcom WiFi unit is not detected.

Under 15.10 (fresh install) everything worked like a dream (including video-playback speed AND the Broadcom WiFi) BUT when I ran my first software/system update, video speed on DVDs and online (e.g. YouTube) dropped into basement with videos juddering and CPU-usage up to 100%.

I thought it might be the video-driver but ATI-Radeon is installed.  I also tried installing "fglrx" but that completely broke the system with me not even being able to boot (boot-graphics turned into blotches rather than letters) so I did another fresh install. 

This is bizarre.  Especially the fact that an update caused the drop in speed and increase in CPU-usage.

What should I do?  Try to do more diagnostics (I have already spent hours!!! on this) or wait for (L)Ubuntu to issue an update with a fix?  Or should I investigate another potential cause of the problem?

Many thanks for any tips that you can give.

Yours,
Alan Searle
Cologne

---

### Post by asearle on 2015-12-14
Hallo Everyone,

After a lot of fishing around I found this bug-report which describes my problem perfectly:  Low-speed, high-CPU-activity, fan permanently running ...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/280202]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/280202")

The solution they recommend (and which seemed to work for a good number of people) is to switch apic off.  

[http://ubuntuforums.org/showthread.php?t=1376547](http://ubuntuforums.org/showthread.php?t=1376547)

I changed this line in GRUB ...

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash apic=off noapic nolapic"

Which fixed the problem.

Here I am a bit bemused that the initial install was correct but somehow the update messed up by the system update meaning that the problem needed to be fixed with this change to GRUB.

Anyway, I hope these comments help someone out.

Regards,
Alan

---

### Post by sudodus on 2015-12-15
Congratulations and thanks for sharing your solution :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

