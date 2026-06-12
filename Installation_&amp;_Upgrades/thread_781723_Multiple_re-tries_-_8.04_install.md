---
title: "Multiple re-tries - 8.04 install"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by mailcar on 2008-05-04
Hi All,

On the same PC, have successfully installed 7.10 Alt (AMD X2 3800+, Asus A8N-SLI, 2G Mem, 74G Raptor).

I have downloaded 8.04 Alt from 4 different servers. On all the MD5 check is good.

Have tried Alcohol 120 & Roxio to make the ISO CDs at a variety of speeds, also tried using DAO/SAO & Raw DAO. Have burned at the lowest 4X.

Each time I go through the install, under load "Base System", I always get the error "locales_2.7.9-4_alldeb was corrupt", which eventually leads to a "Debootstrap Warning", which ends in "MT86Plus Checksum" error. Also the CD Integrity fails, but the MD5 is good and tried all variations of the ISO burn ???

Based on my experience with 7.10, thought this would be much easier. Have hit a deadend and out of solutions.

Any help would be appreciated.  Thank You, C.A.

---

### Post by pro003 on 2008-05-04
well first i would recommend you to use poweiso to burn the image... i never had a single problem with burning iso's when i was using power iso... now, you said that u used 7.10 alternate cd to install gutsy but now you having a problem with 8.04? am I right? did you download the desktop edition, cause if you have problems with desktop edition try downloading the alternate cd of 8.04... and burn it with poweriso, ;-)

come back with details...

---

### Post by mailcar on 2008-05-04
Yes. The previous install (a few times), I used both 7.10 Std & Alt Desktop version (i386). I prefered the Alt, cause I would use LILO. Also, I used Alcohol to burn the ISO, and did that at a medium speed. All worked fine (didn't have to go to the lowest speed).

For 8.04, downloaded the i386 version, with a check in the Alt checkbox. In comparing notes between my 7.10 & 8.04 install...can't find any differences ???

---

### Post by pro003 on 2008-05-04
```
For 8.04, downloaded the i386 version, with a check in the Alt checkbox
```

was it alternate cd of 8.04 that you have downloaded? or desktop version?

---

### Post by pro003 on 2008-05-04
and why don't you burn the iso with max speed? did you try that? it sounds to me like some files are corrupted in this cd you got...

and what do you mean by "downloaded it from 4 different servers"?

---

### Post by mailcar on 2008-05-04
Double-checked the main Ubuntu download screen...

I selected the "Desktop Edition" & "Std Personal Computer", choose a location (when I said 4 servers...essentially tried 4 different locations), then checked the box that says "Check here if you need the alternate desktop CD."

Once the download is complete, I run MD5 & make sure the checksum is good before burning.

I can try at Max Speed, but I've read that slower speeds usually will have less errors.

What I don't understand, is that with all the verifying & trying different methods, I still get the the same errors for each install, regardless of which CD I use and regardless of the burn method.

---

### Post by pro003 on 2008-05-04
well, try that.. burn with max speed at check it out... if it works - post good news here...:popcorn:

---

### Post by mailcar on 2008-05-05
Well, I'm clueless.

I used Alcohol 120 in the past, with no problems, to burn 7.10 and previous versions.

It's definitely a burn issue. Downloaded PowerISO as you suggested and bingo !   All is good.

Would still like to figure out why the same process I used in the past didn't work, but just don't have the time.

Thanks for your help !

---

### Post by pro003 on 2008-05-05
first, glad to here you solved the problem. :guitar:

second, burning at lower speed is recommended because some cd-roms are designed to work at lower speeds and needs those cd's burned at lower speed, but those cd-roms are mostly history now like floppies :lolflag: so that's why I've never burned an .iso or other image file at lower speed any than maximum, and I never had a single problem. Also burning an image file in linux i.e. ubuntu at maximum speed is what I always do and also never had a problem, as for windows poweriso does the job pretty good.

once more glad you solved this issue...

---

