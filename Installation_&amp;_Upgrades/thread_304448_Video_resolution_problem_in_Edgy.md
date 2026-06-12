---
title: "Video resolution problem in Edgy"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by terwilligerjones on 2006-11-21
This is making me nuts. I'm trying to install Ubuntu 6.10 from the live CD. This problem also exists when I try to install 6.06. The box is a Dell Optiplex. The problem is that video will come up ONLY in 640x480, and that is displaced 1/2" from the top. Also, the screen vertically hides part of the desktop. In other words, I don't see all the panel at the bottom, and when I try to install from the live CD, I do not see, nor can I resize windows to see, the bottom where the "Next" buttons are, so I can't even install. Killing the panel at the bottom and moving the top panel to the side to provide more vertical real estate doesn't help.

The display is a Dell FT1800. It's optimum resolution is 1280x1024x60hz. Ubuntu detects it OK, and builds an xorg.conf with what appears to be lots of resolutions, but it comes up in 640x480. The GUI screen resolution tool only offers 640x480x75hz.

I used ctl-alt-F1 to get to a cli. As root:

/etc/init.d/gdm stop
[OK]
ps -ef|grep gdm
[lots of 'em]
killed all of 'em. (I also tried it without doing this part -- just gdm stop.)

vi /etc/X11/xorg.conf

I then removed ALL resolutions except 1280x1024 for each color depth, included the VertRefresh and HorizSync from the spec sheet in the monitor section and saved.

/etc/init.d/gdm start
[OK]

alt-F1, and guess what? 640x480

ctl-alt-backspace
640x480

Gaaaaa! What am I missing??? 
:confused:

---

### Post by taurus on 2006-11-21
Instead of using the LiveCD to install Edgy, you can use the alternate CD since it's a text base installer...  It should be able to pick up your graphic card and your monitor.  Then, just install a driver for your onboard graphic card controller (I assume it's Intell since I have a Dell Optiplex GX620 here at work).

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

