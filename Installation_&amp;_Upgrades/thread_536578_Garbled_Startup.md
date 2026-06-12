---
title: "Garbled Startup"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by neoian on 2007-08-27
I just installed Fiesty and had to set the resolution to 1024x768 when installing or the boot screen and everything after would become garbled.

I now have it installed and added "vga=1024x768" in the boot manager thing and just the boot screen shows up, but everything after is garbled. I am using an Nvidia GeForce 6800 with my primary monitor on VGA and Secondary on DVI.

Is there any way to prevent this? This never happened on Dapper for me.

NOTE: I am pretty much a linux newbie so please explain the best you can.

---

### Post by Pumalite on 2007-08-27
The Alternate CD is for this graphics problems.

---

### Post by neoian on 2007-08-27
ok, so what do I need to do from here. Do I need to remove my current ubuntu install, or just run that CD?

---

### Post by Pumalite on 2007-08-27
You can try first: sudo dpkg-reconfigure xserver-xorg at the command line. Choose 'vesa' as your driver. Then: startx. If that doesn't work; re-install with the Alternate CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) Mark box below 'Start Download'.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by merlinus on 2007-08-27
Sorry to say, but I cannot imagine that reinstalling with the alternate cd will solve video problems afterwards.

Perhaps do a search for the correct drivers, and install them from a CLI, if choosing vesa does not get you to a gui.

-merlin

---

### Post by Pumalite on 2007-08-27
As usual Merlinus is right. I might be getting sleepy.

---

### Post by merlinus on 2007-08-27
Nah.  It's the total lunar eclipse!

Also, the OP might try removing one of the monitors to see if that helps.

-merlin

---

### Post by Pumalite on 2007-08-27
How are you doing Merlin?. It's pretty late here. BTW, what's the OP?

---

### Post by merlinus on 2007-08-27
I am just back from a day on the river.  It's a bit after nine pm here.

OP = original poster.

Keep up the excellent work!  I am learning a lot from your posts, and am continually amazed by the many resources and links.

BTW, I downloaded tribe 5 and will burn it to disk tomorrow.  I am excited to give it a spin.  Thanks for that info as well.

-merlin

---

### Post by Pumalite on 2007-08-27
There seems to be a bit of a problem with Tribe 5. I saw it in one of the threads. You might be better off with Tribe 4. At least I can vouch for it.

[http://digg.com/linux_unix/Ubuntu_Gutsy_Gibbon_Alpha_Tribe_5_Released](http://digg.com/linux_unix/Ubuntu_Gutsy_Gibbon_Alpha_Tribe_5_Released)

[http://www.linuxcompatible.org/Ubuntu_7.10_Gutsy_Gibbon_Tribe_5_s94811.html](http://www.linuxcompatible.org/Ubuntu_7.10_Gutsy_Gibbon_Tribe_5_s94811.html)

[http://www.phoronix.com/forums/showthread.php?p=11937](http://www.phoronix.com/forums/showthread.php?p=11937)

---

### Post by neoian on 2007-08-28
Ok, I tried the dpkg thing and set it to VESA got through to the desktop. It works, but when I do that I cannot open the Restricted Drivers window.

I installed the drivers manually and then restarted and got the same garbled screen on a normal boot. On my one monitor the screen says "Input Signal Out of Range" and the other one is purple with green dots on it that change when I move the mouse.

It does the same thing when I unplug either one of the monitors and reboot.

**Remember I am new to Linux so please explain what you are talking about.

---

### Post by Pumalite on 2007-08-28
Did you install 'restricted drivers' through Synaptic or did you install proprietary drivers? Do you have 'build-essential'?

---

### Post by neoian on 2007-08-28
The Restricted Drivers Manager would not come up so I followed these instructions: [http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html)

And then I restarted and then I get the same thing. Input Signal Out of Range and wild pixels.

---

### Post by Pumalite on 2007-08-28
You better restore your xserver and investigate further before attempting changes to your system. I would recommend installing drivers from the Nvidia site: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by neoian on 2007-08-29
I've already installed those, and I still get the same thing. I think either the refresh rate or resolution that it boots with is too high.

---

### Post by Pumalite on 2007-08-29
Check your monitor's specs and replace them in dpkg-reconfigure or edit /etc/X11/xorg.conf

---

