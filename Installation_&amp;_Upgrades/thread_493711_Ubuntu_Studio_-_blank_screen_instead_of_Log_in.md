---
title: "Ubuntu Studio - blank screen instead of Log in"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by Tsega on 2007-07-06
Hi there people I just installed Ubuntu Studio 7.04 and the installation went very smoothly and once it finished installing, I rebooted and the right after the screen with progress bar, the screen goes blank. That was supposed to be the Log in screen but it's not there. I tried to search for this in the forum and I found a post saying that the person had the same problem but he fixed it. The problem is he really doesn't describe the way he fixed it clearly here is the link to the post.

[http://ubuntuforums.org/showthread.php?t=449215&highlight=ubuntu+studio+login+problem](http://ubuntuforums.org/showthread.php?t=449215&highlight=ubuntu+studio+login+problem)

I was wondering if someone could help. Thanks

---

### Post by jackocleebrown on 2007-07-06
Hi,

I've not come across your problem myself but I can translate the fix that **proclaimation** describes in that thread into some commands for you to try.....

1) when you get to the blank screen after bootup hold down ctrl+alt and press F1 hopefully after a couple of moments you will see a terminal with a text login prompt.

2) login using your username and password that you setup in the install.

3) from the command line 

sudo mv /etc/X11/xorg.org /etc/X11/xorg.bak

4) reboot
(it seems strange to do this at this point because you have no config file for X.... but that is what **proclaimation** says worked for him....)

If you want to change back you can use the command
sudo mv /etc/X11/xorg.bak /etc/X11/xorg.conf



Jack.

---

### Post by Tsega on 2007-07-07
Thanks Jack I'll try it right away and post the result so nobody has to ask this question again.

---

### Post by Tsega on 2007-07-07
Sorry man that didn't work. It said that the it couldn't find the X configuration file. And X could not start. I don't know what's happening can you suggest anything. 

**[COLOR="Orange"]Here's a thought[/COLOR]**, I have the Ubuntu Feisty Live CD, I can run it see the contents of the xorg.conf file and replicate them manually into my Ubuntu Studio Installation. How's that sound?

---

### Post by Martin Witte on 2007-07-07
looks like a wrong video driver, try to replace it with the vesa driver, as this works almost always. try to edit /etc/X11/xorg.cong - after making a backup of course, and the find the section 'Driver', mine looks like 
Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS/940GML Express Integ
rated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection
 
replace here your entry - where i have 810 -with vesa, and save the file. restart and hopefully you got a login.

---

### Post by Tsega on 2007-07-07
It's already vesa and it goes like this.
```

Section "Device"
             Identifier      "Generic Video Card"
             Driver            "vesa"
             BusID            "PCI:0:1:0"
EndSection 

```

Thanks Mike but I still have the problem.

---

### Post by 043087m135 on 2007-07-07
from the text console (either bot into REcovery mode or hit ctrl alt f1 at blank screen) try ```
sudo dpkg-reconfigure -phigh xserver-xorg
```. see if that helps. tell us what driver it recommends (highlights by default) and whether you get a login after reboot. also, do you have a multi-head card? is there more than one place to plug in a monitor or tv?

---

### Post by Tsega on 2007-07-07
Tried it before and it didn't help. I couldn't log in after reboot as well and the recommended driver was **vesa** and I did choose that.

> do you have a multi-head card? is there more than one place to plug in a monitor or tv?

No, I don't.

---

### Post by jackocleebrown on 2007-07-08
Sorry to see this is still not working for you, what video card do you have? I'm pretty sure I've seen some threads that mention trouble using anything but the fglrx driver with ati video cards and Ubuntu Studio.

Jack.

---

### Post by Tsega on 2007-07-20
**[COLOR="DarkRed"]Sweeeeeeeeeeeeeeettttttt![/COLOR]**
it works, I love this! It's pretty and it's useful. I or rather we fixed. Here's what I did

1. Booted my PC with the 7.04 Live CD.
2. Checked out/wrote down the contents of the /etc/X11/xorg.conf file. I noticed that the values for the **Identifier** and **Driver** variables under the "**Device**" Section were different from the ones that I had while I tried to boot with Studio. 
3. Booted without the live CD into Studio and at the place where my screen turns blank I pressed down ctrl+alt and F1 to go into the terminal.
4.After I logged in  I typed the command "sudo vi /etc/X11/xorg.conf" and I typed in "a" (in order to edit the file )and then went down the Driver section as well as the section with all the resolutions in it and I typed in the appropriate values. (Sorry I forgot the exact details):( 
5. Saved the file and restarted my PC. 
6. Behold it was the Studio alive and kickn'. 

Thanks everyone for all your help and I am really glad that Ubuntu has such a great community. Peace

P.S Sorry for not posting it back asap (I think I did it on the same day of my last post)

---

