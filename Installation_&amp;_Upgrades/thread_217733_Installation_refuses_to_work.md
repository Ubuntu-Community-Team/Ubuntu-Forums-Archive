---
title: "Installation refuses to work"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by Aranel on 2006-07-17
Hi. I'm pretty much a newb to Linux in general, though I have been using it for about two months. I started out with a dual boot of Windows XP and Mandriva One v2006.0 on my laptop, which worked okay. However, I soon grew tired of the distribution's obsolete software packages and tendency to screw everything on my computer up whenever I try to update something. Finally, after it crashed my computer for the fourth time when I attempted to upgrade KDE - to a *non-current* version, I might add - I decided that that was the last straw.

So last week, I tried out SuSE 10.1. It seemed like a very likable OS, but I soon discovered that - horror of horrors - my Linksys WPC54G v1.2 wireless card is unsupported; and whereas it worked just fine in Mandriva with ndiswrapper (which is fully integrated into that OS), ndiswrapper could now only vaguely detect my router without being able to connect to the Internet. Four full days I spent either wrestling with ndiswrapper, stubbornly (and forlornly) trying to get the obsolete BCM43xx drivers to work with the broken SoftMAC, or attempting unsuccessfully to patch or clean upgrade the kernel to one supporting the BCM43xx drivers (which, apparently, SuSE doesn't like unless it's a certain specialized kernel that's not available yet).

Yesterday, I finally gave up after hearing that Ubuntu has BCM43xx drivers built-in. I burned the Ubuntu 6.06 LiveCD, popped it into my computer, and... waited. The kernel booted, GNOME came up, and I double-clicked on the Install icon. It didn't seem to do anything, so I tried again. And a third time. I left it alone for a little bit, and finally a gray window came up after a full three minutes. It took another several minutes to load the "choose your language" dialog, whereupon I clicked Next. A map with a bunch of dots on it appeared, but I've never been able to go any further than that - even after waiting for 45 minutes for the dang thing to load. Thinking it may be a problem with the CD, I burned another, but the same thing happened. I then tried it in another computer, and the installation came up as it rightly should. It's not my CD drive, either, since I can boot just fine from the Mandriva LiveCD I still have. But obviously, something is not right.](*,)

I've tried a couple different options - including hitting Escape during the boot screen and entering "live vga=771 noapic nolapic" as per the help menu's advice - but to no avail. My computer is an Acer TravelMate 230 laptop with an Intel Celeron and 256MB of RAM, and it's worked fine with the other two distributions...

So what do you think is wrong? Is there another installation method I could try? All these different dead ends have been giving me a headache for the past week, and I refuse to let this one hamper me. I *will* have a reliable distribution that supports my wireless card while I wait for a version of SuSE with a 2.6.17+ kernel (or perhaps not so temporary, if I like it well enough :) ).

Help me, Ubuntu community. You're my only hope.

---

### Post by zhoux on 2006-07-17
have you tried the "alternative" discs? It is text-based installation disc, and I personally find that the easiest to use (and the most powerful may i add)

---

### Post by Aranel on 2006-07-17
> **zhoux said:**
> have you tried the "alternative" discs? It is text-based installation disc, and I personally find that the easiest to use (and the most powerful may i add)

Um, somehow I managed to miss those on the site. I'll try that! Thanks!*feels kinda stupid*

---

### Post by Aranel on 2006-07-18
Oy. The text installation went more smoothly, but then it just... stopped. I went through all the steps, it installed the "base system" with no trouble, and it got 50-something percent into the software installation. Then the screen went completely black for a moment, two grayish rectangles appeared on the screen, the hard drive's light stopped blinking, and my (normally rather loud) CD drive stopped making noise. I've attempted it twice more, and the same exact thing has happened each time.

I think Ubuntu hates me.:-|

---

