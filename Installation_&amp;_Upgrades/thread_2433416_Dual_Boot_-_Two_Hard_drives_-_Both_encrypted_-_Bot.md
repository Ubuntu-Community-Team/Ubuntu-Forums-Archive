---
title: "Dual Boot - Two Hard drives - Both encrypted - Both Ubuntu"
date: 2019-12-18
forum: Installation &amp; Upgrades
---

### Post by roundrock90210 on 2019-12-18
I had a dual boot system with two hard drives both were Linux one was my Desktop Running Kubuntu 14.04 and the other was Lubuntu 14.04. The Lubuntu was my media system. I ended up upgrading my Desktop to 18.04 Kubuntu but it ended up breaking my dual boot and I can't figure this one out. I ran os-prober thinking it would look at the boot drives for the OSs. It didn't find anything. Guess I was wrong as I had to mount the second hard drive so I used udiskctl unlock. I then tried to mount it but it mapped it to the same point as my current OS (kubuntu-vg) so it gave me an error. I then changed the name by using vgrename and I looked in the boot drive of 14.04 and saw it was called usernamepc so I just called it this with vgrename. I then was able to mount it. I ran op-prober and it saw it so I ran update-grub and it picked it up but when I try to boot into it says kernel not found and then drops me to a shell. I've done some searches but they mostly came up with windows 10 plus Ubuntu or the two Ubuntus were unencrypted. Not sure of the next step.

---

### Post by roundrock90210 on 2020-04-05
Still trying to figure out why I can't get this to work.

I booted into the system with grub then I did a 

#cryptsetup luksOpen mypc-vg
#mount /dev/sda5 mypc-vg

I then did an os-prober and it finds my other Ubuntu install.

The problem is that it puts the root=/dev/mapper/kubuntu--vg-root

kubuntu-vg is the vgscan name of the Ubuntu with Grub.

When I try to boot into the other I get dropped to an intrafms shell as it says can't find /dev/mapper/kubuntu--vg

I tried editing the grub entry to say root=/dev/mapper/mypc--vg-root but when I do this I enter my decrypt password and it just hangs.

Anyone have any pointers?

---

