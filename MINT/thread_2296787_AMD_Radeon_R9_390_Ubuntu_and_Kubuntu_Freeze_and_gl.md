---
title: "AMD Radeon R9 390: Ubuntu and Kubuntu Freeze and glitch up"
date: 2015-09-28
forum: MINT
---

### Post by Rehaan_Raja on 2015-09-28
Here goes to re-typing my essay which firefox auto saved - then crashed - then didn't recover, all over again.
Enjoy the font


Lets see
Using my GPU - MSI

Ubuntu + Kubuntu crash when booting live cd + graphics rendering is failing. Patchy patches of random colours that aren’t supposed to be where they are.
Point being, my GPU can’t render those distros.
Why? What is the solution?
 
Lubuntu is fine.
 
Xubuntu is fine – though I don’t like it. Too much mess everywhere.
 
I like Linux Mint though. Simple, clean UI. It boots fine. But it shows an error “Running in software rendering mode”
 
Like this:
[http://www.thehyperlink.net/sites/thehyperlink.net/files/debian-8-or-mint-cinnamon-software-rendering-mode.png](http://www.thehyperlink.net/sites/thehyperlink.net/files/debian-8-or-mint-cinnamon-software-rendering-mode.png)
 
What is the solution?
 
Another problem. When outputting sound through HDMI, there is a lot of crackling sound on Mint and Xubuntu. What is the fix? Sound is fine through the 3.5mm audio jack.
 
I would ideally like to be actually using my high end GPU to render graphics and not my CPU. Lest that GPU turns out to be a waste.
 
As for the problems with Ubuntu and all that graphics patchy colour rainbow stuff. I suspect it’s a driver problem. Apparently drivers are something Linux is terrible at? Please tell me there is a fix for this!
 
Ubuntu is fine when I take out the HDMI from the GPU and connect it to the mobo. Effectively rendering everything with my integrated graphics.
 
Problems:

[LIST]
[*]Patchy random rainbow square colours on Ubuntu and Kubuntu, followed by an unusable, unresponsive system. Effectively a crash
[*]Static through hdmi
[*]Software rendering thing. Might be linked with the patchy random rainbow square colours thing. Bad drivers? Is there a fix?
[/LIST]


On behalf of Firefox, I apologise for keeping this short and terribly typed. This would read a lot nicer had Firefox not crashed. I blame you Windows.

Sound through youtube does come out through hdmi. 

Just accompanied with crackling-static sound

Oh and when I drag a window to the top of the screen, only the top half gets filled.

Is this normal for linux? How can I have it fill the entire screen?

---

### Post by QIII on 2015-09-28
Please use the default font.


Unity and KDE each differ from other DEs in ways that likely make it difficult for the open source driver to manage such new hardware.  I run an R9 290X and the open source driver's performance was terrible.  The open source developers are playing catch-up.  They don't have much choice for new hardware.   They have to start over and figure it all out.  

My GPU works very well with the proprietary driver.  Not long ago I tested the R9 290X on several releases of Ubuntu and put the results in my blog.  The open source driver did not work well with any of them.  It does not work very well with my Kubuntu daily driver.

So I use the proprietary fglrx driver.  Since the R9 390 uses the same GPU chip, just over-clocked, and more memory, I suspect that you will get the same results from an R9 390.

---

### Post by Rehaan_Raja on 2015-09-29
I have just realised that while using Mint, Linux detects that I have a 290. I suspect, as you said, that this is because they are catching up to the new hardware.

I can run ubuntu by running off the integrated graphics. but that'll involve me having to connect the hdmi to the mobo and open up my pc and disconnect the power for my GPU every time.

BUT is there some way I can install and run Ubuntu while on the integrated graphics chip, and then install 'better' drivers for the 390?

Also, are there no 390 drivers for Linux or am I stuck with 290?

---

### Post by QIII on 2015-09-29
I suspect that if you use the fglrx driver in the repo, which is provided to Canonical by AMD and packaged by Canonical for Ubuntu, you will get excellent performance.

---

### Post by howefield on 2015-09-29
Thread moved to the "*MINT*" forum.

---

### Post by Rehaan_Raja on 2015-09-29
How would I go about installing the driver?

...twas about Ubuntu too :/

lol

---

### Post by QIII on 2015-09-29
Please see the ATI driver wiki in my signature.  I prefer installing via the command line, which I have detailed in Section 3.1.  In Section 5 I described how to add some hardware acceleration.

---

### Post by Rehaan_Raja on 2015-09-29
> **QIII said:**
> Please see the ATI driver wiki in my signature.  I prefer installing via the command line, which I have detailed in Section 3.1.  In Section 5 I described how to add some hardware acceleration.

Is there some way for me to install the proprietary driver for my 390 while using my integrated graphics chip?

Will Linux allow this?

---

### Post by QIII on 2015-09-29
Some motherboards will allow the use of both GPUs simultaneously.  Those are not common.

In any case that does not work well under Linux.  Unfortunately, the OEMs do not put that much effort into such things for such a small segment of the market.  It is very unlikely that you can use both as you sometimes may with Windows.

---

### Post by Rehaan_Raja on 2015-09-30
Worth noting I built my Desktop myself - it's not branded or anything.

My mobo is a Z97-Pro (Wifi.a.c.)

[https://www.asus.com/Motherboards/Z97PROWiFi_ac/](https://www.asus.com/Motherboards/Z97PROWiFi_ac/)

I meant because I could connect the hdmi to my mobo, disconnect my GPUs power cable, and install Ubuntu that way. Then once Ubuntu is installed, I could install the 390 drivers and after, connect my 390.

There is no other way I can see of which would allow me to install Ubuntu since once I boot up with my 390, or even without booting, Ubuntu freezes up without giving me the chance to change drivers.

---

### Post by v3.xx on 2015-09-30
If you like Mint, then try ubuntu Mate, its similar to Mint and will run on machines that will not run Ubuntu (Unity).  And its supported here.

---

