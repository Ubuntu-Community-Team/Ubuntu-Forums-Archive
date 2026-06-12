---
title: "Feisty installs but GDM won't finish booting"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by patik on 2007-04-21
Previous I had Edgy set up like this:
sda1 - swap
sda2 - /
sda3 - /home

and I decided to do a clean install for Feisty (i386), so I downloaded the live CD and ran the installer. I checked the box next to sda2 to format it, kept sda3 as /home, and all went well. During my initial setup I installed something that, upon rebooting, made GDM hang. After typing in my name and password at the login, the Ubuntu logo with orange background came up but the upper left of the screen was gray and it hung there. Ctrl-alt-backspace restarted it, but then it hung at the same spot. Failsafe Gnome produced the same result.

So I figured I'd start all over and format sda2 yet again. However I've been having trouble actually clearing it out. When I delete it and add a new ext3 partition, the partition manager says it has 10,000MB used. Formatting and installing over it leaves me with the same hang-at-login-with-gray-box issue.

I feel like there's some file leftover on sda2 with a bad configuration that's causing my gray box problem, but I can't seem to clean the partition entirely. I've got Windows XP with Partition Magic on hand, and of course the live CD -- what can I do?

---

### Post by patik on 2007-04-21
I managed to clear off /dev/sda2 by formatting it to FAT in Windows, but when I tried to run the Feisty install again it still has the gray box problem. I'd say Feisty just doesn't like my machine, but I had it up and running before all this. I guess I'll try reinstalling Edgy and doing the upgrade.

Edit: Edgy installed fine, then I upgraded via Synaptic to Feisty which went fine until I rebooted and had the same problem. I guess Feisty just doesn't want to work, which is odd because it was working at one point and I had Feisty Herd 5 running just fine a couple months back.

Could it be something in my home folder?

---

### Post by tate311 on 2007-04-22
had the same exact issue on my laptop. i edited /etc/gdm/gdm.conf-custom to say 0 under [servers] then rebooted. after that i could log in and gnome loaded up fine. dont know why this works because /etc/gdm/gdm.conf says to use server 0 by default but whatever. btw, its a toshiba laptop with trident cyberblade xp display adapter.

---

### Post by patik on 2007-04-22
I got it to work by installing from the DVD and not specifying a home directory but letting it make a new one. Now I guess I'll just try to point /home to my old partition and slowly reintroduce the hidden .configuration folders since it must be one of those.

---

