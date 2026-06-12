---
title: "Ubuntu installation with a old screen"
date: 2015-09-19
forum: Installation &amp; Upgrades
---

### Post by andrei23 on 2015-09-19
Hello. Some days ago I burned a DVD with Ubuntu and boot it.

I tried many things, I asked the #ubuntu IRC, but they can't help me (well, I have been send to ##hardware, I have never join ##h before, but the IRC told me I'm banned :( ).

My problem is the following: anything I tried (nosetmode, any Ubuntu mode), after about 10 seconds my screen tells me 
[http://i21.servimg.com/u/f21/16/13/35/99/20150910.jpg](http://i21.servimg.com/u/f21/16/13/35/99/20150910.jpg)
uh, too big image :/

I don't even know if this is the right category to post into. It looks that ubuntu forum doesn't anymore look like the photo attached to this [post]("http://ubuntuforums.org/showthread.php?t=2054969&p=12225867#post12225867") (old auto message, I think).

Thank you for everything.

---

### Post by grahammechanical on 2015-09-19
The forum administrators update the forum sections from time to time. They remove sections that no longer have a valid basis for existing and add new sections as they detect a need. So, we now have a section on Ubuntu Phone & Tablet which we never had when I first joined the forum. But I am sure that the section for Hardware has been around even before I joined the forum.

Posting in the wrong section can easily be rectified by the forum moderators. It may cause a delay in getting a useful reply as some of us like to stay in areas that we have some knowledge of. What causes the longest delay is the failure to provide enough information to make even a guess as to the cause of the problem. So,

What is monitor are you using? You say "old screen" and that causes me to think old Cathode Ray Tube (CRT) monitor. Correct or incorrect? Also, it is not clear if you are getting this error message when running the Ubuntu live session or as a result of changes that you have made to the video settings of an installed Ubuntu. Are you trying to set a screen resolution that is outside the optimum range of the monitor? That could cause damage to the monitor.

Regards

---

### Post by andrei23 on 2015-09-19
Well, not soo old.

I found [this]("http://i.ebayimg.com/images/i/310907989013-0-1/s-l1000.jpg") photo on google and it look like my monitor.

I tried both live session and install ubuntu, same error message. I'm not able to set a resolution. I through nosetmode will.. I don't know.. set a lower resolution, but it doesn't. I don't know what resolution want Ubuntu to show on my monitor. But my monitor isn't able to show anything higher than 1280 x 1024.

I could succesfully see [this]("http://i.stack.imgur.com/FfEwE.png") screen(another google pic), but after I select Try or Install(with or without nomodeset) it shows me this error. The settings aren't changed. I can't set any resolution.

Thank you.

---

### Post by andrei23 on 2015-09-21
Any ideas ?

---

### Post by Radall on 2015-09-21
I did a quick search and stumbled across [this post]("http://ubuntuforums.org/showthread.php?t=1888642").
I didn't read it in detail, but I guess, this only works if you have a working screen available.

---

### Post by oldos2er on 2015-09-21
> **andrei23 said:**
> Any ideas ?

Please tell us which version of Ubuntu you're using, and list your hardware specs.

---

### Post by mörgæs on 2015-09-22
Yes, first of all post the monitor details. Should be printed on the back of it.

---

### Post by andrei23 on 2015-09-22
[SIZE=2][FONT=arial]Hello.

The version is ubuntu-14.04.3-desktop-amd64 .

My monitor is Philips 190S. I think is [this]("https://www.pcliquidations.com/p11593-philips-190s-grade-c") (I have white, but does not matter).

[/FONT][/SIZE][h=1][SIZE=2][FONT=arial]Intel Haswell Refresh, Core i7 4790 3.6GHz box[/FONT][/SIZE][/h][h=1][SIZE=2][FONT=arial]GIGABYTE GeForce GTX 970 OC WindForce 3X 4GB DDR5 256-bit[/FONT][/SIZE][/h][h=1][SIZE=2][FONT=arial]Crucial Ballistix Tactical 8GB DDR3 1600MHz CL8 1.5V[/FONT][/SIZE][/h][h=1][SIZE=2][FONT=arial]ASRock H97 PRO4[/FONT][/SIZE][/h][h=1][SIZE=2][FONT=arial]WD Blue 1TB SATA-III 7200 RPM 64MB[/FONT][/SIZE][/h][h=1][SIZE=2][FONT=arial]Gembird 1x DVI-A Male - 1x VGA Female[/FONT][/SIZE][/h][SIZE=2][FONT=arial]
This are the mains. If it needs something else, just say.[/FONT][/SIZE]

---

### Post by mörgæs on 2015-09-22
> **andrei23 said:**
> But my monitor isn't able to show anything higher than 1280 x 1024.

The monitor is built with this ^ as maximum resolution, as can be seen in the link you posted. There is no point in trying to set a higher resolution.

---

### Post by andrei23 on 2015-09-22
I am not trying to do this. Ubuntu does when I try to install it (ubuntu):/ .

---

### Post by Vladlenin5000 on 2015-09-22
What connection are you using? Those issues seldom - if ever - occur in digital. Your monitor has DVI and so has your graphics card. That's what you should be using.

(EDIT)

No need to answer.
> **[SIZE=2][FONT=arial]Gembird 1x DVI-A Male - 1x VGA Female[/FONT][/SIZE]**
^^^^
This is your problem!

---

