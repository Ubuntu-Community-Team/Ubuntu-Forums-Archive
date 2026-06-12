---
title: "Motion M1300 Questions"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by BlindFate on 2007-04-21
I have a Motion M1300 Tablet PC that I use for when Im not at home, and the WinXP Tablet Edition has recently, well died. I was hoping to have a few questions answered, and I appreciate all responses.

1) Will Ubuntu x86 architecture operate on the Tablet?
2) Should I use Dapper or a different build?
3) If I were to install it from a different PC then replace the harddrive into the original computer, would it work?


Thanks! My experience in Linux is very limited, but I do want to learn.

Edit: Mobile Intel® Celeron ® M 800Mhz ULV processor is the processor

---

### Post by priegog on 2008-04-06
Sorry I'm a little late, but I just bought one of these on ebay, so I'd better get this thread revived. To answer your questions:
1) Most probably yes
2) I'm gonna try the hardy beta
3) Yes, and that is pretty much the only method that would work, since this computer is from 2003 when I think booting from a USB drive was not standard.

Edit: I will try and put ubuntu on it, so if this thread gives signs of life I will post my findings here.

---

### Post by xdata666 on 2008-04-29
I have used an m1300 with feisty somewhat successfully in the past (got the pen interface working). I ended up not having time to mess with it so it sat around as a TV pc (ha ha). Just installed hardy LTS on it today.

---

### Post by priegog on 2008-04-29
Oh man, I'd love it if you could point us in the right direction as to how you got the pen interface working. Also, a TV pc is not that bad in my oppinion :D

---

### Post by andrewPCT on 2008-05-18
As I write this, I am currently installing 8.04 onto a M1300 (I was able to pxe boot the machine for the install).  I'm glad to hear that people have had success with the pen.  Right now my other concern (just because of my luck with getting Broadcom wireless cards on other machines) is wireless.  Will this work without much fiddling?

---

### Post by priegog on 2008-05-19
Hi. First off, I just wrote a guide for it in [this other thread.]("http://ubuntuforums.org/showthread.php?p=4972622#post4972622") I suppose you will be installing with an external USB cd drive (the easiest way by far, ltho the method doesn't really matter). As for it having a broadcomm, I really don't think so, these machines come with that "centrino" thinguie wich means even the wifi is from intel, which should work out of the box. Mine did at least. But if it doesn't for you, by all means keep asking because I DO have another laptop with a broadcomm wireless chip and I have it working just fine. Good luck.

---

### Post by andrewPCT on 2008-05-19
A bit of an update, I had run the install by PXE booting the unit (I learned how to do that...) as I didn't have a USB cd drive (nor did I have the patience to wait a day or two for one from Newegg).

I was shocked (in a good way) to see Compiz working and enabled by default.

Wireless appears to be working flawlessly (first time I've ever had wireless working flawlessly in Ubuntu).

I'm kind of bummed that the battery is only holding 39%, but I can't complain as I'm probably the 3 or 4 owner of it and I received it for free.

Now I'm off to your Howto.  Thanks for it.

---

### Post by priegog on 2008-05-19
yeah, its a great machine... Writing from it :D

---

### Post by andrewPCT on 2008-05-19
I was following your howto, and unfortunately didn't see the feedback from the pen test, I'm wondering if something is off or if it's just my luck.  I know that the pen worked when I was changing the boot order in the BIOS.

Update: After following the rest of the tutorial, (since I wasn't about to admit defeat), I rebooted, and upon reboot, the pen was working. Thanks a lot for the tutorial.

---

### Post by andrewPCT on 2008-05-19
I curious how hot-dockable the unit is while running Ubuntu.  Can I just drop it on/remove it from it's dock while it's running?

---

### Post by priegog on 2008-05-19
I'm glad you got it to work. The how-to is a work in progress, as I continue my quest to make it work perfectly (things to figure out include the eraser [which I'm sure is just a stupid command away] and a way to change the backlight's brightness [that one is KILLING me!]) If you ever figure any of those things out before myself, please post right there in that how-to with the solution. 

> **andrewPCT said:**
> I curious how hot-dockable the unit is while running Ubuntu.  Can I just drop it on/remove it from it's dock while it's running?

I would have no idea, since I bought mine without the dock. What's the dock good for, besides adding more ports and recharging? (My first guess would be that everything would work just fine?)

Edit: Oh, BTW, I got a battery for it on ebay, not too expensive (less than $45 if I remember correctly). Altho for some reason the charge state is not correctly recognized and when fully charged it says it's at 50% (but it still lasts a good 3+ hours) [Here's an ebay search for the kind you need]("http://search.ebay.com/search/search.dll?from=R40&_trksid=m37&satitle=BAT0016&category0=")

---

### Post by andrewPCT on 2008-05-19
The dock that I have came with it.  It really doesn't add any extra ports, but it does hold the unit upright, and allows for 90 degree rotation.  I'm using the rotation scripts that you provided in the howto, but was wondering if there is a way to also 'rotate' the input from the arrow pad on the unit.

I'm currently using matchbox-keyboard ([http://matchbox-project.org/?p=1](http://matchbox-project.org/?p=1)) as an on-screen keyboard, which unfortunately is in early stages of development, and hasn't seen a commit for over 3 months.  The only problem currently is that there is keyboard for the login screen.  (Then again, I only know my password by touch.)  Also, is it possible to make us of the other buttons on the unit.  I have no idea what they were intended for (all they are labeled by are shapes...), but I have had one of them open up Firefox.

---

### Post by priegog on 2008-05-19
I use cellwriter as an input app (it can also become a keyboard). I have auto-login enabled, so I don't need it to be enabled at that time, but that problem has been solved elsewhere on the forum. Feel free to add it to the how-to if you find it and make it work. The buttons should be fairly easy to assign and remap (when rotating), but that's not as high a priority for me as, say, the backlight issue.

---

### Post by priegog on 2008-05-22
Just to let you know, I edited my last post on the other thread with instructions to change the backlight.

---

### Post by sarah.fauzia on 2008-06-24
> **priegog said:**
> I'm glad you got it to work. The how-to is a work in progress, as I continue my quest to make it work perfectly (things to figure out include the eraser [which I'm sure is just a stupid command away] and a way to change the backlight's brightness [that one is KILLING me!]) If you ever figure any of those things out before myself, please post right there in that how-to with the solution. 



