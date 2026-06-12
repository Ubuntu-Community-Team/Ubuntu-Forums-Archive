---
title: "LiveCD Freezes"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by kodek on 2007-08-30
So after gnome comes up, I've about less than three minutes before my keyboard and mouse freeze and I have to reboot. I'm pretty sure the entire system freezes up, as hitting caps lock doesn't do anything, and I can't reach the terminals through ALT+Fx.
This one time, I managed to get through the installation wizard, but once it got to ~50%, the computer rebooted. I had the system log with syslog opened and I didn't catch any errors before it rebooted.

Here are my specs:

AMD Athlon 64 3500+ (Clawhammer)
Giga-byte K8NS Ultra-939 (nForce 3 Ultra)
3 GB Corsair XMS (DDR-400, memory has no errors, afaik)
a few SATA hard drives (shouldn't be a problem as nothing seems to be loading when it freezes up)
Audigy 2 ZS (never had any problems with it under older versions of ubuntu)
HIS Radeon X1950 Pro 256 MB (AGP)
usb Mouse, usb keyboard, bluetooth dongle, IR receiver (I tried unplugging these last 2 since they can act like input devices), firewire drive, all were connected before the machine was on.

I'm using one of the shipped CDs. I tried two so far and it doesn't seem to be a bad cd. They're a little old, though, but they're 7.04. If I tried burning an ISO, would it be updated compared to the cd I was shipped, or would it be the same image?

Thanks,
KodeK

---

### Post by merlinus on 2007-08-30
Did you try Safe Video Mode?

If that does not work, you might try the Alternate Desktop install cd. It is text-based, but quite straightforward.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

-merlin

---

### Post by kodek on 2007-08-30
I haven't tried either option cause I don't know how they'd relate to my problem. 

I'll try, but I don't know if it's a video driver issue.

And if it is, wouldn't the issue reappear once I'm using the installed version of the desktop, assuming the problem wasn't fixed in an update? (an update that I probably won't be able to get)

---

### Post by merlinus on 2007-08-30
At least some, if not all, of your problems are video card related.

Once installed, you will be able to use the generic vesa driver to get to a gui, and then search for and install the correct drivers.

Lots of info on that in these forums.

-merlin

---

### Post by kodek on 2007-08-30
Thanks for the replies.
I'm downloading the alternate installer as we speak, by the way.

Why do you say it's a video-related issue? I'd really like to read up on it.

From what I managed to see before the LiveCD froze up on me 4 times, the video was fine. I wasn't getting 3d acceleration, or my native resolution, but it didn't seem to be displaying some weird low-res, low-depth image or anything.

Thanks again.

---

### Post by merlinus on 2007-08-30
Do a fourm search for radeon.

-merlin

---

### Post by kodek on 2007-08-30
Okay. I found a thread that had about 60 pages and people were complaining about freezes similar to what I'm having, but not completely the same (their system seemed to be half responsive cause their mouse was still working).

I tried the safe video mode, but I got to 39% and everything froze up.

Got any other ideas? I'll try the alternate CD tomorrow morning since it's still downloading.

---

### Post by kodek on 2007-09-01
Okay, I'm still in need of help. I really don't want to give up on the issue.

I tried 7.10 t5 and I had the same issue. The installer would freeze half-way through it.

I also tried disabling powernowd, and I managed to get through the whole installation like that, but I had some grub problems so I had to do it again, and the second time, stopping powernowd didn't do ANYTHING :(

How can I get some information about the problem? I'm sure something must be getting logged somewhere, but the machine won't let me access it (since it's frozen). I tried keeping the system logs app in the background with syslog updating, but I didn't see anything out of the ordinary in it.

What else can I try?

Thanks everyone.

---

