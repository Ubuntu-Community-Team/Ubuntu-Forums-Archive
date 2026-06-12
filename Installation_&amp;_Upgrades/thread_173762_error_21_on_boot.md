---
title: "error 21 on boot???"
date: 2006-05-10
forum: Installation &amp; Upgrades
---

### Post by webbcm01 on 2006-05-10
i just built my new pc its an asus a8n32 sli deluxe mobo, amd 64x2 4800, 2x250 gig western digital, 2(2x1)gig mem, 7900 gtx video, soundblaster x-fi sound i had xp and ubuntu dualbooting on my last computer, but this one i want strictly linux. i dont know what it is and i cant find any info to tell me what it means, but i installed the 64 bit ubuntu from the cd they sent me then when i took the cd out and rebooted as instructed, i get error 21 i tried installing lilo instead of grub but no avail. even tried going to the 32 bit installation but then i get "error 2" coming up. anyone know what this means or how to fix it?

---

### Post by Sef on 2006-05-10
> This is a definition of a boot 21 error:

Error 21 means :
"
21 : Selected disk does not exist
This error is returned if the device part of a device- or full file name
refers to a disk or BIOS device that is not present or not recognized by the
BIOS in the system.

[https://launchpad.net/distros/ubuntu...grub/+bug/8978]("https://launchpad.net/distros/ubuntu...grub/+bug/8978")

Click the link and read through the posts above and see if one of the solutions that people have written applies to you.

Hope this helps.

---

