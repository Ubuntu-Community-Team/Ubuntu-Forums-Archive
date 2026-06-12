---
title: "Install with HDMI flat screen"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by TimTang on 2009-11-29
Has anyone ever been able to install ANY version of Ubuntu with just HDMI and a Flat screen TV?

I haven't used Ubuntu for about 9 months or more; that's when I got rid of the old crt monitor I had kicking around. With out it I can't install Ubuntu. At this time they also destroyed Xorg by eliminating the option of creating your own settings file. I used to have a PERFECT pixel per pixel setup (1360x768) that even windows couldn't do, now I have NOTHING. Changing Xorg so you can't customize it, is something you'd expect Microsoft to do.

I've tried every version that's come out with no success, yet windows installs flawlessly with no problems what-so-ever. Has anyone on the Ubuntu developement team ever tried to install only using HDMI and a flat screen. I'm sure I'm not the only one in the world that uses their computer in the living room as a home entertainment device.

I tried 9.10 tonight having downloaded the installation disk yesterday. I chose graphics in safe mode (F4). I got as far as the partitioning. At this stage I can't read or have access to the selection buttons at the bottom of the screen (I don't like GUESSING when I'm installing an operating system), also Ubuntu say's "there is no operating system on your computer"; I have 3 OS's on my computer: I'm given the option of formating and installing on the hard drive that contains all my important data rather than the second hard drive (I have 4) which is where I WANT to install it.

Anyway...I guess it's no Ubuntu for me again. I hope someday they will provide an installation disk that I can just run and install; that doesn't exist yet. What a shame! I used to like Ubuntu but I'm not going to rush out a buy a crt monitor just to install it. I've wasted HOURS if not DAYS trying to install with no success. I just don't have the patience any more.

---

### Post by Dinodoc on 2009-11-29
I admit I have not tried installing in this way, but it is my understanding that Xorg is not setup so you can't customize it, it does do alot of stuff automatically, but it will still read an xorg.conf file if it is presented with one.  In fact installing for example the nvidia drivers will create one that xorg uses.

If you have a copy of the old xorg, maybe it would still work.

---

### Post by TimTang on 2009-11-29
Correction: I had my display set for 1366x765 not 1360x768. Both worked but I prefered 1366x765 because you could position the screen with the lost 3 pixel on the bottom where I had my single taskbar. This was perfect because the taskbar was completely hidden without any need for tweaking or 3rd party utilities.

I do still have my original xorg.conf. The last operational system I had was Intrepid but it didn't work even then. I was forced to use the ATI Catalyst but I could never get the display to even fit the screen much less have a perfect pixel to pixel set up. I know they say that you can tweak your own xorg.conf file but I even tried radical settings just to see if it was working but it made no difference at all. So...I don't know if there is a switch somewhere or what! But I've never been able to get a custom xorg.conf file to work; even a bad one!

---

### Post by TimTang on 2009-11-29
Just for comparison: When you install windows using my current system, it defaults to 640x480 for the installation process. It's kinda klunky and stretched out but everything fits and you can read everything and provide the appropriate answers to all the questions. Once the OS boots up it goes directly into 1920x1080; no questions, no problems. It's not pixel per pixel but it fits and it works.

Installing Ubuntu selecting the F4-low res. option you end up with screens that are larger than the display even though there are black bars on the top and bottom. Unlike windows the screens are full not inside frames that can be resized so there is no way to read or select anything. I don't know how you can get around this but it basically makes it impossible to install.

---

### Post by mazz0 on 2010-05-14
When do you press F4?  My problem trying to install using HDMI is it goes blank after the Man=Keyboard screen.  Is that when you press F4?

I was going to stea- borrow a VGA cable from work and try it using that, have you tried that?

---

### Post by Cerin on 2013-01-26
I'd like to know an answer to this as well. Three years later and this problem still persists in Ubuntu 12.04 LTS. Now wonder no one's adopting Ubuntu en mass...Windows handles this just fine.

Sorry for the venting, but it's frustrating seeing ancient bugs that stop something as simple as installing the damn OS.

---

### Post by darkod on 2013-01-26
> **Cerin said:**
> I'd like to know an answer to this as well. Three years later and this problem still persists in Ubuntu 12.04 LTS. Now wonder no one's adopting Ubuntu en mass...Windows handles this just fine.

Sorry for the venting, but it's frustrating seeing ancient bugs that stop something as simple as installing the damn OS.

I suggest you open a new thread and specifying your problem exactly, including any error messages, symptoms, etc. And data like video card model, how exactly you tried to install, etc. We can't guess.

Further more, going back to the OP first post, he also says other OSs are not detected as they should be, so it points to something more than video issues. Maybe running on raid disks (that everyone seems so eager to use but not so eager to clean them up from meta data once they break up the array and want to use them as single disks), etc. Not detecting your OSs has nothing to do with the monitor.

---

