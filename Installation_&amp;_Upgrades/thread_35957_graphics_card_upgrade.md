---
title: "graphics card upgrade"
date: 2005-05-21
forum: Installation &amp; Upgrades
---

### Post by sharmaravi on 2005-05-21
Hi,

I am trying to solve this problem for last few hours and I do not know what to do now. May be someone here can help.Here is the problem :

 I had an old nvidia card and I had hoary installed on my computer. Everything worked fine. Yesterday I upgraded my video card (FX5700LE) and now I can boot into linux but X does not start. It seems to be complaining something like fonts registered to 0... I do not remember the exact error but may be I am missing some steps that are needed upon upgrading a hardware. Can somebody help me on this. 

Live cd works fine with this card using nv driver. Also X starts with nv driver. Windows sure works with nvidia drivers but nvidia driver does not work in linux. Please help.

---

### Post by nad on 2005-05-21
At the terminal screen, issue the command: dpkg-reconfigure xserver-xorg

This will redo your xorg.conf file. You may wish to retain a copy of the original file. I don't know if your existing nvidia driver will be picked up. If not, try manually changing the driver line. I also do not know if the installed proprietary driver becomes hardcoded to your (old) hardware upon installation, in which case you can try dpkg-reconfigure nvidia-glx, or a remove and re-install.

---

### Post by sharmaravi on 2005-05-21
Hi nad, thanks a lot for responding. 

I tried dpkg-reconfigure xserver-xorg and it did pick up nvidia driver but the xorg.conf created did not help. I got a blank screen just like before.

I also tried dpkg-reconfigure nvidia-glx and reinstalling nvidia-glx, but still no go. Not sure what should I try next.

Anymore ideas, ready to try anything.

---

### Post by SickTwist on 2005-05-21
Perhaps you could try changing the graphics driver from "nvidia" to "nv" (which is the free software driver for nvidia cards) in /etc/X11/xorg.conf

sudo vi /etc/X11/xorg.conf
press "i" (without quotes) to enter insert mode in vi
find the part that says...
Driver "nvidia"
and change it to this:
Driver "nv"
type ":wq" (without the quotes) to save the file and quit
sudo /etc/init.d/gdm restart

I'm not sure if it will work or not but that's what I would try if I were in your shoes.

---

### Post by sharmaravi on 2005-05-21
Hi SickTwist, I already know that it works with nv , I was trying to make it work with nvidia. Anyway, thanks for trying to help.

I found the solution in another post. All I had to do is add 
       Option    "ConnectedMonitor" "DFP"
in the device section of xorg.conf. It seems sometimes nvidia driver can not find out where the monitor is connected, i.e. vga or dvi. It is also documented in /usr/share/doc/nvidia-glx/README.gz

Thanks all. Now its time to tweak it further  :grin:

---

