---
title: "Low graphics mode"
date: 2010-10-03
forum: Installation &amp; Upgrades
---

### Post by voucherman on 2010-10-03
As a recent Ubuntu convert (installed 10.04 to get rid of Vista) I've managed to sort most problems but have not been able to fix the graphics driver. 

I've not been able to find a graphics driver for my monitor (SiS Mirage 3 Graphics - SiS 307ELV) but found that choosing [COLOR=DarkRed][COLOR=Black][COLOR=DarkRed]Create new configuration for this hardware [COLOR=Black]on start up [/COLOR][/COLOR][/COLOR][/COLOR]it would fix the resolution.

Unfortunately every time I re-start it reverts to low graphics mode.



[COLOR=DarkRed]Ubuntu is running in low graphics mode.
The following error was encountered. You may need to update your configuration to solve this.

(EE) FBDEV(0): EGA/VGA planes are not yet supported by the fbdev driver.


[COLOR=Black]After choosing 

[COLOR=DarkRed]Reconfigure graphics - Create new configuration for this hardware
[/COLOR]
I  got the message

[COLOR=DarkRed]A new configuration has been generated and your old configuration backed up
Please restart[/COLOR]


The screen then returns to a 1280x800 resolution and from recent  experience will remain until I have to restart, when it will go back to  800x600 with the error message.



Can the settings be saved so that I don't have to keep re-configuring?[/COLOR][/COLOR]

---

### Post by P4man on 2010-10-03
Support for SiS video is.. aweful. But googling I came across this here:
[http://ubuntuforums.org/showthread.php?t=958967&page=38](http://ubuntuforums.org/showthread.php?t=958967&page=38)

If you feel like trying, you may even get video acceleration.

---

### Post by voucherman on 2010-10-03
Thanks for the reply.

I came across this page via a google/Linux forums link a few weeks ago.

I'm not sure if I typed it all correctly but I think it's only since then that I've been able to re-configure the graphics. Before then I don't think the option was there.

I'll print the page out and try again.

---

### Post by Claus7 on 2010-10-03
Hello,

since you are able to solve your problem like that, then the only thing that remains is to make it permanent. Depending on your graphics card driver, you could create a xorg.conf file comprising all the data needed so as your computer to boot normally. After you have fixed your resolution try to type these commands. Beforehand go to /etc/X11 and see if a xorg.conf file exists. If affirmative, make a backup as root and test afterwards the differences you might have.

for nvidia I think the command is nvidia-settings and for ati aticonfig --initial

Regards!

---

### Post by voucherman on 2010-10-06
Thanks again.

Success this time. I think on my original attempt I didn't pay attention to upper-case characters, typing everything in lower-case.

So if anyone comes across this thread while looking for an SIS driver - keep trying it will probably work.

---

