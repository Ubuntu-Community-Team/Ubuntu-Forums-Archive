---
title: "Xorg Fatal IO error, no screens loaded"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by tamarku on 2006-06-02
OK, anyone know how to get around this one?  I ran the upgrade via the Update-Manager.  All 'seemed' to go fine.  When came time to reboot I am getting a fatal IO error.  A message about can't load screens.  I get a black screen with a login I can login and move around but it seems the Xorg file is hosed up somehow.  I do have an NVidia 5200 Geforce video.  Breezy was nice and stable so this is kinda bummer.  I wanted to wait but the temptation to upgrade was toooo great.  Anyway, any help would be greatly appreciated.  Right now I am running on an Xubuntu live CD.  So the network seems to be working and all.  Thanks in advance.

---

### Post by pyromithrandir on 2006-06-02
You were probably using the proprietary Nvidia driver on breezy, right?
And, when you upgraded, you got a new kernel and the Nvidia module isn't in this new kernel. So, you can do 1 of 2 things (or both if you want).
The easiest way to get you back up and running would be to edit your /etc/X11/xorg.conf and find the "Device" section, and the Driver line. Replace where it says "nvidia" with "nv". You won't be using the proprietary driver anymore, but your X should work :)
The other thing is to just reinstall the nvidia driver. You could do that instead of what I just said, or you could do it afterwards.
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) -- That's the page that'll get you the nvidia driver. If you're using an 32 bit processor, here is a more direct link to what you want. -- [http://www.nvidia.com/object/linux_display_ia32_1.0-8762.html](http://www.nvidia.com/object/linux_display_ia32_1.0-8762.html)
It has a little guide on that page that should get you up and running.

---

### Post by tamarku on 2006-06-03
GOT IT!! Whew, actually what I did was sudo dpkg-reconfigure xserver-xorg.  Basically, it did exactly what you said.  Thanks for the reply.  Can I ask that if I followed a thread by poofyhairguy to install xgl and compiz would that have installed the drivers for my nvidia fx5200 geforce video card? If not could I go ahead and install them now?

---

### Post by pyromithrandir on 2006-06-03
Yeah, if you follow that thread, it'll install the nvidia drivers. You don't need to follow the thread to do it, but, hey, whatever floats your boat.

---

