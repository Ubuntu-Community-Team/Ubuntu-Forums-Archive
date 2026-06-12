---
title: "lower resolution after upgrade to 12.04"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by avidesh on 2012-04-30
Hello,
I recently upgraded to 12.04.
Post upgrade, my display resolution is 1024x768. In the display settings menu, I do not get any other option for higher resolution.

I was always using higher resolution before.
I use onboard graphics....Intel Corporation 82G33/G31 Express Integrated Graphics

Please suggest what I should be doing.
Avinash

---

### Post by whiskers751 on 2012-05-01
Sigh. Yet ANOTHER new kernel problem...
Ok - here's how to fix:
Hold Shift at boot
Select an OLDER kernel (lower numbers)
You may need to go into Previous Linux Versions
Hit Enter...

This will NOT permanently resolve your problems, though.
You'll have to do this every boot...

---

### Post by avidesh on 2012-05-01
No unfortunately that did not work...

---

### Post by whiskers751 on 2012-05-02
Hm. Maybe some bit changed the driver for your card!
(just saying this for the benefit of other people)

---

### Post by mycomputerstuff on 2012-05-08
Did you find out what the problem was? I'm having this exact problem also and stuck on 1024x768 resolution. I also have an Intel Corporation 82G33/G31 Express Integrated Graphics.

Installed mesa-utils but not a change in the slightest, still an unknown monitor... Everything is really slow too.

---

### Post by mycomputerstuff on 2012-05-08
I worked out a fix and here it is:

Open up a shell :

$ xrandr

(This will show you your connection type, in my case it's VGA1)

$ cvt 1680 1050 60

(Just type this in and hit enter, my refresh rate is 60. My resolution can handle 1680x1050. Copy the part after 'Modeline' e.g.
Modeline [COLOR=DarkOliveGreen]"1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync[/COLOR]
then add this to the following command...

$ xrandr --newmode "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
(Notice how I took out the "_60.00" part after "1680x1050" above? I don't know why this is but it only works if you take out that refresh bit...)

$ xrandr --addmode VGA1 1680x1050

(This should add the new resolution you used to get, my monitor only gets to 1680x1050. The VGA1 is the connection type you get in the first command i mentioned. You might have something like hdmi1 or something..)


Now check the display options, and hopefully you'll be lucky enough to get the resolution you were after.

---

### Post by mycomputerstuff on 2012-05-08
Seems that once the system is restarted, you get a big error screen and the display is back to 1024x768

To remove this error screen you have to invoke this command every time you power off the machine :

$ rm ~/.config/monitors.xml

Then to fix resolution after booting up again :

$ xrandr --newmode "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

$ xrandr --addmode VGA1 1680x1050

$ rm ~/.config/monitors.xml

---

This is a farce, can anybody help with a script that automatically does all this so we don't have to constantly do this just to see the screen properly?

---

### Post by Humanity for Others on 2012-05-08
I had a similar problem with the Unity installation.  I was able to change to a higher resolution, but it looked strange.  One thing that helped was to get the KDE (Kubuntu) installation.  After installing, I was able to choose a better resolution, with 2 more available (but those look bad also).  
 
Perhaps this issue is Ubuntu being too simplified, it's leaving some essentials behind in the "kitchen sink".

---

### Post by mycomputerstuff on 2012-05-08
I don't know man. Maybe you're right. I've never tried Kubuntu, maybe it's worth a shot. Thing is with linux, if you give up on one flavour because you can't get your head around a problem you end up finding another problem in the other.. Linux is just sooooo time consuming to fix stuff like this. I think linux is great (when it works..) Thing is, it hardly ever just works. I've been using it for years and no matter what PC or laptop I've ever installed it to I've spent hours or days trying to get the sound working or the graphics to work or the wireless card to work. I don't think I've ever actually had a linux install where i've not spent at least 5 hours trying to google troubleshooting. That's why windows will always be ahead of linux. It always just works. If linux just worked like that, my frustration wouldn't be as high as what it is right now. Problems problems problems. All I ever have. But I don't wanna use windows because it's not open source and free. It's a damn catch 22. Damn it's depressing. 

Anyway

If someone can work out a better method than the one I've made above I'm all ears. Thanks.

---

### Post by mycomputerstuff on 2012-05-09
I found a better way of doing this which doesn't involve deleting the monitors.xml file...   This is a script I made, adjust yours accordingly using the info I've already provided..   #!/bin/bash xrandr --newmode &quot;1680x1050&quot; 146.25  1680 1784 1960 2240 1050 1053 1059 1089 -hsync +vsync xrandr --addmode VGA1 1680x1050 sleep 1 xrandr -s 1680x1050 sleep 1 exit   Save it as videosettings.sh  $ chmod +x videosettings.sh  Double click on it when you log in. Sorted.

---

### Post by danielsender on 2012-05-12
I have the same problem. After executing the script the screen goes black and never returns. If I type the steps it runs and when I click on "Displays" it shows the 1600x1200 (that is my monitor) but after selecting it, it ignores it.

---

### Post by avidesh on 2012-06-04
when I boot into 11.10 on another drive (same desktop hardware & monitor) higher resolution works just fine.I am getting 1280x1024.

How to resolve this issue on 12.04

---

