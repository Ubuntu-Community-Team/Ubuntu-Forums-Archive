---
title: "Problem with Mar 8 Live CD"
date: 2010-03-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2010-03-08
I have been able to boot the Lucid Daily Live CD for the past several weeks. With today's current ISO (Monday, Mar 8), I thought things were going better than ever, but, in the end, it doesn't work at all.

Fof the first time, I got a nice, GUI Plymouth splash screen. Then, after a few seconds, I get a black screen for long enough for my monitor to shut down saying, "No video input". Then, after a minute or so, I get a purple Radiance wallpaper with a live cursor  and nothing else. No menus, panels, nothing. Hitting the Enter key does nothing, holding down the Enter key does nothing, and right clicking on the desktop does nothing. There is no apparent disk activity, either. Just sitting there with a wallpaper and a cursor.

I re-booted to try it again, but I got the same result.

I guess I will try the alternate image, but I have never been able to get it to work, before. Be back, later.

Tim

---

### Post by ratcheer on 2010-03-08
And today, for the very first time, I was able to do a complete installation from the Alternate CD image and reboot Lucid, normally. I did get a little of the disk grinding, but after 30-40 seconds of it, it stopped grinding and the desktop came up and worked, perfectly. Then, I was able to install the nVidia current recommended proprietary driver and reboot again.

Plymouth is working just fine, with a cool purple splash screen. Karmic still boots much faster, for me.

So, this week is a complete flip-flop from the past few weeks. Until now, I could not install the alternate image and had to install from the Live CD desktop. Until now, I could not boot Lucid without going to a grub recovery boot prompt and starting gdm from the command line.

I wonder if they will ever get everything working at the same time?

Tim

---

### Post by grubdude on 2010-03-08
Beats me. Today's updates t -16 kernel hosed my nicely working 10.04. I am downloadin today's build to see if fresh install versus upgrading helps, but it really screwed up my virtualbox guest additions, etc.

---

### Post by ratcheer on 2010-03-08
Dern! I finally get this thing (Lucid) working with some sense of normalcy, and they release another kernel upgrade, today. #-o

I am going to hold off until tomorrow. I will finish my weekly testing with the current setup.

Just when I thought I was finally getting somewhere.

Tim

---

### Post by grubdude on 2010-03-08
Tell me about it. I finally get things setup fine and the new kernel hosed my X. I hope they fix this as it is a show stopper for me, for now...

---

### Post by Dougie187 on 2010-03-08
I think these are reasons why you aren't supposed to use it on a production machine. It chances quite frequently and can break stuff.

---

### Post by aceracer24 on 2010-03-08
> **grubdude said:**
> I hope they fix this as it is a show stopper for me, for now...

Seriously??? Umm it is in Alpha....it has not even made it to beta yet which means it is still a ways from being stable. If you installed this assuming it would work out of the box and you did so on your every day PC without a stable linux install (9.10, 9.04 or other)...you deserve what you get.

---

### Post by rtalcott on 2010-03-08
Lucid is working fine on 3 machines...all 64 bit....tried to boot today's 32 bit daily...boots...but the mouse and keyboard are frozen after boot...guess I'll try again tomorrow...this machine runs 9.10 without a problem.
rt

---

### Post by MacUntu on 2010-03-08
Similar "problems". Just did Ctrl+Alt+F6, F7, F8 or so until the desktop showed up.

As for the "no signal" part: I think that's a problem whith Nouveau(fb?) not getting valid EDID from your monitor. X works cause it uses some failsafe resolutions. Dunno.

---

### Post by ranch hand on 2010-03-08
I hate to admit it but I can actually usually get the bugger to boot with out going to recovery.  It may not boot with out a kick in the enter key but it boots.  Most times on its own.

---

### Post by jppr on 2010-03-08
Just did a clean installation. First I install in synaptic Unetbootin and then live-cd download and installation, and system run well. Unetbootin is a lot easier and quicker than usb-creator

---

