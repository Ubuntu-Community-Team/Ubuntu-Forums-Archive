---
title: "Edgy Live CD Freezes at X"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by Aikon- on 2006-10-29
**UPDATE:**
[INDENT]A bug report has been filed here: [https://launchpad.net/distros/ubuntu/+bug/67487]("https://launchpad.net/distros/ubuntu/+bug/67487")
Please check [this thread]("http://www.ubuntuforums.org/showthread.php?t=281111") for more information / troubleshooting steps we've taken so far.
[/INDENT]

__________________


Hey everyone, hope this thread gets noticed before its bumped to page 2 within about 10 minutes..

I plan to, and had always planned to, do a fresh install of Edgy instead of upgrading from Dapper. So, I downloaded the install CD for my architecture (386) and burned it to a DVD (because they cost the same as CDs and I don't burn music discs).

When I booted my computer from the DVD, the first thing I did was to check integrity. No checksums failed.

Next, I selected the first option in the boot menu. I got the usplash screen, everything seemed to be loading fine, and then right when the system is about to run 'startx', everything stops. The screen is blank but from experience I can tell that X tried to start accessing it (just from what the cursor/screen does when X starts).

So, I tried again, this time using safe graphics mode. Same problem. I tried several other times using various options like acpioff and vga modes that I know work etc. and couldn't get X to start.

Does anyone have any other suggestions? I seem to recall having a similar problem with my Dapper DVD, but I can't seem to remember how I resolved it (and I can't seem to find my DVD to test with, either).

Any help would be greatly appreciated!

-Aikon

---

### Post by drucer on 2006-10-29
Hi and welcome on board - there are a lot of users who are experiencing the same. This bug was reported long before the official Edgy Eft was released, but no one seemed to be interested enough to fix this bug.

So, there you have it - a lot of people not being able to install Edgy. It's pretty damn challenging to install it if you can't see anything on your monitor.

---

### Post by Aikon- on 2006-10-29
> **drucer said:**
> Hi and welcome on board - there are a lot of users who are experiencing the same. This bug was reported long before the official Edgy Eft was released, but no one seemed to be interested enough to fix this bug.

So, there you have it - a lot of people not being able to install Edgy. It's pretty damn challenging to install it if you can't see anything on your monitor.

Seems to me this is why I would have preferred the option for installing from the CD immediately, instead of first having to load the Live CD.... As I said, I had a similar problem with Dapper, but as soon as it was installed on my hard-drive it worked fine.

/sigh

-Aikon

---

### Post by Aikon- on 2006-10-29
what boot option can i use to not see the usplash? (so that I can see where things fail or what the last command was etc.)

---

### Post by craigi on 2006-10-29
I am also having this problem when I try to load the Live CD.  I see the Ubuntu splash screen, but when it tries to load into X, the only thing I see are small video lines at the very top of my (LCD/DVI) monitor.    I even hear the chime letting me know that the desktop is loaded.

I experienced no problems with 6.06.  I suppose I'll re-download that and upgrade from there, although I fear the upgrade will kill the video too.

I have a GeForce 6800 (standard) video card connected to a ViewSonic 21" LCD with DVI

---

### Post by Aikon- on 2006-10-29
Is there a way to set the screen resolution that X will use from the boot prompt? Or to customize the mode-lines?

---

### Post by Aikon- on 2006-10-29
anything?

---

### Post by Aikon- on 2006-10-29
/bump

---

### Post by Gustave on 2006-10-29
I'm also encountering problems in the same area.  
I have a GeForce 7800GT, and 19" LCD monitor.
I'm getting serious graphical glitches when booting into the LiveCD screen.  If I use safe Graphical mode it happens even faster.  One time I actually made it to set two of the install before it locked up on me.  
I installed Dapper when it came out and I had similar problems then but by using safe graphical mode, I got past it.  Not this time.  ](*,)
Any nifty startup commands would be helpful.

---

### Post by seldon77 on 2006-10-29
yeah, I had this problem with X as well. 6800GS graphics card - as above, I also just had a lot of mess drawn on the screen when X tried to load.

solution was to hit F4 at the boot CD bootup screen and select 1024x768 high colour and that worked - but I didn't get a cursor so it was a bit hard to select things (cursor showed up once edgy was installed to HDD).

---

### Post by Gustave on 2006-10-29
Selecting another resolution didn't help me.  I had already tried it but I tried it again for grins.  No luck.
However, if you go to the download pages, there are alternate installs.  I used that and it let me select a text install.  I was able to successfully install this way.
However, this version of Ubuntu doesn't like my setup.  I actually got it installed correctly, loaded it up, went to open up a browser and the whole thing froze on my like it had been doing in the LiveCD screen.
At this point, I dunno what to do.  I might try to install 6.06 again if I can find the CD and give that a wack with an upgrade, but I've heard bad things about the upgrades, too.  
Oh, well.  I have a perfectly functioning OS right now.  I dunno why I wanted to mess around with that anyway.

---

