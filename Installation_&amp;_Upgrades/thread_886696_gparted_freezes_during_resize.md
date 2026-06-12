---
title: "gparted freezes during resize"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by serialbox on 2008-08-11
I really really hope I haven't messed up my hd.

I have ubuntu 8.04 installed as my main os.. and I wanted to install winxp using dual boot so I can play a few games. 

I downloaded the rescuecd with gparted, booted from the cd and ran gparted to resize my 145g hd to give 20gb for windows.   it says its resizing but its been stuck for like 2 hours with no progress.  the bar just keeps moving back and forth.  the harddrive is working and the light is flickering but Ive read that this shouldnt take nearly as long as it is.

If I restart my laptop will it ruin the data I have on my hd?

---

### Post by fs3rp4 on 2008-08-11
> **serialbox said:**
> I really really hope I haven't messed up my hd.

I have ubuntu 8.04 installed as my main os.. and I wanted to install winxp using dual boot so I can play a few games. 

I downloaded the rescuecd with gparted, booted from the cd and ran gparted to resize my 145g hd to give 20gb for windows.   it says its resizing but its been stuck for like 2 hours with no progress.  the bar just keeps moving back and forth.  the harddrive is working and the light is flickering but Ive read that this shouldnt take nearly as long as it is.

If I restart my laptop will it ruin the data I have on my hd?

Trust in your lucky. You can't do anything more...

This happened with me last week. I rebooted expecting no boot, but, the resize worked.

---

### Post by serialbox on 2008-08-11
> **fs3rp4 said:**
> Trust in your lucky. You can't do anything more...

This happened with me last week. I rebooted expecting no boot, but, the resize worked.

well today must have been my lucky day kind of.  i rebooted and my original partition is still working properly and the new resize didnt work. I stil have my full 145gb.

i'll skip the dual boot.. I dont need windows that badly.. it sucks

---

### Post by rtlong on 2008-09-10
I just wanted to ask if anyone else had had this issue. I'm finding it a real p.i.t.a. I've got my 8gb flash drive that I need to reconfigure, and, like he said, gparted just sits there. It's not frozen; I can cancel the operation with no problem. It's certainly doing something wrong, though. Anyone else experiencing this?

---

### Post by penfold33 on 2008-10-01
hi, I also have this problem. Last night I resize a 250GB drive to remove a 6GB partition at the start. I took over an hour to perform the read operation (as part of the resize) and said it would take 6hrs to perform the write. I left it overnight and in the morning it said it had 0 mins left but was not moving to the next task which was to check the filesystem for errors. I've cancelled the operation and it seems to have worked ok but needless to say it took ages and there was a fair amount of uncertainty invovled.

---

