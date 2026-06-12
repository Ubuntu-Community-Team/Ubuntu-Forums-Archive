---
title: "Urgent: black screen upon boot after restarts, probable firmware issue"
date: 2020-08-12
forum: Installation &amp; Upgrades
---

### Post by lelmst on 2020-08-12
I have a very strange problem. I've had some bugs with the default gnome version of ubuntu and yesterday it broke completely, unable to boot. Nothing was actually lost though because of internet and external storage. Reinstalling it from USB worked at first but upon trying to update some software when prompted to, the restart would leave my screen black it wouldn't boot by any method. So I decided to install kubuntu finally, and had the exact same problem despite that they occupied separate install disks and each time the installs would format and replace all content on the SSD. This seems like a firmware problem since it happens irrespective of the SSD's contents, but I'm not sure. Ever since I tried ubuntu first I had a somewhat similar situation. Powering on or restarting would lead to an infinite ASUS logo screen, but I always got into ubuntu easily through the UEFI menu by holding ESC immediately, so it wasn't a real issue. That's been a thing since my 1st day of linux. But the new problem is a far worse version of that one where instead, I can't load any part of the OS by any method on regular gnome ubuntu, and on KDE. At least the UEFI still works tho.
Computer type: ASUS zenbook Q536FD
https://www.asus.com/us/Laptops/Q536FD/specifications/

---

### Post by lelmst on 2020-08-12
Flashing the BIOS completely fixed everything and kubuntu works fine. Now I must know why ubuntu decided to modify the BIOS completely unprompted resulting in gnome partially breaking during the session before the first broken reboot

---

### Post by TheFu on 2020-08-12
How can we help without knowing the OS version?  Did you read the "Release Notes" for that version which probably has instructions to get around a black screen issue?  

Have you patched the firmware from Asus?

For example, 20.04 have known problems with nVidia GPUs.

---

### Post by lelmst on 2020-08-12
Kubuntu works after flashing the BIOS and I have absolutely none of the old issues.
Idea 2:
It was actually probably messed up from day 1 and that's why I had the first boot and failed second login issues. No idea if a modification of BIOS happened again yesterday or it just got worse for other reasons.

---

### Post by lelmst on 2020-08-12
I was going to go read it actually but the BIOS flashing removed every boot and login issue I've had so this has been solved. Thanks for advice

---

### Post by TheFu on 2020-08-12
If fixed, please help the community,  Thread tools  ---> SOLVED  so others know easily.
Please.

---

### Post by lelmst on 2020-08-12
Alright I'll do that
There's a lot of edits in the post btw but it's mostly to add new info or better clarify things

---

