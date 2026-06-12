---
title: "Nvidia 6150 se with a 22 HP w2207h monitor"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by darrowj on 2008-11-30
I just bought a new HP (model a6622f, Nvidia 6150 se, Monitor 22 HP w2207h, 5G Ram, 500G HD) PC yesterday and spent half the night trying to get Ubuntu loaded.  My problem centered around the monitor I believe.  I kept getting an "Out of range" message.  My hope here is to maybe... maybe save someone else some pain.

I'm a relative newb at Ubuntu so go bark at someone else if this all sounds wrong.  I got things working and did what I needed to with limited understanding and documentation.    

First, I ended up installing with the Alternate Installation CD.  I did that after the Desktop CD failed to install all together or more accurately I could not see the install to continue.  The OS installed with the Alternate Installation but I *still* got the message that the display input was "Out of Range" after starting up for the first time.

I ended up having to get an old monitor.  I hooked it up and could finally see the Desktop.  Afterward I went back and forth between the old monitor and the new until the new started working.  If I had done this originally I probably would have used the traditional Desktop install CD.  

I tried to install the Nvidia driver directly from the Desktop but for some reason I cannot explain they would not Activate. (I found later that running "sudo apt-get update" beforehand might help but I'm not sure.)  

I ended up finding and downloading the Nvidia Drivers I needed at the following link:  
[http://www.nvidia.com/object/linux_display_amd64_177.82.html](http://www.nvidia.com/object/linux_display_amd64_177.82.html)

I tried exiting x win and getting to a commandline with "sudo /etc/init.d/gdm stop" but my system simply froze.  To put it plainly I have no idea how to exit the X win (Server) from a normal login to Ubuntu.  However, It appears as though that is what should be done to install the driver correctly.  Meaning that you cannot install the driver from Nvidia with the X system running.

I instead rebooted to the recovery mode and got a commandline prompt from there to install the drivers.  I executed "./NVIDIA-Linux-x86_64-177.82-pkg2.run" and ignored or accepted all the scary messages (the one that explains that a Kernal Interface(?) needs to be recompiled made me close my eyes and press the enter key... WTF was that all about?).

Anyway, I rebooted afterward and automagically my new monitor started working.  My resolution is set to 1680 x 1050 and it looks beautiful.  I did *not* edit my xorg.conf file at all.

One difference I see is that my Nvidia configuration is now under "Applications > Systems Tools" instead of "System > Administration" like on my old PC but I really don't care.  Nvidia Driver version is 177.82.

---

