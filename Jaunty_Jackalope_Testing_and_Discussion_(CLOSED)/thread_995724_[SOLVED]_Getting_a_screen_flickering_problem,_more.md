---
title: "[SOLVED] Getting a screen flickering problem, more like fizzing"
date: 2008-11-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-11-28
I'm using an lcd monitor but on Jaunty it looks like a bad crt. 

Anyone else.

On Intrepid it's rock solid.

---

### Post by ronacc on 2008-11-28
I'm not seeing that here on my 64bit jaunty , Nvidia 7600gs with 180.08 driver and samsung ws lcd.

---

### Post by philinux on 2008-11-28
Thanks. I think the driver in use is older than the 180.

I know it's not hardware as 8.10 is fine.

It's the same with compiz off or on.

[edit] It's the default 177.80 driver in use.

---

### Post by ronacc on 2008-11-28
I wasn't getting anything like that when I was still using 177.80 , must be something "new".

---

### Post by Gina on 2008-11-28
I'm using Jaunty and nvidia GeForce 6200 with 177 driver ATM on my AMD64 with Samsung SyncMaster 2232BW WS LCD monitor and it's rock solid.

Couldn't be a bad connection, could it?

---

### Post by philinux on 2008-11-28
Intrepid is fine just Jaunty.

LCD OSD does not exhibit the same fizzing.

---

### Post by ronacc on 2008-11-28
has it been this way in jaunty from the start or did it begin after an update ?

---

### Post by philinux on 2008-11-28
Started yesterday. I'm on intrepid now and no problem at all. Just got a dvi cable too what a difference.

---

### Post by ronacc on 2008-11-28
I never had any choice the 7600gs only has dvi (2) no vga .

---

### Post by philinux on 2008-11-28
> **ronacc said:**
> I never had any choice the 7600gs only has dvi (2) no vga .

Same here but old monitor was vga so it had a dvi>vga adapter. Got a new benq 22" ws last month and guess what it only came with a vga cable. So today for £10 got a dvi cable and it's great.

---

### Post by philinux on 2008-11-28
Back on Jaunty and flickering gone.

Could it be jaunty did not like the vga or could it be an update. :lolflag: I'll never know.
Thread solved unless it comes back......

---

### Post by robinharvey on 2009-04-14
Hi Guys,

Following an upgrade to Jaunty, I had a similar problem to the one you've described, but my solution was a little different...

I noticed that there was a particular horizontal area on my monitor which was going 'fuzzy' (Viewsonic VX922, NVidia 6800LE, 180.0 driver).  It was only noticeable when there was some text over this area, and the result was that the text appeared to move, or jerk around.  This also seemed to effect the bottom pannel, which also flickered a bit.

My solution was to go to the NVidia screen settings dialog (System > Preferences > Display, then click yes).  In the GPU 0 section, DFP-0 subsection there is a checkbox labeled "Force Full GPU scaling".  This was unchecked, and when I checked it, the problem went away.

HTH,
--Robin

---

