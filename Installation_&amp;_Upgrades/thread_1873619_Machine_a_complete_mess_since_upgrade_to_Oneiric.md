---
title: "Machine a complete mess since upgrade to Oneiric"
date: 2011-11-01
forum: Installation &amp; Upgrades
---

### Post by Kheiron2711 on 2011-11-01
Hi guys.

I don't really know where to start but since I upgraded to Oneiric last weekend, I've found that practically nothing works anymore.

To clarify, this install is on an HP laptop.

Firstly, after the upgrade, I kept getting a "Checking Battery State" error on boot. I changed over to lightdm and this seems to have solved the problem although, honestly, I'd prefer to start using gdm again if I had the choice.

I then had a problem getting my account to log in at all. It would accept the password, a CLI screen would flash in the background and then it'd take me back to the login screen again.
I resolved this eventually by deleting the .Xauthority file.

However, I still cannot get the machine to auto-login. Not sure what's going on there but it's not too much of an issue for now. I can live with the current state.

However, here are a few other things that broke that I simply cannot fix:

1. Even though I've purged it, somehow Network-Manager keeps overwriting my resolv.conf file on boot. I've double checked and Network-Manager is definitely not installed.

2. Lirc doesn't seem to be working anymore. I was using a Harmony remote for my XBMC media center and now, since the upgrade, it doesn't seem to recognise anything I press. I've tried purging and reinstalling lirc but nothing seems to work. I didn't have to make any strange changes to lirc the last time around so I'm not sure what has changed.

3. I currently have my display outputting to both my normal built-in screen as well as my HD TV. I'm essentially duplicating the display. However, I now see that on the TV, it's very off-centre. If I manually center it, the laptop screen becomes off centered. In fact, even if I use VNC to remote into the laptop, that screen is also off center.

I suspect that both of these are as a result of some sort of driver compatibility issue. 
I think GDM won't load due to there being some problem recognizing or loading the Intel graphics drivers (or some bug in the way it uses it). 
Likewise, I think the off-center display issue is as a result of the same thing.

The lirc issue is probably as a result of it somehow no longer recognizing my USB IR receiver driver. It does recognise the device as a "(Fintek) F71610A or F71612A Consumer Infrared Receiver/Transceiver". 
I'm not entirely sure if that's the correct driver it should be using since I didn't have to check what it was using prior to the upgrade since it always just worked. It's a standard "HP Media Center" receiver.

On a side note, I had to uninstall and reinstall proFTP as well as, for some reason, it refused to boot initially and kept complaining when trying to start the service. A reinstall fixed that issue.

I'm just confused as to why I've suddenly run into so many problems as a result of an upgrade. I've never had this amount of problems in prior upgrades. It's normally just one or two things that are easily fixed after a few tries but this is killing me.

---

### Post by lincoln.burton on 2011-11-02
Sorry to but in on your thread, this may or may not be unrelated.
I'm running **Oneiric **now, and I'm having a probably related video issue.

> 3. I currently have my display outputting to both my normal built-in  screen as well as my HD TV. I'm essentially duplicating the display.  However, I now see that on the TV, it's very off-centre. If I manually  center it, the laptop screen becomes off centered. In fact, even if I  use VNC to remote into the laptop, that screen is also off center.My issue is that I'm running two monitors in Twin View, when I run up an application that starts up on the second monitor I cannot see this (due to the monitor being in the other room!) however I used to be able to click on the workspace manager, then when the window zoomed out and allowed me to view both monitors on my main monitor. I could then click on the application on the second monitor and drag it back over to the first. Now with the new upgrade I cannot do this, strangely enough if i click my mouse in the original monitor (whilst zoomed out using workspace manager) on the same horizontal line, i can click and drag the application from the secondary monitor!

I just thought this misalignment of screens may be related.

BTW I'm using Nvidia drivers version 280.13

---

