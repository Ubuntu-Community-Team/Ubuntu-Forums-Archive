---
title: "No panel, no anything in ubuntu hardy"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by maturin on 2008-05-05
Before installing/upgrading to ubuntu (or kubuntu) hardy, I thought I'd try it out by installing to a usb flash drive.  Kubuntu did install, though it has some issues (might put that in another post).  

Ubuntu appeared to install (different flash drive).  It came up with the login screen, and I logged in.  Then nothing except a nice orange background.  No panel, and clicking around with the mouse was fruitless.  Just a nice orange screen.  Switching to another (text) console works fine.  Restarting the x-server (crtl-alt-backspace) merely puts me back to the login screen with the same issues.  Trying to change screen resolutions also fruitless.  Same problem with failsafe gnome.

Any thoughts?

Thanks.

---

### Post by fixitdude on 2008-05-05
This may help
[http://ubuntuforums.org/showthread.php?t=781923](http://ubuntuforums.org/showthread.php?t=781923)

Basically I had to move (disable) the ".font" files left over from other installs. There's more info in the thread.

If not, try creating a new user and see what happens, see thread above.

---

### Post by maturin on 2008-05-06
Well, I tried your suggestion, but discovered I don't have a .font file, probably because it's a new install(?).

I also found a thread ([http://ubuntuforums.org/showthread.php?p=4893023](http://ubuntuforums.org/showthread.php?p=4893023)) suggesting an upgrade to a new kernel (in "pre-release"), but that didn't help either.

Still sitting there with a totally blank orange screen.  Not terribly useful, to say the least!

---

### Post by maturin on 2008-05-07
Any one have any ideas on this one?  I've tried a number of different things since my first post, including using the alternative install disk.  But as before, everything's fine until I get to the log in screen.  I log in, then nothing but an orange screen.

Just booting into the live-CD works, but what's wrong with the install to the flash drive?   I'd really like to give Ubuntu a more thorough test run than I can do from the live CD.  Besides, this doesn't make me confident about actually installing it to my hard drive.

---

### Post by fixitdude on 2008-05-08
So you boot the live CD and you get to a graphical screen, mouse pointer and all right?

When you boot from a USB drive you get a graphical log in screen / box with mouse pointer and all that? Meaning X is up and running OK and your display card is working with X at that point.

At that log in box, see in the right lower corner, you can select different things like KDE and Gnome etc.. (on a USB maybe not due to space problems). Try them.

If you drop to terminal, check your USB disk space, type:

df

How big is your USB drive anyway? Is it possible the install ran out of room?

Another thing is that just because they announce that Hardy is now available, doesn't mean it's perfect. It's better to wait and let them get the bugs out of it, sorry.

Most likely there's no need for the latest and greatest OS, so why not try 7.10 on your USB drive?

---

### Post by maturin on 2008-05-11
Yes, everything boots just fine, and I can switch to other (text) terminals.  Mouse pointer works just fine, but no panel, and right or left clicking does nothing.

I tried the various log in options from the log in screen, and they haven't helped.  

The drive is big enough (4 gigs, using about 1.8).  

I generally agree with you that Hardy (Ubuntu) is still having some issues.  That's why I wanted to try it out on the USB drive before trying to install it.  Kubuntu has it's own set of (mostly annoying, but less serious) problems, which is why I was hoping to try out Ubuntu.  I'll probably wait a bit and try again to see if it works any better.

Thanks for all the help - sorry for being so slow in responding.

---

### Post by fixitdude on 2008-12-06
Another idea, I wonder if the screen res is way large? One time I was messing with screen settings and it got so huge that I had to place the mouse at the bottom and then the screen would sort of scroll down and to the side etc... Like I was looking through a magnifying glass.

One more, get a old HD and install it there and test it that way.

---

