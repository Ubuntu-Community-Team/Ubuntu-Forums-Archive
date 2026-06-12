---
title: "Ubuntu 12.04 LTS installed over 10.04 LTS --&gt; CANT BOOT WINDOWS XP SP2"
date: 2012-12-26
forum: Installation &amp; Upgrades
---

### Post by Microsoft Hater on 2012-12-26
Hey, I installed 12.04 to update 10.04.

Now, there is no grub2 bootup menu, and startup goes to Linux.

Solution 1 [failed]:

I used TestDisk to rewrite the mbr on windows, which let me boot up the recovery partition - worth noting is that after reinstallation, I still did not have access to the Windows partition - I had to run a full format first, and I got windows back in factory condition. Perfect.

Booted up the LiveCD to reinstall grub2 and allow the dual-boot option - Same problem:

On startup, bios screen comes and goes, then flashing underscore in top left, like normal, then my moniter stops with "frequency out of range" error (meaning the signal physically cannot be shown by the moniter), then linux automatically boots up. That's the new bootup process. Any ideas? 

Thanks much in advance community.

---

### Post by darkod on 2012-12-26
Looks like the grub menu is shown during the out of sync message and then it boots ubuntu by default.

You can open /etc/default/grub and there is a line to set the grub menu resolution to something like 640x480 (don't remember the exact line syntax right now but it's easy to find in the file).

Uncomment that line to activate it (remove the # symbol at the start), then run:
sudo update-grub

to create new grub.cfg. Reboot and see if that shows you the grub2 boot menu.

---

### Post by Microsoft Hater on 2012-12-26
Thank you sir! That did the trick.

For less experienced newbies (ohhh, I remember the days...) with the szme problem:

1) Open a Terminal (crtl + alt + t)
2) type:

sudo gedit 'etc/default/grub'

3) Remove the "#"
4) click save
5) Back in the terminal, type:

sudo update-grub

6) Restart computer, and it should be working again.

---

