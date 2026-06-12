---
title: "Touchpad Clicks *not sensitive enough* (karmic)"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mobrien118 on 2009-10-19
Hello,

I took it upon myself to install Ubuntu on my fiance's laptop. I was hoping she would be pleasantly suprised by the increase in speed, reliability and ease of use, but instead I was shocked to find her extremely frustrated!

The issue is the sensitivity of the touchpad **clicks**. She is used to gently brushing the touchpad to incite a click action, but now she has to tap it pretty hard, which leads to inaccurate clicks and frustration when the cursor moves and clicks something else.

I am sure there is some way to adjust it, and I even found some old threads on how to make it *less* sensitive (but no one asking for more, like me), but most of them had something to do with editing the xorg.conf file. Since I know there has been a dramatic shift away from using xorg.conf, and since this is Karmic Beta (installed through Wubi as Jaunty, then upgraded), I was hoping to get some updated information on how to accomplish this.

I am hoping to make a Ubuntu convert out of her yet, if I can just overcome these relatively minor interface issues...

Thanks so much!

--mobrien118

P.S. The system is a Dell Inspiron E1405 laptop.

---

### Post by P4man on 2009-10-19
xorg.conf is still your friend for tweaking stuff like that.
I think the option you want to tweak here is 

```
Option "FingerHigh"
```
I got no idea how much to set it though
google on it. 

more tweaks here:
[http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html](http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html)
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by mobrien118 on 2009-10-19
> **P4man said:**
> xorg.conf is still your friend for tweaking stuff like that.
I think the option you want to tweak here is 

```
Option "FingerHigh"
```
I got no idea how much to set it though
google on it. 

more tweaks here:
[http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html](http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html)
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

OK, I also just was looking through Synaptic and found that "gpointing-device-settings" is the successor to "gsynaptics" for touchpad option management. There is also a package, besides these two, called "tpconfig" that looks like it has similar functionality. Can anyone speak to the effectiveness of these tools?

Thanks P4man for the advice. I'll try tweaking this parameter if I can't find an appropriate GUI tool (that she can easily adjust when I'm not around) that does the job.

Thanks so much for the lightning fast response!

--mobrien118

---

### Post by iTheBadGuy on 2009-10-19
If you are trying to convert her into a Ubuntu user, then you should of installed Jaunty, it's not always a good idea to try and convert users with a beta form of Ubuntu :P.

I converted my mother to a Ubuntu user about 4 months ago, and she can't live without Add/Remove. Her laptop didn't have any problems with the sensitivity.. i installed jaunty tho..

I don't like using betas to showoff Ubuntu, you never know what can go wrong and embarrass you :P

---

### Post by mobrien118 on 2009-10-19
> **iTheBadGuy said:**
> If you are trying to convert her into a Ubuntu user, then you should of installed Jaunty, it's not always a good idea to try and convert users with a beta form of Ubuntu :P.

I converted my mother to a Ubuntu user about 4 months ago, and she can't live without Add/Remove. Her laptop didn't have any problems with the sensitivity.. i installed jaunty tho..

I don't like using betas to showoff Ubuntu, you never know what can go wrong and embarrass you :P

I hear ya, and couldn't agree more, but one of the BIG requirements was being able to go back to Windows and forth to Ubuntu seamlessly, which meant using "Weave" in Firefox, which meant using Firefox 3.5, which is MUCH less than an optimal setup in Jaunty. Because of this, I was going to wait for at least RC, but she was out of town for 2 weeks, which was the perfect opportunity for me to "surprise" her with it.

Ultimately, I am running Karmic beta on 4 systems I own and still have Jaunty on 3 others, and Karmic beta has actually been more stable and had less bugs than I have existing and unresolved on my Jaunty systems. Honestly, I had a Jaunty fresh install on one of them that wouldn't boot into the GUI, but updating through "apt-get upgrade -d" brought the system back to life. So, yeah, I trust a beta *this time* :-)

--mobrien118

---

### Post by P4man on 2009-10-19
> **mobrien118 said:**
> I hear ya, and couldn't agree more, but one of the BIG requirements was being able to go back to Windows and forth to Ubuntu seamlessly, which meant using "Weave" in Firefox, 

check out [xmarks]("http://www.xmarks.com/"), 
Synchs IE, firefox, chrome and safari across OSs and PCs.

---

### Post by psyke83 on 2009-10-20
One setting that may help is "FastTaps".

You can set it like so:
```
$ synclient FastTaps=1
```

Without this, it seems to take half a second for taps to register, which I find irritating. With this setting enabled, touchpad taps register immediately.

---

