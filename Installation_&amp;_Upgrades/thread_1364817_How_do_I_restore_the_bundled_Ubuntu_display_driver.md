---
title: "How do I restore the bundled Ubuntu display driver?"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by jmlynn on 2009-12-26
Hi,
 
I had successfully installed Ubunto 9.10 on my Toshiba notebook, with the capability of display main desktop on the internal LCD and extended desktop on a second LCD monitor.

However, after I run System/Administration/Hardware Drivers and tried to install the "recommended" Nvidia accelerated graphics drivers (version 185), it failed during install, giving me the following error:
"System error: installArchives() failed"

When I reboot the machine and click System/preferences/display, I now get the following error:
"It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's tool instead?

If I select yes, I got the NVIDIA configure screen that I have no clues as to how to configure it.  

If I cleck No, I will get a low resolution display driver.   I am also unable to extend the desktop to the external screen.  

Any idea on how to restore to the Ubuntu distribution display driver without having to rinstall Unbunto? 

Appreciate any help!

Jeff

---

### Post by audiomick on 2009-12-26
Hallo Jeff.
I would suggest having a go at the nvidia settings thing. It actually isn't that hard. 
However:

start it with
```
gksu nvidia-settings
```
in the terminal, or it wont let you save. It has to be run as a super user. That is what "gksu" does.

I've attached a picture of mine,  a desktop computer with two different sized monitors attached.

You should only have to worry about the relative position of the one screen to the other. You can change this by clicking on the picture and dragging the monitors around.

You can see in the attachment that the left screen is highlighted, and next to "position" the drop down has "absolute" selected. It also offers "left of", "right of" and a couple of others, but they didn't want to work right for me. 

"Absolute" is not complicated. The key to it is to know that the "twinview" function divides one screen up over 2 monitors. In my case, the screen is 2048x1024, which is "total width of both monitors" x "height of the bigger monitor"

(ok, now it is 2 attachments...:))
In the first picture,  monitor "AMT" is highlighted, and the absolute position is +0+128. This means "starts on the left" for +0, "up 128 pixels" for +128. The +128 is there because the monitors don't stand at quite the same height. The +128 means that the mouse goes from one to the other at nearly the same height.

In the second picture the monitor "GVT L9..." is highlighted, and the absolute position is +1024+0, which is 1024 from the left (width of the other monitor) and 0 up.

Note that the grey area above and below the AMT monitor _is part of the screen_, but is not on a monitor. It is more or less dead space. Occasionally I lose the top bar of a window up there, and have to extend the window to the right onto the other monitor to get it back.

edit: I just remembered why I used "absolute" for the position. It was because the left monitor is a bit higher up on the screen than the right (the +128 in the position). "left of" and "right of" doesn't allow for adjusting the vertical position of the monitors relative to each other.

---

### Post by jmlynn on 2009-12-26
Thank you, Michael.  I did as you suggested, and now it works, I can have the desktop extended from internal LCD to the external LCD monitor.  Great stuff.

One minor problem though, I cannot leave my external monitor connected while booting the system.  As I will get a black screen after the Grub started.  Wonder if there is any other way to configure that.

Beside, when I boot up my Ubuntu on my Toshiba notebook, to extend the desktop to the external LCD, I have to use System/Preferences/display to "detect" the external LCD.  The problem is, whenever I do that, I got the "annoying warning: "
"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"

Is there anyway to get around that as well?  I had already saved the XServer configuration.

Jeff

---

### Post by audiomick on 2009-12-26
Hi.
Glad it works so far.
I think System/Preferences/display will always call up the "annoying warning", because the item in the menu calls up the standard Ubuntu display config process, which then "sees" that you are using the nVidia driver and changes to the config tool for that. I don't think I can help with a way around that. Sorry.

If you want to start the nvidia-settings thing directly, you can add a button to the panel (task bar at the top of the screen). I just tried this, and it seems to work.

Right click on the panel, choose "add to panel"
Choose "user defined application starter" and click on "add" at the bottom
in the field "command" type in [FONT="Microsoft Sans Serif"]**gksu nvidia-settings**[/FONT]
confirm and close
When you then click on the new button, it should ask for your password then open the nVidia display settings GUI.

As far as starting with the external monitor plugged in, that sounds similar to my old Toshiba laptop. If I had an external monitor plugged in, it always booted with that as the monitor. I never got twinview working on that machine, and never worked out how to make it start to the internal monitor when an external was connected.

I think it is possible to get monitor switching working on some laptops, but I don't know how to do that either. Sorry once again...

---

### Post by jmlynn on 2009-12-27
Thanks, Michael!

I recently switched from Windows to Ubuntu.  Had been away from Unix/Linux for a long long time.  Very happy with the switch, so I can gladly accept some minor inconvenience such as this.

Appreciate all you helps!  Thanks again and wish you a great year to come!

Jeff

---

