---
title: "[SOLVED] 8.10 Home folder requires password"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by Trezker on 2008-10-31
After upgrading to 8.10, when I go to Places -> Home folder I am prompted for administration password.

I thought I fixed it after I went into folder properties and gave myself permissions for my home folder. But it didn't stick.

How do I fix this?

---

### Post by swedmiro on 2008-10-31
Well...when i try to open my home folder after updating, the media player starts!

---

### Post by Trezker on 2008-10-31
8.10 is awesome, suprises at every corner!

Well, I can start nautilus from terminal and that's all well and good. So it's the Places/Home folder that starts gksudo it seems.

What the bleep have the Ubuntu devs been doing? Turning Ubuntu into Alice's wonderland?

---

### Post by ken_do_san on 2008-10-31
I had the same problem when I did fresh install of 8.10 as well, I figured out that during the install, when the install came to partitioning the drives I hadn't selected the /home option on the partition my home directory resides in. 

All I did was another install, got to the point where it offers guided partitioning or manual and chose manual.  Once there, I selected the partition for home,(double click on the partition and a dialogue box comes up, go to the pop down menu and select /home click ok and your back at the partitoning manager, don't format the partition or you lose everything) and once the system installed again and rebooted there was my home partition up and running (so to speak, no request for admin psswrd or anything).

Hopefully I've explained this well enough to be understood.

:)

---

### Post by Trezker on 2008-11-01
I don't think there's anything wrong with my home folder as such. It's all there and usable, it's just the Places menu that's broken.

It starts gksudo instead of nautilus for some reason. The same thing happens in ktorrent when I open data folder.

I'd really like to fix this without reinstalling. It's an annoyance but I can live with it.

---

### Post by Trezker on 2008-11-01
Solved!

In properties for any folder, I looked at "open with" tab and indeed gksudo was selected. Changing back to file browser solved the problem.

---

### Post by supernova_hq on 2008-11-09
Thanks that worked for me.

The real question is why the bloody murder what gksu the default?!?

---

