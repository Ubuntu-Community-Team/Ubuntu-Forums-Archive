---
title: "Synaptic Touchpad sensitivity"
date: 2008-09-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by babyhuey on 2008-09-06
Is there anyway to adjust a synaptics touchpad sensitivity/acceleration other than xorg.conf?

I have a first gen macbook which it detects to have a synaptic touchpad, but it is painfully slow. 20 or so swipes to get across screen.

The settings under System>Preferences>Mouse have little to no affect on the touchpad. They do work as expected for my mouse though.

---

### Post by hexion on 2008-09-06
I also noticed the huge sensitivity difference between Hardy and Intrepid.
Using the mouse is ok, but when I use the touchpad booting with Intrepid is so painful. Even the best combination between sensitivity/acceleration keeps the touchpad unusable, just too slow.

I really think there should be a different configuration tab for the touchpad and for the mouse but those changes must come upstream.

---

### Post by windozehater on 2008-09-06
Try the app qsynaptics its in the repo's there is also gsynaptic but i feel it is not as configurable but you most likely will have to modify your xorg to add a line for this feture but it is not hard follow the error prompt.

---

### Post by robzon on 2008-09-06
I have the same issue with touchpad on my MacBook (3rd gen). Furthermore, bluetooth input services don't even show up in bt settings, so I can't use my mouse! Things look pretty bad right now.

---

### Post by stari4ek on 2008-09-06
> **babyhuey said:**
> Is there anyway to adjust a synaptics touchpad sensitivity/acceleration other than xorg.conf?

I have a first gen macbook which it detects to have a synaptic touchpad, but it is painfully slow. 20 or so swipes to get across screen.

The settings under System>Preferences>Mouse have little to no affect on the touchpad. They do work as expected for my mouse though.

1. add 
 Option         "SHMConfig" "on"
to xorg.conf

2. restart X
3. start gsynaptics

you can tune sensitivity, acceleration and stuff

---

### Post by hexion on 2008-09-07
Solved. Thanks :)

I think gsynaptics and qsynaptics should be added in the default installation of Ubuntu and Kubuntu respectively..

---

