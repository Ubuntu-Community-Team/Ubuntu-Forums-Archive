---
title: "Digital camera Stopped working after upgrade from 6.10 to 7.04"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by Buddha_Joe on 2007-04-30
I have a Canon PowerShot A530 which worked fine under 6.10 but since I have upgraded I get the following error when I try to use it with 7.04 

```

An error occurred in the io-library ('Bad parameters'): 
Could not find USB device (vendor 0x4a9, product 0x3126).
 Make sure this device is connected to the computer.

```

I have searched this forum and all I can seem to find are older posts referring to an error that related to the permissions on the mounted device.

I followed the suggestions in the posts just to see what would happen and edited 45-libgphoto2.rules but I sitll receive the same error. I have since restored the rules file to it's original state. 

I also searched the rules file to see if my camera was listed but I did not find it so I tried adding it but still had no luck so I commented it out. I am really at a loss here. 

I even went so far as to replace my sd card in my camera and I am still having the same problem.

---

### Post by Buddha_Joe on 2007-05-01
bump.

---

### Post by terrellf on 2007-05-01
I have the exact same problem.

Editing the 45-libgphoto2.rules (usb* to usb_device) did NOT work for me either.  

I have an Olympus C3000Z but I bet all usb cameras with special drivers are broken now.  

Have to keep looking and hope somebody figures it out sooner rather than later.

Terry

---

### Post by Buddha_Joe on 2007-05-03
I finally got it to work. I had to delete several pictures from my camera (I have a 2GB SD card and an obscene number of images on it). Once I did that it started downloading again. The number of images was causing gphoto2 to choke using the PTP protocol..

---

### Post by netmackan on 2007-06-24
Did you do something else than just removing images?

I have an Olympus C-3000Z and get an error:

> 
An error occurred in the io-library ('Error updating the port settings'): Could not release interface 0 (Invalid argument)


I only have one photo in the camera. Also when there is no photo there is no error message. 

Do I have to edit the .rules-file? Anyone know how?

---

