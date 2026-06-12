---
title: "Camera Problems after Normal Upgrades"
date: 2007-03-11
forum: Installation &amp; Upgrades
---

### Post by myke on 2007-03-11
What a shame. I went thru the normal package upgrade process today that was recommended under the adept updater and now my camera won't work again. And I know it was something in the upgrade as I used it just yesterday and uploaded some photos just fine. Now ... it recognizes my camera, a Kodak Easyshare CD33 but under gthumb I get the following error when trying to import photos (though it does show my camera model as recognized):

An error occurred in the io-library ('Bad parameters'): Could not find USB device (vendor 0x40a, product 0x59c). Make sure this device is connected to the computer.

That's what I get with gThumb thought my Kodak is listed right above the error.

With DigiKam, it just says:

Failed to connect to camera. Please make sure its connected properly and turned on. Would you like to try again?

The camera is on and detected by my system but no ability to import.

This sux. It seems that every other time I do the recommended package upgrades, something breaks on my system.

Also of note ... the  solution I tried before [from this thread]("http://www.ubuntuforums.org/showthread.php?t=346840&highlight=mount+kodak+camera"), I tried again but to no avail this time. My camera is actually still correctly identified on rules file that I updated successfully on the previous problem. I went thru the steps again just in case ... but nothing. I need help.

---

### Post by myke on 2007-03-11
Going back to the same thread I linked to up above in my original post, some one came in and posted another solution which worked.    Apparantly there's a posted bug on this very thing.  

Basically what worked is this:

[I]FWIW, I got the "Could not claim the USB device..." import error last night, though my Canon S3 IS had always worked fine, right up to the latest update. Adding a line with the device IDs from lsusb didn't do anything because the line was already there. I came across the bug report linked below and tried changing BUS!="usb*" to SUBSYSTEM!="usb_device" in my 45-libgphoto2.rules. Restarted udev and now it works again.

[https://launchpad.net/ubuntu/+source...to2/+bug/91250](https://launchpad.net/ubuntu/+source...to2/+bug/91250)[/I]

The working solution is thanks to [FM1]("http://www.ubuntuforums.org/member.php?u=27002").

---

### Post by peterx14 on 2007-03-12
I just had the same problem with my Kodak C330 and the same fix worked perfectly! :)

A bit disappointing it happened though. Are all other Ubuntu Camera owners expected to find the fix here or will an update patch be rolled out?

---

### Post by Falcorian on 2007-03-18
Same problem with the recent update and my Casio EX-Z750, and the same solution fixed it! Thanks! :)

---

### Post by jcconnor on 2007-03-18
Thank you thank you thank you

---

