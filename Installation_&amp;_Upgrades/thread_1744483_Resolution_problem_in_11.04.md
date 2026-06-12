---
title: "Resolution problem in 11.04"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by This_is_mike on 2011-04-30
So fist i tried updating ubuntu from 10.10 to 11.04. It didn't work out, i got just a black screen trying to load new ubuntu. Nevermind, after multiple tries to recover it i simply installed ubuntu 11.04 over it. It works fine now, but i already got some problems :( Mainly, i can't find a way to pick the appropriate resolution. 

I have a 19" monitor with 1280x1024 resolution, video card is nvidia 8500gt. Any GUI tool (nvidia driver settings or 'monitors' tool) doesn't allow me to pick what i want.

xorg.cong is nearly empty, that's all what i have there 

> Section "Device"
   Identifier   "Default Device"
   Option   "NoLogo"   "True"
EndSection


I did some google searches and found out about Xrandr (i'm not much a techy really). That's what i get running xrandr in the terminal

> xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   512x384        57.0  
   400x300        58.0  
   320x240        59.0  
  “1024x768_60.00&#8243; (0x17f)   63.5MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.8KHz
        v: height  768 start  771 end  775 total  798           clock   59.9Hz


Quite embarrassing...  Any thoughts?

---

### Post by dino99 on 2011-04-30
follow this link to modify the "monitor" part (sudo gedit /etc/X11/xorg.conf)

[http://ubuntuforums.org/showpost.php?p=10742921&postcount=7](http://ubuntuforums.org/showpost.php?p=10742921&postcount=7)

---

### Post by This_is_mike on 2011-04-30
Sorry, i'm really not sure which options i should set.

---

### Post by dino99 on 2011-04-30
have you edited /etc/X11/xorg.conf ? (or created using nvidia-settings) then modify it by adding HorizSync & VertRefresh values of your monitor


Section "Monitor"
Identifier "Configured Monitor"
# add these custom lines with the monitor doc values to workaround boot issue
HorizSync 31.0 - 48.0
VertRefresh 56.0 - 65.0
Gamma 1
# adapt these values depending on your monitor
EndSection

---

### Post by teachop on 2011-04-30
I think I would do an experiment from the command line, using xrandr which you have already used, as you know the resolution that you are looking for...

Since the modeline isn't being show with xrandr, first I would try the utility gtf or something similar to create it.

Then, xrandr --newmode can be used with the resulting new modeline.

Then, xrandr can set the output to use the modeline.

Then, if it all does what you want, it can be made permanent but I have to search that, just saw that in a post earlier today.

EDIT:  This looks really close to what I was thinking to do:[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html")

---

### Post by This_is_mike on 2011-04-30
> **dino99 said:**
> have you edited /etc/X11/xorg.conf ? (or created using nvidia-settings) then modify it by adding HorizSync & VertRefresh values of your monitor


Section "Monitor"
Identifier "Configured Monitor"
# add these custom lines with the monitor doc values to workaround boot issue
HorizSync 31.0 - 48.0
VertRefresh 56.0 - 65.0
Gamma 1
# adapt these values depending on your monitor
EndSection


Sorry again... Can you please point out which values i should set for  HorizSync & VertRefresh? THis is what i googled out about my monitor specifications [http://reviews.cnet.com/lcd-monitors/benq-fp93g-lcd-display/1707-3174_7-32549764.html](http://reviews.cnet.com/lcd-monitors/benq-fp93g-lcd-display/1707-3174_7-32549764.html) , but i can't seem to find the figures i'm looking for

---

### Post by This_is_mike on 2011-04-30
I googled some examples and set 

 >    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0

It did the trick. Now i can set the proper resolutuion. Have i dove everything right? In this case, we can close the thread :D

---

### Post by This_is_mike on 2011-04-30
eh, the only thing still remaining is the fact the resolution reverts to 'auto' instead of 1280x1024 like it should be after a restart. And 'auto' strangely is 1024x768. How can i avoid this?

I know, you must be hating me already :D

---

