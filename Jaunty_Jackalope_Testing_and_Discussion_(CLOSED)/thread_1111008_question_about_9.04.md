---
title: "question about 9.04?"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cptrohn on 2009-03-30
Will it support the AR242x card out of the box?

Anybody testing it use that card?

---

### Post by Bachstelze on 2009-03-30
Moved to Jaunty Testing.

---

### Post by cptrohn on 2009-03-30
So nobody is testing with this card at all???

I would just like to know in advance if it is going to be an issue if I upgrade to 9.04,  I've seen screenshots of it and it looks really nice.... I just don't want to go through a lot of problems with the wireless card if I go ahead and update when it releases.

---

### Post by olskar on 2009-03-30
Hm, if you burn a livecd or make a liveusb you can try it yourself? :)

---

### Post by cptrohn on 2009-03-30
> **olskar said:**
> Hm, if you burn a livecd or make a liveusb you can try it yourself? :)

Is it ready to do that?

I'm pretty new to linux and didn't know if everything was ready or not for that...    I'm really not a programmer or anyhthing like that.. (but I'm learning more and more everday....thanks to linux..)

---

### Post by andrewabc on 2009-03-30
> **cptrohn said:**
> Is it ready to do that?

I'm pretty new to linux and didn't know if everything was ready or not for that...    I'm really not a programmer or anyhthing like that.. (but I'm learning more and more everday....thanks to linux..)

Definitely. If you want to know if Jaunty 9.04 will work "out of the box" for you, burn a live-cd. Preferably use a cd-rw if you have one laying around, because for each new release to test you will be burning a new version. Instead of having lots of old cd-r with old version on it.

Download the beta livecd, burn to cd, restart computer, hopefully it will detect the livecd (if not BIOS options might need to be changed to allow booting from cd drive). Once it starts booting you will get first option "start ubuntu without affecting your system". Do that, and hopefully it will work. **Do not** go through with "install" icon on desktop.

Once running you should be able to tell what works and what doesn't work with your computer. Mess around with everything, to make sure stuff works (such as your wireless). Shutdown and take cd out of cd drive and then you will go back to your windows or whatever.

Get the beta from here:
[http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)
Once you read everything there, click on
[http://releases.ubuntu.com/releases/9.04/](http://releases.ubuntu.com/releases/9.04/)

And most likely you should try this file specifically *PC (Intel x86) desktop CD*:
[http://releases.ubuntu.com/releases/9.04/ubuntu-9.04-beta-desktop-i386.iso](http://releases.ubuntu.com/releases/9.04/ubuntu-9.04-beta-desktop-i386.iso)

Unless you know your computer supports 64 bit, then get 64-bit PC (AMD64) desktop CD.

---

### Post by cptrohn on 2009-03-30
Ok, thanks alot for the information... I use kubuntu so I will give that a try with the alternate install link...  Hopefully it works for me.. thanks a bunch.

---

### Post by Marat89 on 2009-03-30
you need the Desktop CD ;-)
I would prefer to test with the Ubuntu (Gnome) Beta CD, I think its more stable as KDE 4.2

---

### Post by Bakon Jarser on 2009-03-30
I think Marat is right.  I've never downloaded it but I don't think the alternate install works as a live cd.

---

### Post by cptrohn on 2009-03-30
> **Marat89 said:**
> you need the Desktop CD ;-)
I would prefer to test with the Ubuntu (Gnome) Beta CD, I think its more stable as KDE 4.2

LOL darn it!!

Well I guess I will just have them both on disk then.....LOL Told ya all I was still wet behind the ears with linux...:lolflag:

---

### Post by cptrohn on 2009-03-30
> **Bakon Jarser said:**
> I think Marat is right.  I've never downloaded it but I don't think the alternate install works as a live cd.

Ok thanks.... I guess I will have 3 disks now...:lolflag:


I'll get the hang of this one day and be a pro someday.:)

---

### Post by Marat89 on 2009-03-30
hey, i hope your hardware will work ;-)
but instead of wasting CD-R you could use CD-RW´s or try the USB stick version of ubuntu.
Or: Why dont you use Virtualbox, its secure and you can easily test all features

---

### Post by cptrohn on 2009-03-30
> **Marat89 said:**
> hey, i hope your hardware will work ;-)
but instead of wasting CD-R you could use CD-RW´s or try the USB stick version of ubuntu.
Or: Why dont you use Virtualbox, its secure and you can easily test all features

Thanks, I do have to go to the store and have been meaning to get a USB stick anyway, today might be the day to do it... I have never tried virtualbox, but am open to trying anything out and will give it a shot as well.

Thanks for all the help and good ideas everybody.

---

### Post by andrewabc on 2009-03-30
> **cptrohn said:**
> Thanks, I do have to go to the store and have been meaning to get a USB stick anyway, today might be the day to do it... I have never tried virtualbox, but am open to trying anything out and will give it a shot as well.

Thanks for all the help and good ideas everybody.

If you are planning on using kubuntu, there are kubuntu livecds. Do not get the alternate cd, as that is install only.

Direct link to kubuntu beta 32bit:
[http://releases.ubuntu.com/releases/kubuntu/9.04/](http://releases.ubuntu.com/releases/kubuntu/9.04/)
[http://releases.ubuntu.com/releases/kubuntu/9.04/kubuntu-9.04-beta-desktop-i386.iso](http://releases.ubuntu.com/releases/kubuntu/9.04/kubuntu-9.04-beta-desktop-i386.iso)

To get some first hand info on liveusb, I tested it for first time this week, and here are my results:
[LiveUSB faster than liveCD and other liveusb questions](http://ubuntuforums.org/showthread.php?t=1107298)
Summary: USB is much faster to use than livecd. Much better for testing assuming it works.
You will need 1gb usb stick minimum. If you shop online oczrally2 is one of best to get. Check out reviews. brick and mortar stores will sell overpriced slow usb sticks, I've bought 3 of them over the years :(

---

