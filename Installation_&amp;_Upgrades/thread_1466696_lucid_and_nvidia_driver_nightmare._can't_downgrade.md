---
title: "lucid and nvidia driver nightmare. can't downgrade to 185"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by lordmundi on 2010-04-30
i had karmic running nicely on this new sager np8120.  It has a dual gtx285m and a 18.4" 1920x1080 screen (i'm not seeing many others with this issue, so perhaps the odd screen size is the issue).  I was running the nvidia 185 driver.

Used update-manger to move up to lucid.  Upon rebooting, had crazy blurry screen which I am typing on now.  nvidia-settings suggests it could be off because it is detecting the screen as 1024x768.  I have been desperately trying to figure out how to downgrade to the 185 driver from the 195 in "nvidia-current".

Trying to remove the "nvidia-current" wants to uninstall the 185 driver also!  I tried installing all "nvidia*glx" packages and under Administration->Hardware Drivers all I see listed is nvidia-current, and the 173 driver.

I saw some posts talking about the changes with this great new alternatives system.  Looking at the alternatives for "gl_conf" only the "nvidia-current", mesa, and 173 driver are listed.  Switching to mesa gets be a completely black screen which I have to reconfigure back via ssh.

So, I am open to either fixing the screen detection issue in the 195 driver or just figuring out how I can downgrade to the 185 driver which I think will work as before.

Can _anyone_ with some nvidia driver experience in lucid help me out??  I'm going nuts!!!

Thanks.

---

### Post by lordmundi on 2010-04-30
well, wow.  after a few hours of removing packages, installing packages, doing force installs with dpkg (yikes), I finally got something that gets me to a useable desktop.  Luckily, it doesn't need any force installs i don't think. 

I installed nvidia-current after cleaning up my mess to get back to the original 195 driver.  If you already have this (which is how lucid probably sets you up by default, then you can just fix the EDID i think).

I booted into windows and used the phoenix utility (from here: [http://www.tucows.com/preview/329441](http://www.tucows.com/preview/329441)) to capture the EDID of my flat panel (looking through all the details of the 2 you can import form the tool, one had 16:10 and one was 4:3 so obviously the 16:10 was for the laptop flat panel on the sager np 8120).  I did this by telling it to import from the registry, then told it to export, changed the file type to the "Raw 128 byte" file type, and saved the file.  For those without windows to do this and happen to have the same exact laptop as me, I'm going to try and attach the file here so you can use it - make sure you change the file extension from .zip to .raw - it is _NOT_ a zip file.

Then, I booted into linux, ssh'd into the box (because my screen is black) and edited the /etc/X11/xorg.conf file (via: sudo vi /etc/X11/xorg.conf).  I added the following lines to my "Device" section:

```

    Option         "ConnectedMonitor" "DFP-0"
    Option         "CustomEDID" "DFP-0:/etc/8120_184.raw"

```

Next, I copied the file I captured from windows in the raw 128 byte format to /etc/8120_184.raw.  Crossed my fingers.  Prayed to St. Joseph.  Then rebooted.

The screen flickered a bit like it tried a few times, but ultimately, I got a display!!!

This is pretty horrendous.

Also, this doesn't fix the fact that none of the Virtual Terminals are working and that I have a black screen throughout the entire boot process... no plymouth or anything.

ok... so my impression of lucid is not starting out to well.  

hope this helps someone.

---

### Post by rsmendivil on 2010-08-02
I'm having this problem as well.  
One thing to note is that plugging an external monitor into the DVI port brings up your desktop.  
Makes things much easier to work with.

---

### Post by rsmendivil on 2010-08-03
Just got this to work on Debian 5.05.
Now to get my external monitors working...

---

