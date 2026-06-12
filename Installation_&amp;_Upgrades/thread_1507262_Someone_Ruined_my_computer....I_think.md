---
title: "Someone Ruined my computer....I think"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by Greenhorn Geek on 2010-06-11
Just the other day this guy was helping me set up my computer for the game Planeshift.  For some odd reason the game wouldnt work and he told me to download the drivers through the terminal. ( I have ati x700 graphics card).  After I rebooted, the resolution was all funny and I couldn't put compiz effects on or anything.  I went to visual effects and it was on "none." This happened with my last computer to which had an nvidia geforce2.  So now I reinstalled ubuntu and its running great with compiz and everything.  Any suggestions?

---

### Post by howefield on 2010-06-11
> **Greenhorn Geek said:**
> So now I reinstalled ubuntu and its running great with compiz and everything.  Any suggestions?

Suggestions for what ?

It's running "great with compiz and everything"

---

### Post by HeirPixel on 2010-06-11
> **howefield said:**
> Suggestions for what ?
It's running "great with compiz and everything"
I take it the OP is looking for suggestions on how to get drivers installed correctly to play the game...

When you downloaded the drivers "through the terminal" what did you actually do? Did you get sourcefile/DEB from ATI?

---

### Post by jocko on 2010-06-11
> **Greenhorn Geek said:**
> Just the other day this guy was helping me set up my computer for the game Planeshift.  For some odd reason the game wouldnt work and he told me to **download the drivers through the terminal.** ( I have **ati x700** graphics card).  **After I rebooted, the resolution was all funny and I couldn't put compiz effects on or anything.**  I went to visual effects and it was on "none." This happened with my last computer to which had an nvidia geforce2.**  So now I reinstalled ubuntu and its running great with compiz and everything.  Any suggestions?**

The open source drivers (named radeon) are installed by default in ubuntu, and used by default on supported hardware.
I guess that the driver you tried to "download through the terminal" was ATI's proprietary driver (fglrx), which does not support your card. That means you replaced a fully functional (but not very good performance-wise) driver with one that does not work at all with your card. That forced xorg to resort to using vesa, which is why your resolution got all funny (probably 600x800@60Hz) and you lost all 3d acceleration.

So don't try to replace the radeon driver. It is the only one that supports your card (except perhaps some newer, more experimental version of the radeon driver).
There may be some tweaks you can use to improve the performance a bit (I know I had a couple of options I had to put in my /etc/X11/xorg.conf to make the radeon driver run acceptably smooth on my old radeon 9600 before I replaced it. Unfortunately I've forgotten exactly which tweaks, but I posted them on these forums a couple of times when I tried to help other people).

Edit: I found my old tweaks. They can be found [in this post]("http://ubuntuforums.org/showpost.php?p=8486047&postcount=6")... but I have no idea if they will help you in any way...

---

### Post by pricetech on 2010-06-11
> **Greenhorn Geek said:**
> Any suggestions?

Just one, don't listen to "this guy" any more.

---

### Post by Greenhorn Geek on 2010-06-11
Thanks guys!...I need to learn more about linux before rushing into stuff..XD

so im guessing just leave everything as it is??

---

### Post by pricetech on 2010-06-11
Yes and no.  On the one hand, if it ain't broke, don't fix it.  On the other hand, some of my best learning experiences came about as a result of "crash and burn".

Try not to leave yourself completely without a computer.  Otherwise, dive in.

---

### Post by Greenhorn Geek on 2010-06-11
What I dont get is that under the "Ubuntu Software Center" I search ATI, and it comes up with this....

ATI X.org Driver
Optimized hardware acceleration of OpenGL with newer ATI graphics cards
This is a transitional package xorg-driver-fglrx, and can be safely removed after the installation is complete.

I really dont get this stuff.....O.o

---

