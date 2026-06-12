---
title: "&quot;cannot read the Linux header.&quot; New install, old machine"
date: 2012-01-23
forum: Installation &amp; Upgrades
---

### Post by ScrollerBlaster on 2012-01-23
I hope not. I have an old Compaq Evo laptop and I have completed a fresh install of lubuntu from here: [http://cdimages.ubuntu.com/lubuntu/releases/11.10/release/](http://cdimages.ubuntu.com/lubuntu/releases/11.10/release/).
There were no complaints during setup which was a complete wipe of the 250 GB HD. I get a boot menu when booting from the HD but it has never got past the error message:

    error: cannot read the Linux header.
    error: you need to load the kernel first.

I am now in rescue mode and I can execute a shell in /dev/sda1. When I do fdisk -l I see just three partitions:

 - /dev/sda1 (id:83), real big 
 - /dev/sda2 (id:5), extended 
 - /dev/sda5 (id:82), swap

I can see files in /boot and in ~. 

**My RESULTS.txt** **should be attached.**

I thought its maybe a BIOS limit thing with the old BIOS and large HD. But the pertinent files should all be stored at the beginning so would that matter?

---

### Post by ScrollerBlaster on 2012-01-24
Reinstalled, manually partitioning to keep partition sizes less than whatever limit the old BIOS could cope with (e.g. 40 GB for /, 2 GB for /boot). 

Now it's up and running.

---

