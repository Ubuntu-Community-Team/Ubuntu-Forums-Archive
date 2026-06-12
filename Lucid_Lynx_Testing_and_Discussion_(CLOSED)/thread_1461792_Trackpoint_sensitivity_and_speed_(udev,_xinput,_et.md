---
title: "Trackpoint sensitivity and speed (udev, xinput, etc. frustration)"
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jblackhall on 2010-04-24
Does anyone out there know how I can PERMANENTLY change my trackpoint sensitivity and speed settings.  I've tried about 15 different methods, and I'm extremely frustrated.  I managed to get middle button scrolling working right away.  I've tried multiple methods listed here: [http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint)

---

### Post by jblackhall on 2010-04-25
bump

---

### Post by jblackhall on 2010-04-27
No one? :(

---

### Post by Untitled_No4 on 2010-04-27
I never really changed those settings so I don't know what to expect when I change them, but try these two commands in terminal:
```
xinput set-int-prop "ThinkPad Extra Buttons" "Evdev Sensitivity" 8 X
xinput set-int-prop "ThinkPad Extra Buttons" "Evdev Speed" 8 X
```

Change X to your desired settings and please report back to let me know if it works.

---

### Post by Untitled_No4 on 2010-04-27
Actually, I stand corrected. The above shouldn't work because it's not for the TrackPoint

Speed:
```
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Speed" 8 X
```
with X being your desired setting, but I can't see a difference if I set it to 1 or 99, but perhaps I'm not very sensitive to those kind of things.

I can't see any settings for sensitivity though. If you run 
```
xinput list-props "TPPS/2 IBM TrackPoint"
```
you will get the TrackPoint properties and there is no sensitivity, but perhaps you can recognise which property it is uses instead of sensitivity. Again, I've never changed the default settings so I don't even know what to expect...

---

### Post by jblackhall on 2010-04-27
> **Untitled_No4 said:**
> I can't see any settings for sensitivity though. If you run 
```
xinput list-props "TPPS/2 IBM TrackPoint"
```
you will get the TrackPoint properties and there is no sensitivity, but perhaps you can recognise which property it is uses instead of sensitivity. Again, I've never changed the default settings so I don't even know what to expect...

Agreed, I looked at xinput list-props, but I didn't see anything that seemed related to the sensitivity/speed or anything I felt confident enough to change.  Maybe I'll try something though...

---

### Post by jblackhall on 2010-04-29
Any other ideas anyone?

---

