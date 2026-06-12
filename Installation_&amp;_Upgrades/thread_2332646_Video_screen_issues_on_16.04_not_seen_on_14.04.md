---
title: "Video screen issues on 16.04 not seen on 14.04"
date: 2016-08-02
forum: Installation &amp; Upgrades
---

### Post by jfaberna on 2016-08-02
I've been running a flavor of Ubuntu 14.04 on my hardware:

 Intel DQ77KB motherboard with a Core i5-3450S CPU, 8GB of DRAM.

The version was specifically Mythbuntu 14.04.  I tried a upgrade in-place to 16.04, but had a lot of video issues.

So I got a fresh USB installer of Ubuntu 16.04.1 and tried to boot it to install to see if the video issues were related to mythbuntu or not.

The first screen of the install had the same problems as I'd seen after I tried to do the in-place upgrade.  The problems are:

1.  the screen goes blank for a variable number of seconds from 1-5.
2.  there is random video noise. i.e. horizontal lines, single pixel tall that seem to be popping up in various vertical positions on the screen.

I never saw any issue like this on previous versions of Ubuntu.

---

### Post by jfaberna on 2016-08-05
I did further testing on this issue.  The PC is connected via HDMI to an Onkyo TX-NR709 A/V receiver and it's connected to a Sony KDL-52XBR6 TV.

I ran a HDMI cable directly from the PC to the TV and and there was no noise or blanking. So it appears to be specific to the receiver.

I tested multiple inputs and multiple HDMI cables and the problem remains.

I would completely blame the A/V receiver if it wasn't for the fact that Ubuntu 14.04, Windows 98/7/10 all work flawlessly.

So what is it in the 16.04 video driver for the Intel Core i5-3450S that is exposing this A/V issue?

---

### Post by jfaberna on 2016-08-11
2 New items to add:

Connecting directly to the Sony XBR6 is better but the screen blanks for 3-4 seconds about 1st every 30-40 minutes.

I tried a different computer with Intel HD internal graphics and it has exactly the same issues.  It also had no problems with 14.04.5

---

### Post by jfaberna on 2016-08-13
I recently tested this same computer running 16.04 on a Denon receiver and a Panasonic TV.  I had no issues there.

Could changes in video drivers in 16.04 be misinterpreting what HDMI device they are connecting to and setting parameters incorrectly.  Maybe that change is over driving my Sony TV??? 

How would I override those setting with an Xorg.conf file.  I'm guessing I could get those parameters from the Sony Spec???

---

