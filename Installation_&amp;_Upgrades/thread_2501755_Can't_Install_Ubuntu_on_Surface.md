---
title: "Can't Install Ubuntu on Surface"
date: 2024-10-19
forum: Installation &amp; Upgrades
---

### Post by megtruelove on 2024-10-19
During the installation process, the 'Erase and Install Ubuntu' option is not available and only offers manual installation.

When going into manual installation, it only detects the USB and nothing else. When going into Gparted, I also can not find anything besides the USB. 

I am not sure what to do from here.. I have tried trouble shooting to the best of my abilities but have gotten nowhere.

---

### Post by yancek on 2024-10-19
Is there an OS installed on the computer?  If so, what is it?  This is just a guess due to limited information but, if you have a newer version of windows installed on the machine it is probably hibernated in which case Linux won't see it or mount it.  If you have another OS, is it usable, can you boot it?  If you do not have any OS installed, is the drive seen in the BIOS?

---

### Post by yancek on 2024-10-19
Is there an OS installed on the computer?  If so, what is it?  This is just a guess due to limited information but, if you have a newer version of windows installed on the machine it is probably hibernated in which case Linux won't see it or mount it.  If you have another OS, is it usable, can you boot it?  If you do not have any OS installed, is the drive seen in the BIOS?

Is the computer you are referring to the one in the video at the link below?


[https://www.youtube.com/watch?v=wyhjUFcXgo0](https://www.youtube.com/watch?v=wyhjUFcXgo0)

---

### Post by megtruelove on 2024-10-19
I have Surface Book - 256GB / Intel Core i7 .

It had windows 11 on it, but windows 11 constantly crashed so I decided now was the time to switch it over. However, after messing around with Ubuntu and trying to get it installed, I can no longer boot windows 11. 

It does not seem like it is detecting any drives. Womp womp

---

### Post by nicolasdentremont on 2024-10-19
You wouldn't have a setting for RST in the BIOS menu would you? I had to set it to AHCI before the Ubuntu installer could see my drive.

---

### Post by megtruelove on 2024-10-20
Where would that be located? When I looked I didn’t see any settings for RST or anything similar.

---

### Post by nicolasdentremont on 2024-10-20
For me it was hidden in the BIOS menu, I had to use ctrl+s to show the hidden options but it's probably going to be different on your system.

It's just a guess really.

---

### Post by tea for one on 2024-10-20
> **megtruelove said:**
> I have Surface Book - 256GB / Intel Core i7 
Have you seen this website?
[https://github.com/linux-surface](https://github.com/linux-surface)
Is this your PC?
[https://github.com/linux-surface/linux-surface/wiki/Surface-Book](https://github.com/linux-surface/linux-surface/wiki/Surface-Book)

Just offering info - I don't have a Microsoft device.

---

