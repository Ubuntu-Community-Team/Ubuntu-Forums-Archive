---
title: "please help"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by diabloSW on 2007-02-06
I`m new here,so first Id like to say hello to everyone here.):P My problem is trying to install ubuntu 6.06 LTS on a dell inspiron 2500 laptop.It has an Intel celeron 900Mhz processor,128 megs RAM,an a 10 gig hd.This computer has no operating system.I ordered the live cd.The cd boots fine,I select start and it starts fine but shortly ends up at a light blue screen with faint multicolored vertical lines all the way across the screen.The cd still runs and the hd is still being accessed.I get no messages or errors that I can see.eventually every thing stops and the screen stays the same.I tried booting in the safe graphics mode and get to the desktop,but the only icons are on the corners and I cant click on any of them.This same computer will run puppy linux with no problems.I dont know much about computers,and have only used windows.Any help anyone can offer would be greatly appreciated.

---

### Post by m.musashi on 2007-02-06
I'm no expert either but my first guess is a graphics problem. I can't remember with the 6.06 version if there is a text mode install. If so, try that. It may be that you have to pass some command at the boot prompt. Does anything give you that option? I think there is a F button to push for other options. Sorry I can't be more specific. I'll have to dig out a disc and try it to be sure. Anyway, if you can do a text install that might get you past the problem section. Once installed we can help you set up the graphics. With the specs on that computer you might also consider a server install and then installing a light window manager. XFCE is a popular one and I think many people on the forums like fluxbox, openbox, icewm among others. The server install might be the way to go at first. It isn't just for servers. It just installs the minimun needed and you can add to it to get what you want.

Xubuntu is a version with XFCE for the window manager but since you ordered the disc my guess is you don't want to download something else. Try the server instal first.

---

### Post by SoloSalsa on 2007-02-06
> **diabloSW said:**
> It has an Intel celeron 900Mhz processor,128 megs RAM,an a 10 gig hd.
It's fast enough, but you have half the necessary ram.  It is not possible to install live on such a system.  You could use Ubuntu, but you would need to install from the alternate cd.
However, I think you **should** be able to run it live okay (just not as far as installation).  I have had a similar problem on a 500 MHz celery, 256 MiB.  I use that computer with DSL (Damn Small Linux), because It was not worth it to use Ubuntu on such old hardware...  Anyway, that graphics problem...  I used a Dell Dimension desktop...  But maybe there is some correlation between Celerons + Intel integrated graphics?
If you want the Ubuntu family, the best to use would be Xubuntu, but otherwise, there just isn't enough ram.

---

### Post by SoloSalsa on 2007-02-06
Oh yeah, you had to order the disk...  I could mail a Xubuntu alternate installer if you really want, but again, with that ram, I really recommend something little, like Puppy...

---

### Post by m.musashi on 2007-02-06
Yeah, I just pulled a 6.06 CD and there isn't an option for a server install. I think that is when they went with the alternate CDs SoloSalsa mentioned. I did install an older version of Ubuntu (5.10) on some old laptops. I don't remember the specs but they shipped with Windows 98 so that should give you an idea. It took forever to do the install and once installed it moved slower than molasas. It took nearly 5 minutes for open office to open - of course that's not a light program. Do you have the option of upping the memory?

---

### Post by diabloSW on 2007-02-06
Thanks for the replies.Im thinking of doublling the ram cause I want to use that machine to try different versions of linux.I downloaded the xunbuntu ISO and burned using burncdcc but got the message invalid compressed format( err=2) system halted.I guess I didnt burn it right.I also dont have a clue how to do a text install,windows is all Ive ever used.I downloaded puppy and it works great,I just want to try a full distro to hopefully replace the evil money pit OS.:lolflag: I might try the server install,but maybe Ill just stick with puppy for now.Im really glad I found this forum,seems like everyone is really helpful.

---

### Post by m.musashi on 2007-02-06
The server install is very easy. It's basically the same except you don't have quite the nice GUI interface. Other than that, one it starts installing you just sit back and watch. You will not get a graphical desktop though. You will have to install that as well from a command line. If you have the Xubuntu CD then there probably isn't much point to the server install. Some people recommend it to get the lightest weight install but once you add the XFCE desktop or gnome or whatever you end up with something similar.

As for the forum, it's great. I came to Ubuntu a little over a year ago with no knowledge at all. It's only because of this forum that I am not running Ubuntu about 95% of the time. I still have a lot to learn but I try to give back when I can since so many people have been so helpful to me - and continue to be.

---

### Post by diabloSW on 2007-02-06
Ill have to download xubuntu and burn it again. Ilove the idea behind linux.Why should you have to pay a fortune for software,when you had to pay so much for the hardware.As long as I can find a distro that does close to what windows does Ill be happy.And this seems like a great place to learn.

---

### Post by m.musashi on 2007-02-06
Burn it as slow as you can. It used to be an issue. I don't know if it still is but it can't hurt.

---

### Post by SoloSalsa on 2007-02-08
Just be absolutely sure your doing it right:  it should be the 'alternate' cd.  Would you tell us how you burned it?
Don't worry, it is not that hard or complicated.  Just instead of windows on a desktop, it's basic-color text-only screens, and you use keyboard arrow keys...  The hardest thing is partitioning, but just ask, and we'll get you past.
And m.musashi, it definitely does take a long time.  When I used the alternate on 500MHz, 256MiB, it took about forty-eight minutes.

---

### Post by m.musashi on 2007-02-08
> **SoloSalsa said:**
> And m.musashi, it definitely does take a long time.  When I used the alternate on 500MHz, 256MiB, it took about forty-eight minutes.

Was that for a server install? That's not too bad. I tried to install 5.10 (full version with gnome and all) and it took about 5 hours and the resulting install was just about useless. However, it did install and work. I could not get win98 to work at all - no drivers any more... In the end, I scrapped it and installed DSL instead. That worked a lot better.

---

