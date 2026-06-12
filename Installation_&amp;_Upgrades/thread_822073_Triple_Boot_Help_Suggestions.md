---
title: "Triple Boot Help/ Suggestions"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by thecaptainjs on 2008-06-07
Here is what I want to do.

I want to triple boot. XP(32), Vista and Ubuntu.

I have 4* 320GB Hard Drives. 

My Mobo has raid 5 support now and i have 3 in raid 5 with my XP 64 install on it and Vista on the 4th drive. The performance sucks though with XP 64.

I want the best performance, but I do want some type of comfort that my data wont be lost. I need some suggestions.

I am not as concerned about my OS HD's dying. I can deal with most of that. Should a HD Die I would hate to lose my data, I can live with losing saved games and stuff like that.

How can I setup all 3 on a Raid 0?
What Order?


Basically I think I want to setup a Raid 0 with 2 drives and use it to triple boot XP, Vista Ultimate, Ubuntu. 
The other 2 drives i will with either raid 0 or raid 1 depending. 

So how do i do it?

---

### Post by ScottLij on 2008-06-07
Just use a RAID 1 or RAID 5 and as soon as a hard drive dies you need to replace it, might one to have a spare one if you're worried about losing data.  Once you set up the RAID, the computer should see just one hard drive.  Then install the OSes in this order:  Vista, XP, Ubuntu.

---

### Post by thecaptainjs on 2008-06-08
If only it were that easy. 
I was told a few times that ubuntu doesnt recgonize raid 5, so I wasnt sure about 0 or 1. 

So if i install Vista, XP then Ubuntu it will work?

---

### Post by ScottLij on 2008-06-08
I don't know why Ubuntu wouldn't work with RAID 5 but would work with RAID 0 and 1 as the RAID controller should handle the RAID and the computer should just see a single hard drive.  If you were installing these three OSes on a typical system the easiest (no extra work) install order would be XP, Vista, Ubuntu (this is different from above, I made an error).

---

