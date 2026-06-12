---
title: "xubuntu8.04beta recognizes USB camera but doesn't put icon on desktop"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by hanzj on 2008-04-06
I plugged in my digital camera  to usb port, powered on camera, but there's no icon on desktop. I expected to see a desktop icon.

When I go through the above steps with my iPod, I see an iPod icon on my desktop, but how come there's no icon with my digital camera.

Doing "lsusb" in terminal shows:> 
Bus 001 Device 005: ID 04a9:3074 Canon, Inc. PowerShot A60 (ptp)so the computer does indeed know that the camera is plugged in. 


I would like to import my photos from camera to computer. How do I do so?

---

### Post by kostkon on 2008-04-06
> **hanzj said:**
> I plugged in my digital camera  to usb port, powered on camera, but there's no icon on desktop. I expected to see a desktop icon.

When I go through the above steps with my iPod, I see an iPod icon on my desktop, but how come there's no icon with my digital camera.

Doing "lsusb" in terminal shows:so the computer does indeed know that the camera is plugged in. 


I would like to import my photos from camera to computer. How do I do so?
I think you are not supposed to see an icon on your desktop, because your camera is in [*PTP* ]("http://en.wikipedia.org/wiki/Picture_Transfer_Protocol")mode. Thus, the thing you have to do is to run *gThumb* (or *F-Spot*) and select their *Import Photos from Camera* option.

You can change the mode of your camera to *USB Mass Storage Device* (like an *Ipod*), if you like, and when you connect it to your PC, you will see an icon on your desktop. Then, you will be able to drag-drop your photos.

Which mode you use depends on your preferences and maybe on which of them actually works. I mean, there are some cases when, for example, the *USB Mass Storage Device* mode of a camera does not work in Ubuntu so you have to change the mode to *PTP*.

---

### Post by hanzj on 2008-04-06
can my camera, a Canon PowerShot A60,  be set to *USB Mass Storage Mode*?
Manual here: [http://www.2shared.com/file/3104599/f0eba04e/canon_powershot_a60_manual_user_guide.html](http://www.2shared.com/file/3104599/f0eba04e/canon_powershot_a60_manual_user_guide.html)

---

### Post by kostkon on 2008-04-06
> **hanzj said:**
> can my camera, a Canon PowerShot A60,  be set to *USB Mass Storage Mode*?
Manual here: [http://www.2shared.com/file/3104599/f0eba04e/canon_powershot_a60_manual_user_guide.html](http://www.2shared.com/file/3104599/f0eba04e/canon_powershot_a60_manual_user_guide.html)

I actually opened the PDF but every page of it has a big text saying COPY and nothing else. Something happened, I suppose, when you tried to copy this file or something like that. :(

Nevertheless, I would recommend you to access the preferences of your camera and check them thoroughly. That way, I am pretty sure, you will find if your camera offers an option to change its mode.

---

### Post by hanzj on 2008-04-06
Looking at my Camera's Settings, I don't see any option to go into *USB Mass Storage Device* mode. 

What is the "default" image importing tool for ***Xubuntu*** users?

---

### Post by kostkon on 2008-04-06
> **hanzj said:**
> Looking at my Camera's Settings, I don't see any option to go into *USB Mass Storage Device* mode. 

What is the "default" image importing tool for ***Xubuntu*** users?
You could try *gtkam* which is a small and lightweight application in the spirit of *Xubuntu*.

---

### Post by hanzj on 2008-04-06
is there a way to import photos without installing a new app/program? 
Is there a way to import photos, say, via Thunar (file manager) or via Terminal?

---

