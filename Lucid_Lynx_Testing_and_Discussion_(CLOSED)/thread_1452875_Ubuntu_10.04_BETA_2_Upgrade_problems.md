---
title: "Ubuntu 10.04 BETA 2 Upgrade problems"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by James2k on 2010-04-12
Im currently running Ubuntu 9.10, running latest updates. I've just tried to upgrade to Lucid 10.04 through update manager via "update-manager -d" and the upgrade always fails at this point with the same error:

[http://img408.imageshack.us/img408/9660/lucidbetaerror.png](http://img408.imageshack.us/img408/9660/lucidbetaerror.png)

I have made sure everything is up to date as well as running the various sudo commands to clean the system of packages. I also went into recovery mode and selected repair broken packages, but nothing is broken and nothing is changed.

Wondering if anyone else has had the problem and hopefully a fix :D!

Thanks,

---

### Post by uRock on 2010-04-12
I haven't heard any success stories of anyone using upgrade feature. Clean installs seem to be the way to go for now.

Cheers,
Ronnie

---

### Post by James2k on 2010-04-12
I'll guess I'll hold off to the final release then if the problems with upgrading aren't just me, just wanted to get a preview of 10.04 because it's looks really good :D

---

### Post by uRock on 2010-04-12
> **James2k said:**
> I'll guess I'll hold off to the final release then if the problems with upgrading aren't just me, just wanted to get a preview of 10.04 because it's looks really good :D

I am loving it. I ran the upgrade a few weeks ago and it killed my system. I am currently testing on two machines and though there are bugs to be fixed yet, it is looking great. It will no doubt be an awesome release.

---

### Post by James2k on 2010-04-12
Oh thanks, don't rub it in :P

Just kidding, ah well only 17 more days to go still the final release :)

---

### Post by dannyboy79 on 2010-04-12
i can also ateast to the fact that I had a very stable machine (1 out of 3) running karmic freshly. i tried to do an upgrade using either the alt-cd and also the update-manager -d, it always failed also. it said that it couldnt be upgraded. but my other 2 machines were upgraded jsut fine. not sure what the deal was. and since there was no customization on that machine I didn't care about wiping and starting fresh. it's a mythtv-frontend in the family room. i now think back and wish I would've troublshoot it because i am sure it's just some file somewhere or maybe we got stuck in that partial upgrade loop problem. who knows.

---

### Post by dochood on 2010-04-12
I had exactly this same problem.  Then, when I tried to install from my 9.10 x64 disk, I had some other whacky problem.  I installed from 9.04 x64, and it worked.  I had to upgrade it to 9.10 to get back where I was.

I have 10.04 in a virtual machine running just fine.  I'll probably just run it that way until about 2-3 months after the release.  I seem to have trouble with EVERY new Ubuntu version that comes out.

---

### Post by dochood on 2010-04-12
Oh, and I had the same "Grub Error 15" that everyone is getting when trying to install from CD.

---

### Post by uRock on 2010-04-13
I guess I have been lucky then. (knocks on wood)

---

### Post by geekwanabe on 2010-04-13
I upgraded from Karmic 64 to Lucid 64 last week and it's working great.  I love it!

---

### Post by uRock on 2010-04-13
Awesome, first one I have read about. :)

---

### Post by James2k on 2010-04-13
I just hope this is all fixed on the final release!

**Edit: I just tried the upgrade this morning and it works! I got past the Setting new software channels**, [B]currently it's getting new packages, so it's must of been a glitch! I haven't even changed anything configuration wise either, but im not complaining Ubuntu 10.04 BETA here I come :D
[/B]

---

### Post by beta.tester on 2010-04-13
> **uRock said:**
> Awesome, first one I have read about. :)

Make that 2 you have heard about :)

Something else I have noticed helped?

System => Administrations => Software Sources => Download From => Other => Select best server --- This does a ping test on all server sites for Ubuntu and selects the best for you :) 

I had mine on Main Server and a few times had problems till I got the correct server. It maybe coincidental but running 10.04 here with kernel -10 and all looking well :)

As always,** this is beta software so CAUTION :) **

Keep on Ubuntuing and kind regards     john

---

### Post by beta.tester on 2010-04-13
> **James2k said:**
> I just hope this is all fixed on the final release!

**Edit: I just tried the upgrade this morning and it works! I got past the Setting new software channels**, [B]currently it's getting new packages, so it's must of been a glitch! I haven't even changed anything configuration wise either, but im not complaining Ubuntu 10.04 BETA here I come :D
[/B]

Hi

You did try:

System => Administration => Synaptic package Manager => Edit => Select "Fix broken packages" and "mark all upgrades" and then applying?

Keep on Ubunuting and kind regards     john

---

### Post by Chianti on 2010-04-13
I have exactly the same problem although the kernel in use is  2.6.31-21-generic installed from karmic-proposed. The solution above didn't work.

---

### Post by James2k on 2010-04-16
Well now that im in the BETA 2 club I can honestly say Ubuntu 10.04 is looking good. Can't wait till the 29th :D.

One problem I've found (slightly humourus) is my WLAN light is having a disco, im on a Compaq Presario CQ60 307-EA and my WLAN light is now blue (Where as before it was constantly orange as if it was off) but it frequently flashes blue and orange, though I've seen other HP users report similar issues so Im not alone hopefully it can be fixed in future updates, if not DISCO LAPTOP.

---

### Post by nanog on 2010-04-16
> I haven't heard any success stories of anyone using upgrade feature. Clean installs seem to be the way to go for now.

I upgraded 7 boxes with only minor problems (dependency issues with flash mostly).

---

