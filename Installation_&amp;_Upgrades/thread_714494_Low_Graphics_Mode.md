---
title: "Low Graphics Mode?"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by d_unit91 on 2008-03-03
Alright, I just got a new computer, customized  by myself. I got all the hardware installed and working, and started up my Live Disc of Ubuntu. I had to run the computer off the integrated graphics of the motherboard, because for some reason it wouldn't pick up my card. When I started the Live Disc, I went to the first choice, as always (Start or Install Ubuntu), and it started loading. When it ended the loading screen, a window popped up saying that my graphics card and monitor could not be found correctly, and that it was running in low graphics mode. From there I could A. Configure B. Shut Down or C. Continue. I've tried all three, and none have gotten me anywhere. Trying Continue and\or Configure (and configuring the monitor and G card) brought me to a black screen with 4 lines of code saying:
```

* Starting deffered execution scheduler atd         [OK]
* Starting periodical command scheduler crond       [OK]
* Checking battery state . . .                      [OK]
* Running local boot strips (/etc/rc.local/)        [OK]
 
```

How do I install Ubuntu, or change the settings so that I can start up the desktop mode of Ubuntu?

---

### Post by Losgann Mor on 2008-03-03
I'm building a new system and this *exact* same thing happened to me today when I tried to install Ubuntu 7.10. So now there are two users with the same question! :)

---

### Post by d_unit91 on 2008-03-03
Hopefully someone can help us, but for now I'm off to bed.

---

### Post by empthollow on 2008-03-03
First, i have to ask what kind of video card is ubuntu not seeing.  and second, try disabling your onboard video card in the bios settings.  Third, something else to try would be passing a kernel option, this is a pretty common fix.  i think the kernel name is live.
```
live vga=771
``` 
there are a number of kernel options you can try.  These problems generally only happen on the live disc for some reason.  once you install the system the issues seem to disappear.  The other option is to avoid this situation by using the alt-install cd.  it is an installer only.

---

### Post by Losgann Mor on 2008-03-04
In my case, I *am* trying to use the onboard video (I built my system on a tight budget, and was planning to use the onboard video until I can save up enough for a good graphics card later). I'm using a Biostar motherboard with NVIDIA GeForce 7025 onboard video chipset, if that's any help. But in any case thank you for the tip about trying the alt-install CD, I'll give that a go today and see what happens.

EDIT: I burned an alt-install CD and it worked! Ubuntu installed no problem. (I've got other issues now, such as no internet connection despite the fact that I have an internet connection, but at least the install went fine. :))  Thanks empthollow!

---

### Post by d_unit91 on 2008-03-04
Alright, first: I am running a GeForce Nvidia 6600 card, second: the only command similar to that in my bios is 'Disable Internal If Ext GPU Is Not Present', and third: how do i "pass a kernel"?

Also, I don't have the connection speed to download an alt-install disc, and I don't have on already, so that idea is probably not going to work.

EDIT: I am using the same motherboard as tmleigh (based on the 7050 chipset, and from Biostar).

---

### Post by empthollow on 2008-03-04
ok, when the cd boots, press F6 at the options screen.  you will see a bunch of text appear, at the end of that text.  
```
vga=771
```  
other things that have helped me boot live cds that are kernel options.  they would be entered the same way as above.  
```
irqpoll
```
```
noapic
```
there is also a vga menu if you press f4 and you can choose your resolution.
another simple option is to choose the start in safe graphics mode option
if you can get it to boot the correct card can be reconfigured after installation.  
good luck.

---

### Post by d_unit91 on 2008-03-05
yea, after looking closer, i think its the motherboard that is not recognizing the card, not ubuntu. i will try the other kernel options, but is there any other way to boot it to the desktop, just off my intgrated graphics?

---

### Post by empthollow on 2008-03-05
some of those kernel opts or safe graphics mode should use the default graphics card.  the live disc will look to find a video card and choose one automatically, - i'm not sure of how it does that maybe a bios setting???-.  if you want, you might try installing without the nvidia card and once it is install boot from the hard drive and configure ubuntu to use the new card.

---

