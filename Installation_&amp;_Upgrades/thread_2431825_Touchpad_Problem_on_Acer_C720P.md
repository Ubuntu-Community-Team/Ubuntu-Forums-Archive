---
title: "Touchpad Problem on Acer C720P"
date: 2019-11-22
forum: Installation &amp; Upgrades
---

### Post by Ronco Pizatto on 2019-11-22
I flashed SeaBios on my Acer C720P and installed Ubuntu 18.04.3 with Gnome 3.28.2 as the only OS.

I ran Software Updater and got all current files. All worked fine.

I installed some software. All fine.

When I installed Gimp the touchpad lost left click. I checked Settings and verified that the primary button was still set to Left. 2 fingered right click works fine.

Using the touchscreen I used Settings to turn off the touchpad and immediately turn it back on. Left click was restored. All works fine.

I tried a clean setup again and found that some other software in addition to Gimp can kill the left click. But turning the touchpad off and then on always fixes the problem.

I also found that a mouse has the same problem as the touchpad.

I would like to know the source of the problem but just an automatic way to turn the touchpad off and then on would help.

I can do that with xinput manually but I've never written an sh file successfully.

Please help.

---

### Post by yancek on 2019-11-22
The command to turn the touchpad off= synclient TouchpadOff=1
Turn it back on=synclient TouchpadOff=0

Just put the command in a bash script and make the script executable.

---

### Post by Ronco Pizatto on 2019-11-22
Good idea. My C720P does not have the synaptic driver and will not work using it. But I agree with your idea.
I can use xinput set-prop "Touchpad Name" "Device Enabled" 0 to switch off and same command with "1" to switch back on.

I'll try my luck at writing the bash script and let you know.

---

### Post by Ronco Pizatto on 2019-11-25
Ok. Here's a work around for the Acer C720P that works really well.

I found that once booted the left click is inactive.
But if I went to settings and switched the touchpad off and then back on. All works fine.

I tried setting the disable touchpad while typing from settings but that didn't work.

However, I installed the software Touchpad Indicator.

[http://ubuntuhandbook.org/index.php/2018/04/install-touchpad-indicator-ubuntu-18-04-lts/](http://ubuntuhandbook.org/index.php/2018/04/install-touchpad-indicator-ubuntu-18-04-lts/)

Then I set "Disable Touchpad While Typing" and AutoLoad option from Touchpad Indicator setup.

I rebooted and found I had the same behavior until I pressed a key on the keyboard. Boom! Problem solved. All is good.

I'm not going to explain it but obviously Touchpad Indicator uses a different command from Ubuntu Settings to disable while typing.

Also set the millisecond delay low to avoid lag. I used 200 or 300.


Also i frequently get an error message shortly after boot up. But the system is stable and there is no performance problem. So no big deal.

If you have a choice for Chromebook conversion get the Acer C720 and not the C720P.
My C720 conversion was easy except for key mapping which is not hard if you have current info (which was hard to come by for me).
I think this should be the end of this thread.

---

