---
title: "Cannot burn Ubuntu 12.04 LTS iso to livecd using Startup Disk Creator"
date: 2013-06-10
forum: Installation &amp; Upgrades
---

### Post by asuastrophysics on 2013-06-10
Hey guys, 

I'm running into a slight problem. I'm currently running Ubuntu 11.10, but whenver I attempt to burn the Ubuntu 12.04 LTS to a flash drive using Startup Disk creator, it simply burns a copy of 11.10 onto it instead. I've made absolutely sure that I'm specifying the 12.04 ISO from "Source Disk Image" box, but it just burns 11.10 onto the drive anyway. 

Anyone have any solutions to this? As of right now, it's impossible for me to install 12.04 onto my other comptuer because of this problem. 

Thanks a ton in advance!

---

### Post by andyg54321 on 2013-06-11
I had a similar problem where SDC would not let me select a different ISO image. I just switched to unetbootin, which worked very nicely.

---

### Post by grahammechanical on 2013-06-11
Have you tried deleting or moving the 11.10 ISO image file?

---

### Post by asuastrophysics on 2013-06-11
I tried unetbootin, but I cannot for the life of me get the program to mark the flash drive as bootable, so I get a "Missing Operating System" error on startup with it. That's why I'm using startup disk creator.

---

### Post by asuastrophysics on 2013-06-11
> **grahammechanical said:**
> Have you tried deleting or moving the 11.10 ISO image file?

Thanks, good point. I hadn't thought of that. I'll try that next and see what happens.

---

### Post by sudodus on 2013-06-12
If you still have problems, I suggest that you try cloning with dd supported by a shell-script to make it safer[URL="http://ubuntuforums.org/showthread.php?t=1958073"]

Howto make USB boot drives[/URL]

---

