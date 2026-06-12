---
title: "Ubuntu 11.10 installer hanging"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by false truths on 2011-10-20
I recently downloaded the Ubuntu 11.10 LiveCD (an amazing feat, considering how slow my internet is), and I've spent a good 3 hours trying to get it to install. It boots from a CD or USB stick just fine and runs great on my previously very finicky laptop, but, whenever I go to install it, every time I try to go past the "select an internet connection" screen, it just hangs. My hard drive starts read/writing like crazy and the CD/USB drive I'm booted from goes dormant.

I'm not really the greatest expert in solving problems like this, so, if there's anything I can do to help solve this, let me know. I just need the help of someone who might know what's going on.

---

### Post by xxrsc on 2011-10-23
I get to the 'Who are you?' screen and it hangs. Is there any way to do a text based install? I think it's graphics driver related.

---

### Post by fredwheeler on 2011-10-24
> **false truths said:**
> I recently downloaded the Ubuntu 11.10 LiveCD (an amazing feat, considering how slow my internet is), and I've spent a good 3 hours trying to get it to install. It boots from a CD or USB stick just fine and runs great on my previously very finicky laptop, but, whenever I go to install it, every time I try to go past the "select an internet connection" screen, it just hangs. My hard drive starts read/writing like crazy and the CD/USB drive I'm booted from goes dormant.

I'm not really the greatest expert in solving problems like this, so, if there's anything I can do to help solve this, let me know. I just need the help of someone who might know what's going on.

I had this same problem and I found a work-around - at least it worked for me.

I was using the 11.10 i386 installer CD and installing to a Dell Inspiron 1764.  I was able to "try Ubuntu" using this live CD on this machine and it ran great for a couple of days - no trouble - amazing really.  But then when I did a complete power down and booted up to do the real install process the installer hung right after hitting continue on the "internet connection" dialog.  The mouse cursor moves but is in the "busy shape" (small circle with dots spinning around).  It seemed that the installer application was hung up or frozen.

The solution for me was to simply wait a very long time.  I let the computer sit in this state while I was out.  When I returned I was at the next stage of the installation process and all went well from there.  I got to the next window somewhere between 20 minutes and 3.5 hours (that is the time period for which I was away).  The next installer dialog is the one that asks whether you want to install Ubuntu to the disk and erase Windows 7 or install next to Windows 7, or other options.  So during this long "hang" the installer must not simply be checking that there is in fact a hard drive, but scanning the hard drive to figure out what OS is on there.  For some reason this must take a long time.

I would suggest that the Ubuntu installer should be made to work faster or at least indicate to the user that it is scanning the hard drive and may have to do that for a very long time.  In the meantime, extreme patience may be a work-around.

After installing i386 Ubuntu I later installed amd64 Ubuntu over the i386 install.  This time there was no significant "hang" after the "internet connection" dialog.  The installer moved to the next screen quickly, asking me if I really wanted to overwrite Ubuntu i386.  So the length of the delay has something to do with the hard disk format or OS.

Fred

---

