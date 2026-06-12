---
title: "Ubuntu 7.10 hangs on boot after first install"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by das88 on 2008-01-29
Hi, I'm new to Ubuntu and I'm trying to install 7.10 on my Averatec av2260-eh1 laptop. I had 6.10 installed but wasn't able to get my wireless card to work. After loading the 7.10 live cd, I'm happy to report that all my network needs have been taken care of automatically (go Ubuntu!). There is, however, another issue (and I apologize in advance if this is something that's been dealt with already! I looked around online but I couldn't find any workable solutions...)

When I boot from the live cd my resolution is too low to use the installation application (I can set it at a maximum of 800x600 on a widescreen lcd meant for 1280x768 ). I'm a little surprised that the resolution is low because 6.10 had it automatically set to 1024x768. I've read in several different places that one solution is to reconfigure the video settings for xserver. I've tried that using the settings for my video hardware (I have an S3 Chrome9 chipset integrated onto a VIA motherboard) and also with some generic settings that were supposed to get it at least up to 1024x768. Neither reconfig worked. I used the command 

sudo dpkg-reconfigure xserver-xorg

to configure the video settings from the terminal both times. After hitting ctrl-alt-backspace I still only had access to 640x480 or 800x600 resolutions from the screen resolution menu in system->preferences. Is this because I'm running the live cd and the file I'm editing resides on the disk rather than the hard drive? And why does my system auto-config to 1024x768 in 6.10 and 800x600 in 7.10?

After screwing around with that for a few hours I decided to try the alternate cd and do a text-based install. The installation worked fine but when I try to boot after installing the operating system it hangs at the line "running local boot scripts /etc/rc.local" (all though that path may not be exactly right... I'm having trouble remembering). I don't believe it gets to the point of displaying an [ok] at the end of that line, I think it just stops as soon as it starts loading that file. Also, it's not a hard lock. I can ctrl-alt-del to reboot and the screen displays what I type (which is weird. Why will it display what I'm typing when it's supposed to be in the middle of something?). I looked around online a bit and a few people talked about this being related to video settings, so I reinstalled via the alternate cd and instead of using my native screen resolution (1280x768 ) when prompted, I told it to use 1024x768. It finished the install just fine and behaves exactly the same way when I try to boot now. I'm pretty much stuck at this point. Is the boot problem even related to my video drivers? I've checked to be sure both disks (the live cd and the alternate cd) are valid and they are. Any suggestions would be much appreciated and thanks a bunch for your help!

P.S.
I'm a super-newbie but can anyone point me to a good introduction to the X Window System in Linux? I understand all the settings I input when I reconfigured xserver but I don't really know what xserver is or how it works. I'd also like to get a little more familiar with the linux boot process (for instance, how do I tell linux to give me more information as it boots? And can I pause it to read the output?) Thanks everybody!

Edit: The path I quoted is correct but the system *does* finish the line (it displays [ok] at the end of the line) and then hangs. I am also running an AMD Turion64 system if that helps.

---

