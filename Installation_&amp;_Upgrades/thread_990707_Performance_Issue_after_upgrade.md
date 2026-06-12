---
title: "Performance Issue after upgrade"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by PPPP on 2008-11-23
I just upgraded from Gutsy LTS to 8.04 LTS and I'm noticing some performance issue.  I find it a lot less responsive comparing to before.  Here is a list of processes sorted by memory usage from top:

```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                   
 9657 plui      20   0  199m  87m  27m S  6.8  8.7   0:12.11 swiftfox-bin                                                              
 9206 plui      20   0  235m  83m  17m R 17.4  8.3   0:32.06 Xgl                                                                       
 9269 plui      20   0 91072  31m  16m S  0.0  3.1   0:03.50 nautilus                                                                  
 9267 plui      20   0 58776  29m  15m S  0.8  2.9   0:03.26 gnome-panel                                                               
 9048 root      20   0  185m  27m 7540 S  0.8  2.7   0:04.18 Xorg                                                                      
 9058 root      20   0  185m  27m 7540 S  0.0  2.7   0:00.00 Xorg                                                                      
 9371 plui      20   0 61444  24m  15m S  0.0  2.4   0:00.90 tomboy                                                                    
 9428 plui      20   0  109m  22m  13m R  0.8  2.3   0:00.92 gnome-terminal                                                            
 9296 plui      20   0 42192  17m  10m S  0.0  1.7   0:00.22 python                                                                    
 9356 plui      20   0 22996  15m 6832 S  0.0  1.6   0:02.78 compiz.real                                                               
 9380 plui      20   0 57836  14m 9.9m S  0.0  1.4   0:00.20 mixer_applet2                                                             
 9289 plui      20   0 40400  13m 9.8m S  0.0  1.4   0:00.14 update-notifier                                                           
 9376 plui      20   0 48560  12m 9300 S  0.0  1.3   0:00.12 gweather-applet                                                           
 9311 plui      20   0 50276  10m 8892 S  0.0  1.0   0:00.22 nm-applet                                                                 
 9226 plui      20   0 40016  10m 7920 S  0.0  1.0   0:00.37 gnome-settings-                                                           
 7097 plui      39  19 30056 9.8m 2896 S  0.0  1.0   0:17.58 trackerd                                                                  
 9403 plui      20   0 18552 9932 7044 S  0.8  1.0   0:00.26 gtk-window-deco                                     
```

What can I do to improve the performance?  I notice there are 2 Xorg.  Why is that?   Also, For some reason, my desktop just shows up as white.  I can't see any icon nor my wallpaper.

Thanks for any help.  :)

---

### Post by inobe on 2008-11-23
tell us how xgl got on there, did you install that ?

---

### Post by PPPP on 2008-11-23
I might have installed it in the past to get compiz working but I'm not sure...do I need it?

---

### Post by PPPP on 2008-11-23
Ahh okay I think now it works better.

I have removed xserver-xgl and in /etc/X11/xorg.conf, I have enabled Composite:

        Option          "Composite"     "1"


Now it works better :)

---

### Post by inobe on 2008-11-24
good deal, if you want great affects' check out fusion.

---

