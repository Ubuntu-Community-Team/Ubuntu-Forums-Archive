---
title: "Not booting from CD to install 11.04"
date: 2011-09-22
forum: Installation &amp; Upgrades
---

### Post by Orion_PKFD on 2011-09-22
Hi all,

I am speechless...

I had the old 9.10 in my laptop but I needed to upgrade in order to use a new program only available in the newer versions. Thus, I decided to upgrade (first to 10.04) but occurred and error. Now, when I try to enter in ubuntu (I have dual boot with Win7) the logo of the 10.04 saying "ubuntu" appears but nothing happens.

I decided to burn an ISO file of the newest version (11.04) and try to install it from scratch. But I can't boot from the CD. I have already changed the BIOS, but does not boot. Still appears the "grub menu" to choose linux or Win7.

I really need my computer working and I am scared because I need it for my everyday work. Anybody nows how to solve this and format the partition with ubuntu and install the newest version from scratch?

Best regards

---

### Post by mörgæs on 2011-09-23
First please give a complete hardware description.

---

### Post by vinterkind on 2011-09-23
if you get the GRUB Screen you could edit the menu of linux to start your old version to tell us how far it goes. If you've got GRUB Legacy (0.97) then you should simply do the following:

press "*e*" to edit the linux menu.

You should see something like

label ..
root ..
kernel ..
initrd ..

press "e" on the "kernel" line.

there you should remove things like "quiet" and "splash" and hit enter.

you can boot with pressing "b"

if your bootloader is GRUB2 (1.97) the "kernel" line was simply renamed in "linux"
Since you've said you're 9.10 I guess you've got the first variant ...

---

### Post by vinterkind on 2011-09-23
and btw.

Does the CD boots without Harddisk ?

You surely did alter the BIOS settings ?

---

### Post by Orion_PKFD on 2011-09-23
Hi all,

I have managed to install ubuntu 11.04 successfully. Thanks you.

Best regards.

---

