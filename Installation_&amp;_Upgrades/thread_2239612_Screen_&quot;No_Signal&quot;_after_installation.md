---
title: "Screen &quot;No Signal&quot; after installation"
date: 2014-08-14
forum: Installation &amp; Upgrades
---

### Post by faultlessimperfect on 2014-08-14
Hey all,

I just installed 14.04 on my HP Pavilion p7z desktop and am now receiving a "No signal" error from my screen. Everything went perfectly during the install. I booted from liveUSB and checked that screen, keyboard, mouse, wifi, speakers, etc. were all working before installing. It went all the way through the install with the screen still working fine right up until I restarted the computer at which point the screen started bahaving like it wasn't plugged into anything...

I've been using Ubuntu for nearly 7 years now and am passably comfortable fixing most problems that come up (with the help of instructions from these forums), however, I don't even know where to start on fixing this as I can't do much without being able to see the terminal, etc... Can anyone point me in the right direction?

Note: I have searched the forums for existing info on this issue, but can only seem to find posts about a blank screen **after** login. I'm not even making it to the login screen, my screen is blank from the moment I restart. If there is an existing thread on this issue, I'd be happy to try and work from that if someone can point me in the right direction.

Thanks!

---

### Post by donkeyoatmeal on 2014-08-15
Can you boot from liveusb disk fine? If so click install and then repair

---

### Post by QIII on 2014-08-15
Hello!

Do you get a BIOS/EFI splash and can you enter and see the BIOS/EFI setup?

---

### Post by faultlessimperfect on 2014-08-15
> **donkeyoatmeal said:**
> Can you boot from liveusb disk fine? If so click install and then repair

It's kind of complicated. I solved the boot up issue by unplugging and then plugging back in the liveUSB after which it booted without issue (to the install, not the liveUSB - it has me log in and successfully saves changes between reboots). However, if I try to boot up with the liveUSB unplugged, all I get is a black screen (a minor improvement on the "No signal" error I was getting). It is also now unable to shut down as it freezes halfway through the shutdown (on the purple ubuntu screen with the progress dots) and I'm left having to do a hard shutdown by holding down the power button. The time when it freezes seems to consistently coincide with the power light on the liveUSB going off, but I'm not sure which is cause and which effect. Also notable, I can unmount and even unplug the USB once the computer is booted up and everything works just fine (until I try to shutdown and it freezes...).

It seems like there must be a file on the USB that is required for startup and shutdown but which was not successfully installed to the harddrive. I have considered trying a clean wipe and reinstall but am wary that this might put me back at square one as I'd essentially be repeating the original install that I did yesterday. I'm also not confident I would then be able to get back to where I am now. At least as is I have access to the terminal (and would theoretically be able to diagnose and treat the problem from there if I knew a little more about how to do so...).

Given the update above, if you still think a reinstall is the way to go, let me know and I'll try it. First, I thought I'd reach out for any ideas of ways to address this in the terminal before I risk losing that option.

Thanks!!

---

### Post by faultlessimperfect on 2014-08-15
> **QIII said:**
> Hello!

Do you get a BIOS/EFI splash and can you enter and see the BIOS/EFI setup?

Nope. There was no BIOS splash either during the original issue (the "No signal" error) or now (the black screen I get if I try to boot up with the liveUSB unplugged). However, I do get a normal BIOS splash (and subsequent startup) if I boot up now with the liveUSB plugged in (see more detailed description in my last post).

Thanks!

---

### Post by donkeyoatmeal on 2014-08-15
Yes I would start on a new usblive disk. [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by QIII on 2014-08-15
With the flash drive unplugged at startup do you get any POST beep codes?

---

### Post by faultlessimperfect on 2014-08-15
> **QIII said:**
> With the flash drive unplugged at startup do you get any POST beep codes?

I get nothing at all. Just a black screen, no sounds. The only thing that shows I've booted up is the power light on the desktop tower itself.

---

### Post by faultlessimperfect on 2014-08-15
> **donkeyoatmeal said:**
> Yes I would start on a new usblive disk. [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Ok. Working on that now. Might take a little while as I need to find another free USB. Will let you know how it goes once done.

---

### Post by QIII on 2014-08-15
Do you get a beep if you have the flash drive in?

What we'd like to know is whether this is OS level or some time prior to OS load.

Of course, if you don't have a mobo speaker you won't hear anything in either case anyway.

---

### Post by faultlessimperfect on 2014-08-15
> **QIII said:**
> Do you get a beep if you have the flash drive in?

What we'd like to know is whether this is OS level or some time prior to OS load.

Of course, if you don't have a mobo speaker you won't hear anything in either case anyway.

No beep, however, I only have external speakers (as far as I am aware). Seems to be prior to OS load since I don't see the BIOS splash but I confess to being not very knowledgeable on this...

---

### Post by faultlessimperfect on 2014-08-15
> **faultlessimperfect said:**
> Will let you know how it goes once done.

Well that didn't work... I made up a new liveUSB and booted to the first menu (options include "install ubuntu", "try ubuntu without installing", etc.) and had it scan the liveUSB to check for errors which it did and said all was fine. Then I booted back to that same menu and picked "install ubuntu". The first install which I did yesterday I had done by booting all the way into the ubuntu OS on the liveUSB and installing from there so I figured I'd go the other route this time in the hopes it would change something. It did, just not in a good way. 

After I chose "install ubuntu" the screen went black and stayed that way for 10 minutes with no sign of change. I ended up having to do a hard shutdown after which the computer is no longer working at all. I've tried booting with the old liveUSB plugged in, the new one, and no liveUSB at all, and they all have the same outcome which is that the power light on the tower shows it as on but the screen says no signal... Any ideas on where to go from here??

Thanks!

---

### Post by faultlessimperfect on 2014-08-16
> **faultlessimperfect said:**
> Well that didn't work...

So, I decided to try and have another go at this today and have had a little more success. Not sure what letting it sit overnight did, but by this morning I was able to get to the BIOS splash and boot to a new liveUSB from which I did a fresh reinstall. Since that install, I am now able to boot up fairly consistently without a liveUSB plugged in (it still does the "No signal" thing about 10% of the time with no obvious pattern, but I can live with that). Yay!

The shutdown thing is still an issue. I've tried every fix listed in this thread with no success: [http://ubuntuforums.org/showthread.php?t=2217602&highlight=shut+freeze](http://ubuntuforums.org/showthread.php?t=2217602&highlight=shut+freeze). it also freezes within one minute of startup about 20% of the time forcing me to hard shutdown and reboot, but if I get past that one minute mark it seems to do just fine even I'm doing pretty resource heavy stuff (video, audio, multiple programs, etc.). I don't even know where to start on fixing this...

Since it's currently passably functional, I think I'm going to try running with it as is (while backing up my files frequently in case it deteriorates) and hope that some set of updates in the next few months fixes it. It's not too long 'til 14.10 comes out so maybe that'll fix it... That said, if anyone has any thoughts on ways to fix this other than time, please let me know and I'll definitely try them out!

Thanks so much for your help donkeyoatmeal and QIII!

---

