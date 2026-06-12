---
title: "Resolution Issues on Fresh Install"
date: 2014-06-03
forum: Installation &amp; Upgrades
---

### Post by Willy_Sin on 2014-06-03
Hello I just installed Ubuntu on my old desktop hoping to revive it as a media PC. Installation went a little rough be all appears to be fine. When I went to boot in for the first time (after the required restart) I get a black screen with white diagonal dashes across the screen so I decided to restart. The next time and the next few times I booted in I received a totally black screen with only my mouse visible. I believe the issue to be a resolution or graphics driver issue, I'm just curious how I would go about fixing this seeing as how I can't boot into and access anything. The desktop computer is an Inspiron 531s with 2GB of RAM and the AMD x2 processor. I installed the 64bit version of Ubuntu 14.04 LTS.

attached is a picture of the diagonal lines that reappeared after another restart

Also seeing as how I just installed this and have no files whatsoever on the computer I'm totally down for anything at this point.

I'm fairly new to the world of Linux so sorry if I ask a few questions,

Thanks for any help in advance.

---

### Post by gdesilva on 2014-06-03
See if you can get to text based log in by pressing Cntrl+Alt+F2.

If you are getting the login prompt then login and check /var/log/Xorg.0.log for any errors. If there is a problem loading the graphics driver you will find it here. Type 'cat /var/log/Xorg.0.log | grep EE ' to show the messages with errors.

Type 'lspci -v' to find out what graphics card is in use. Once you identify the graphics card, ati, nVidia etc, then you would need to make sure that the right driver is loaded. 

Edit /etc/X11/xorg.conf and the Device section is where you need to state which driver should be loaded. You have to have root privileges to edit this file. Save file. Now do 'startx' as your normal userid (not as root) to see whether you can get the graphics screen going.

Hope this makes sense.

---

### Post by keats4 on 2014-06-04
Okay I got as far as the "edit" when I try to do that command I get an error saying I have "no write permission" for that file. The first two commands worked nicely and there does seem to be some type of error with the loading of the nvidia files. 

[    17.532} EE Failed to load module "nvidia" (module does not exist, 0)
also 
     [     17.577]

I suppose my preference would be to find this module else where download it onto a USB drive and sneak it onto the hard drive. (that would be my windows solution) but maybe there is a more elegant solution I don't know about.

Also is there perhaps a generic driver we can direct the startup to until we get this problem solved?

ONE MORE POINT OF INTEREST . . . the 531s does have an AMD processor . . . I didn't use the AMD64 install since is "seems" to be for the MAC.


Thanks for any help . . .
by the way I'm not the original poster but I have the same problem.

---

### Post by Willy_Sin on 2014-06-04
When I hit ctrl+alt+f2 and just kept holding ctrl+alt and tapping f2 I got into the grub menu now. I can do Ubuntu, Advanced Options for Ubuntu, or Memory Test.

Is this the correct location do I then go into advanced options? in there I have Ubuntu, with Linux 3.13.0-24-generic or Ubuntu, with Linux 3.13.0-24-generic (recovery mode).

Ubuntu is the only OS installed on this computer so should I even have a grub menu?

---

### Post by Willy_Sin on 2014-06-05
I don't know exactly what I did but somehow I booted into regular Ubuntu. Going into Display settings the correct resolution for my monitor is not available. What would you suggest I take as action first?

My current graphics card is listed as VESA: MCP61-mcp61-85

---

### Post by grahammechanical on 2014-06-05
@keats4

please open your own thread as it becomes very confusing trying to offer advice to more than one person.

Regards.

---

### Post by Willy_Sin on 2014-06-05
After getting Ubuntu to boot like a regular computer but having the wrong resolution, I went into additional drivers and selected the Nvidia proprietary one and restarted and now all is well, computer is running smoothly.

Thanks for the help everyone

---

### Post by justtryit on 2014-06-30
I am new to Ubuntu and running 14.04 Ubuntu 64bit on an AMD Athlon64x2 machine (m7664x), and sometimes seeing a similar display, second GUI screen, at bootup time.  I recognize that this is not a solution to the problem - I haven't found that yet -  but perhaps it might be useful to some as a temporary work-around so as to avoid having to "reboot and hope".  Perhaps you already know this, but...

I found that I can get back a normal login display by doing an alt-ctl-F1 followed by an alt-ctl-F7.  (...information originally gleaned sometime back from this forum.)

---

