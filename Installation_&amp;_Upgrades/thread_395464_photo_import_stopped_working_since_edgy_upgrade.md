---
title: "photo import stopped working since edgy upgrade"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by HarmonicaGoldfish on 2007-03-28
I upgraded to Edgy this weekend and just tried to import photos from my camera for the first time since then.

With Dapper, I would just plug in my camera and it would automatically import, 

Nothing happened when I plugged in my camera, so I started gThumb and when I selected import, this is the message I received:

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

Does anyone know what I should do?

thanks!

---

### Post by NeuralEskimo on 2007-03-28
I had the same problem. I found the following link in another discussion on this forum:
[https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/91250]("https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/91250"). 
I made the suggested edit and everything worked fine.

Good luck!

---

### Post by HarmonicaGoldfish on 2007-03-29
thanks - I am going to check that out.

---

### Post by Paul41 on 2007-03-29
> **NeuralEskimo said:**
> I had the same problem. I found the following link in another discussion on this forum:
[https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/91250]("https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/91250"). 
I made the suggested edit and everything worked fine.

Good luck!

I just tried this and it worked for me.

Thanks

---

### Post by HarmonicaGoldfish on 2007-03-29
I just tried it...no luck, but I could have done something incorrectly because I am missing some basic linux knowledge :) Maybe someone here knows what I need to do?

This is what I did...

harmonicagoldfish@harmonicagoldfish:~$ /etc/udev/rules.d/45-libgphoto2.rules
bash: /etc/udev/rules.d/45-libgphoto2.rules: Permission denied
harmonicagoldfish@harmonicagoldfish:~$ sudo /etc/udev/rules.d/45-libgphoto2.rules
Password:
sudo: /etc/udev/rules.d/45-libgphoto2.rules: command not found
harmonicagoldfish@harmonicagoldfish:~$

---

### Post by Paul41 on 2007-03-29
You need to open the file in a text editor to work with it so:

```
gksudo gedit /etc/udev/rules.d/45-libgphoto2.rules
```

---

### Post by HarmonicaGoldfish on 2007-03-29
Thank you! I did that and it kind of works ;)

It is not as nice as with Dapper, though. With Dapper my camera was automatically recognized as soon as I plugged it in. Now I need to open up my photo viewer and select import. But at least I can get at my pics.

Very helpful - thank you!

Paul41, Does your computer automatically detect your camera?

---

### Post by Paul41 on 2007-03-29
> Paul41, Does your computer automatically detect your camera?

Yes, it does. It just did this by default for me so I don't know if there is a setting somewhere (probably so). You my find something by searching this forum, but I don't know for sure since I have never looked.

---

### Post by HarmonicaGoldfish on 2007-03-29
It did it by default with 6.06...

I'll search around

thanks again!

---

### Post by HarmonicaGoldfish on 2007-03-29
ok - just found something under System/Preferences/removable drives and media

Apparently it is set to import automatically (it is checked off)

This is the command attached to it...maybe it needs to be changed? 



*gnome-volume-manager-gthumb %h*


Does yours have the same command?

---

### Post by Paul41 on 2007-03-29
My command is the same and the box is checked.

---

### Post by HarmonicaGoldfish on 2007-03-29
strange. 
Wonder why it works on your machine and not mine?

En tous cas, I am happy that I can at least get the photos out of the camera.

---

