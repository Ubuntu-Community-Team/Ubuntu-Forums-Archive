---
title: "Ubuntu 10.10 Netbook, IBM R51 2888"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by konakid on 2010-11-09
Hi, I'm a half newbie to Linux, Yeah, I can now use terminal..

Anyway I have a IBM R51 and I got rid of Windows 7 and installed Ubuntu 10.10 :popcorn:
But it doesn't provide me with a viable display driver?? Also the center trackpoint scroll doesn't work. I install Ubuntu 8.10 to see if it changed anything (with drivers) and everything worked! It even popped up with the notification when I changed the volume or screen brightness! 

I thought maybe I could upgrade from 8.10 all the way up....but will it carry the drivers from OS to OS?? Also in the end I want the Ubuntu Netbook 10.10, is it possible to upgrade a desktop edition to the Netbook edition?

Is there some sort of drivers I could download to use with the R51 and 10.10?  Because I would like to have the ext4 file system if I could.

---

### Post by gordintoronto on 2010-11-09
What do you mean by "viable display driver"?

Personally, I'm holding off on EXT4 until it is completely stable.

What is the video adapter on your computer? The command lspci would identify it, in the line that contains "VGA".

I'm pretty sure an upgrade will always stay as the same edition. If you want 10.10 netbook, that's what you should install.

---

### Post by konakid on 2010-11-10
It has the Intel 855GME display adapter. Having ext4 isn't as important to me as having working drivers.
  Is there some way to extract the drivers which were shipped with Ubuntu 8.10 and use them in 10.10? 
 Last night I tried OpenSuse 11.1 and the drivers worked!! Even the trackpoint scroll button. Is the driver support always different between distros? Because I guess if I had to I could switch, but I really like Ubuntu:(

---

### Post by gordintoronto on 2010-11-11
In what way are the drivers not working? There's no display?

Have you tried running 10.10 netbook from a liveCD (or Live USB stick)?

---

### Post by konakid on 2010-11-11
> **gordintoronto said:**
> In what way are the drivers not working? There's no display?

Have you tried running 10.10 netbook from a liveCD (or Live USB stick)?

I have ran it from the LiveCD, and it is no different. The display works, but I don't have any 3D support, so I can't use the Unity Desktop, Comiz, or anything else graphics demanding. I tried the new Fedora and it shipped with a correct driver for the display. OpenSuse included the ultra-nav trackpoint drivers and the drivers to make the sound volume buttons work. Any other ideas? I just find it weird that it worked so well in Ubuntu 8.10..

---

### Post by tpr51 on 2010-11-15
I have that laptop ...just put ubuntu on it today ... cant say yet if everythings working but i noticed you wrote you installed the "netbook" ... unless i read it wrong it instructed me to install the "desktop/laptop" version ...which is what I did.... netbooks dont have all the built in features of a laptop/note book

---

### Post by tpr51 on 2010-11-16
i also found this 

[http://www.eastwoodzhao.com/thinkpad-middle-button-scroll-ubuntu-linux-10-04-lucid-lynx/](http://www.eastwoodzhao.com/thinkpad-middle-button-scroll-ubuntu-linux-10-04-lucid-lynx/)

hope you can get it working ...Im just starting and dont have a clue about terminal

---

### Post by konakid on 2010-11-24
Sorry I got busy with college:( But I did kinda get the bugs figured  out. Thanks for the link, but I found an easier method. Although my  method probably does the same thing at least it gives you an interface.

Here is the link for the trackpoint setup [http://psung.blogspot.com/2010/09/thinkpad-trackpoint-scrolling-in-ubuntu.html ]("http://psung.blogspot.com/2010/09/thinkpad-trackpoint-scrolling-in-ubuntu.html")
 Just in case it deletes my link what you have to do is open terminal and run 'sudo aptitude install gpointing-device-settings' 
      [FONT=Arial]If  you hate terminal than you can start synaptics and search for  'gpointing-device-settings' Once installed it will be located  in...system>preferences>pointing devices. Enable mouse wheel  emulation and set it to use button 2. :) 
   It should now work! Another  really cool thing is you can set your touchpad to scroll with two  fingers[/FONT]:grin:
  
[FONT=Arial]Ok how I fixed the display was with this link[/FONT] [http://ubuntuforums.org/showthread.php?p=10067580](http://ubuntuforums.org/showthread.php?p=10067580)
 Just in case this site deletes my link it is ubuntuforums.   org/showthread.php?p=10067580
Do exactly as the directions from the Rubi1200 reply. But I used the xorg.conf text which CharlesWelsh posted.
 Unity Desktop works but it sometimes flashes the screen when I click on  Firefox.  I did get a bug where the screen gets all garbled up and the  computer freezes. A handy hold down of  the off button and a reboot  solves the problem. 
    Otherwise this is the only working fix which worked  for me.:) Oh ya, almost forgot. If you boot up and have no mouse just  run '[FONT=Times New Roman]sudo gedit etc/X11/xorg.conf'[/FONT] [FONT=Arial]and  delete everything and reboot. (its hard without the mouse, use you  arrows if possible). Upon reboot run all the steps over again,  making  sure you fill in the xorg.conf first. [/FONT]

Here are some links to other sites which you may find helpful also. Let me know if anyone is successful with them, or if you know of a better fix.

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes#GTT%20Incoherency%20Patch](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes#GTT%20Incoherency%20Patch)

[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)


[http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/](http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/)

---

