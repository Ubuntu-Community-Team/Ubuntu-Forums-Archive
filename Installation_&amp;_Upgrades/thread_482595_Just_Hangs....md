---
title: "Just Hangs..."
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by Contrarian on 2007-06-23
Trying to install 7.04 on a Dell Latitude CPx.  I honestly don't know the full specs, it's like 512MB ram and P3 750 I believe.    It works just fine with XP, 2000, and 2003 which I have had running in the past.

I figured out the first error (the I/O Buffer on FD0) basically that I needed to go hunt down an USB floppy drive, which seems to have eliminated that.  Then I got I/O Buffer error on HDC, so I burned another copy of the Live CD at 8x (raising eyes... never had to do that with a MS .iso image).  

So now I boot up.  I hit the "Start or Install Ubuntu".  It goes to the "Loading Kernel".  Then I get that splash screen with the orange loading bar going back and forth (this stays up for a few minutes). 

Now it's stuck with the flashing cursor in the upper left corner.  I've seen a lot of posts about this, not a lot of answers.  

Why does this take so long to boot?  Is it doing a full disk consistency check or something?

---

### Post by merlinus on 2007-06-23
There may be problems with your video card.

Try Safe Video Mode from the start-up screen.

If that does not work, download the Alternate Desktop install cd, which is text-based.

Burn it the same way as the live install cd.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, and then click the text to begin.

I used this for a straightforward install on a 5-year-old Compaq with 256MB RAM and a 1.09GHz processor.

-merlin

---

### Post by Contrarian on 2007-06-29
I used the alternative disk and still had problems.  Fortunately this laptop I had another CDRom drive that I could plug in, and that fixed it.  This reply is coming from the installed laptop.  Thanks.

---

### Post by dabl on 2007-06-29
> **Contrarian said:**
> 
Now it's stuck with the flashing cursor in the upper left corner. 

When you see that, you can usually hit Alt-F1 and get the console, and log in that way.  Once logged in, you can normally create a functional GUI using the following routine:

```
sudo dpkg-reconfigure xserver-xorg
``` this initiates the xserver configuration script.  On the first screen, do NOT attempt to autodetect the video card (we already know it can't), then on the second screen choose "VESA" as the display type.  From that point you can accept the defaults -- no need to autodetect the keyboard unless it is non-standard.  When you get to the monitor section, choose a refresh rate or two that you can live with for awhile, like 1024x768, and then set the screen refresh range to one that your CRT or LCD will accept. When the script finishes, it will dump you back to the command line.  At that point, you should be able to type ```
startx
``` and get a GUI login.

Now, if you want the highest performance that your video chip is capable of, you will need to identify it and search these forums for details on how to configure your system for that particular model.  Otherwise, your VESA display will work just fine.

HTH :D

---

