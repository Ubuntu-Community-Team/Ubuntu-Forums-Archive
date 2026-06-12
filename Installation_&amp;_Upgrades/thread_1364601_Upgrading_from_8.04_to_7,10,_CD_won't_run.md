---
title: "Upgrading from 8.04 to 7,10, CD won't run"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by menace101 on 2009-12-26
So I just downloaded the 9.10 image from my Windows computer (the Linux machine doesn't have internet access), and burned that onto a CD. I tested the CD by rebooting my Windows to make sure it burned correctly and I was able to run 9.10 fine. When I put the CD into the 8.04 machine, however, I hit "Try Ubuntu without changing your computer" and nothing happens. It just goes to a black screen. Same with "Install it." I'm not sure what I did wrong. 
Any help is appreciated!

I just realized I made a typo in the heading. I meant 9.10. Sorry!

---

### Post by tommcd on 2009-12-26
> **menace101 said:**
> ... and burned that onto a CD. I tested the CD by rebooting my Windows to make sure it burned correctly and I was able to run 9.10 fine....
When you say you "tested the CD" did you run the option that says "check disc for defects"? If you did not run that then you should. That is always the first thing you should do, especially when you have problems like this. It will help us to at least rule out a bad CD. So check the CD for defects and report back.
If you are burning the CD from Windows, I would use Iso Recorder or Infra Recorder, and be sure to burn the CD at the slowest possible speed:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by menace101 on 2009-12-26
How imperative is it that I burn at a slow speed? 

And yes, I did check for defects and the like.

---

### Post by Hashimi on 2009-12-26
Don't burn the CD with Microsoft Software. Try any other software. I also faced with this problem before.

---

### Post by menace101 on 2009-12-26
Well, I'm using Alcohol 120%... I hope that's sufficient?

---

### Post by menace101 on 2009-12-26
Alright, so I tried again with another CD-R.. burned it as slowly as possible using Alcohol 120%, again, nothing.

---

### Post by Hashimi on 2009-12-26
I burned the CD in my win 7 and had the same result. So i tried in my friends Windows Vista using Nero and it worked. Definitely don't know the reason, but this was what i did. I hope it help you solve your problem.

---

### Post by tommcd on 2009-12-26
> **menace101 said:**
> Alright, so I tried again with another CD-R.. burned it as slowly as possible using Alcohol 120%, again, nothing.
Did you run the option to check the CD for defects?
Burning the CD at the slowest speed will minimize the possibility of data corruption on the CD. Burning an iso image of an operating system is much more exacting, and less tolerant of errors, than burning a music CD or data CD. Each and every file on the CD has to be right.

---