I would have no idea, since I bought mine without the dock. What's the dock good for, besides adding more ports and recharging? (My first guess would be that everything would work just fine?)

Edit: Oh, BTW, I got a battery for it on ebay, not too expensive (less than $45 if I remember correctly). Altho for some reason the charge state is not correctly recognized and when fully charged it says it's at 50% (but it still lasts a good 3+ hours) [Here's an ebay search for the kind you need]("http://search.ebay.com/search/search.dll?from=R40&_trksid=m37&satitle=BAT0016&category0=")

I noticed your comment about the eraser, and I do have a fix for it. It just involves changing one of the buttons, just like we have to change a button to enable the right-click, in the xorg.conf file. Add this in your eraser section:

```

Option "Button1" "2"

```

Really was just one command away. I spent a night trying to figure it out! The answer is always simpler than the method to it... (I have a Motion LE1700 so it should work for you. Your method for configuring your Motion M1300 pen worked for me!)

---

### Post by sarah.fauzia on 2008-06-24
Unfortunately, I should add, your method for screen rotation didn't work for me. I had to disable the script because it disabled my compiz! (And I'm using compiz for many things, most importantly, the annotate plugin). Do you possibly have a fix for it?

And as for screen brightness, it hasn't been bothering me at all. Is your screen too dim? Or do you want some way of configuring its settings?

---

### Post by priegog on 2008-06-24
Thanks, I'll try the eraser fix soon. As for the screen brightness I did fnid a fix but have yet to recollect my toughts and put it in my other thread (If you are interested I'll get right on it tomorrow as soon as I finish my last test).
I don't have a fix for the screen rotation thing. Since the M1300 is so underpowered I do not have compiz enabled, but I do see how compiz wouldn't play nicely with xrandr. MAYBE a fix will come in later releases of compiz/ubuntu (just like they did for the interaction between WINE and compiz), but I wouldn't expect them to come very soon. You're gonna have to google that one as I'm sure you can't be the only one who needs that to work. But as I said, come tomorrow I can even help you out with that. Just let me know

---

### Post by sarah.fauzia on 2008-06-25
> **priegog said:**
> Thanks, I'll try the eraser fix soon. As for the screen brightness I did fnid a fix but have yet to recollect my toughts and put it in my other thread (If you are interested I'll get right on it tomorrow as soon as I finish my last test).
I don't have a fix for the screen rotation thing. Since the M1300 is so underpowered I do not have compiz enabled, but I do see how compiz wouldn't play nicely with xrandr. MAYBE a fix will come in later releases of compiz/ubuntu (just like they did for the interaction between WINE and compiz), but I wouldn't expect them to come very soon. You're gonna have to google that one as I'm sure you can't be the only one who needs that to work. But as I said, come tomorrow I can even help you out with that. Just let me know

I'm curious; how do you manipulate the screen brightness now? Is it something manual through the terminal, or a GUI? At the moment, Ubuntu tells me I only have 2 hours and 10 minutes of battery...at 100 percent charge (and I have an extended battery!), so I really should be looking into more ways of getting the best of the the battery (like by lowering the brightness). A fix would be appreciated, but at whatever time is suitable for you. Again, thanks.

---

### Post by priegog on 2008-06-25
I did it. It's [in this thread.]("http://ubuntuforums.org/showthread.php?p=5258166#post5258166")
If for some reason those instructions don't work for you, let me know and I'll help you figure it out, as the acpi path to change the screen brightness is different for all laptops. 
About your other issue, from my research it seems to be a very well known bug, so make sure to [vote this ubuntu brainstorm idea,]("http://brainstorm.ubuntu.com/idea/4161/") [vote on this bug to give it more priority,]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/132065") and [check out this post]("http://ubuntuforums.org/showthread.php?t=581947"), as it might work for you, even tho it's not exactly the same situation. 
Good luck!

---

