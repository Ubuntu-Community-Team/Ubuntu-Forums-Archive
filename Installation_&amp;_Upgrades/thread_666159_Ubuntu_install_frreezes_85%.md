---
title: "Ubuntu install frreezes 85%"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by x3roconf on 2008-01-13
I'm using alternative cd. I downloaded it via bittorrent. Normal install with alternative cd works fine but installation with LVM+encryption fails. When installation reaches 85% it freezes.. during tomboy install :(

My rig:
Q6600  @ 2.40GHz
Nvidia 8800GT
2 gt ddr2
Asus P5E

---

### Post by Sef on 2008-01-13
1) Did you burn the iso at 4x or less?  (Faster can cause a bad burn.)

2) Did you use 'Check Disk for Errors'? (Instead of start/install, go down the list.)

---

### Post by x3roconf on 2008-01-13
> 1) Did you burn the iso at 4x or less?  (Faster can cause a bad burn.)


No.
> 
2) Did you use 'Check Disk for Errors'? (Instead of start/install, go down the list.)

No.

I'm going to make a disk check :)

---

### Post by x3roconf on 2008-01-13
CD integrity check and memory check found no errors and i think that bittorrent does a SHA-1 check?

---

### Post by hardyn on 2008-01-13
it happened to me... i believe it has something to do with network configuration.  i cant really remeber what happened (if i killed it, or it timed out) but in the end everthing worked but had a misconfigured Synaptic.  It was easy enough to fix.

but yes, allways check your media before install.

---

### Post by x3roconf on 2008-01-13
> **hardyn said:**
> it happened to me... i believe it has something to do with network configuration.  i cant really remeber what happened (if i killed it, or it timed out) but in the end everthing worked but had a misconfigured Synaptic.  It was easy enough to fix.

but yes, allways check your media before install.

I waited some 15 minutes and turned my comp off. It was totally frozen (no hard disk activity etc) Never happened to me before.
Maybe it has something to do with LVM and cryptsetup? Who knows?

---

### Post by Kaneda on 2008-01-13
I'm having the same exact problem.  I'm trying to install xubuntu on my system using the alternate cd because of issues with my ATI video card, and it always freezes at 85% right after/when it says "Installed upgrade-notification."

I burned the disc at 8x, had my burning software verify the contents (it passed), and also ran "Check Disc for Errors" at boot up (it also passed).

The computer I'm installing on is a dual boot system, and because the installation stops before setting up a boot manager, I can't boot into anything on the computer right now (aside from boot discs like the install CD).

I've heard about Gusty having issues with laptops, and this system is a IBM/Lenovo Thinkpad.  Do you think it might be a better idea to forget about Gusty and go with Fiesty?

---

### Post by Kaneda on 2008-01-14
Well, I tried installing one more time.  This time I left it going while I went to work.  I came back 10 hours later, and things were running smoothly and I finished the installation no problem.  Thanks!

---

### Post by engalaa on 2008-01-14
Hi :
I have the same problem on my laptop Acer 5520G but when it on 82% "mirror scan "

---

### Post by Partyboi2 on 2008-01-14
> **engalaa said:**
> Hi :
I have the same problem on my laptop Acer 5520G but when it on 82% "mirror scan "
Eventually it should timeout and continue with the install. Just means that when the installer is finished and you have rebooted into your new ubuntu you will need to tick a few boxes to get updates and access to programs you may want to install
To do this go to "Software Sources" (System>Admin>Software Sources)
On the first tab tick all of them execpt the last one. Then on the update tab tick the first 2 then close Software Sources.

---

