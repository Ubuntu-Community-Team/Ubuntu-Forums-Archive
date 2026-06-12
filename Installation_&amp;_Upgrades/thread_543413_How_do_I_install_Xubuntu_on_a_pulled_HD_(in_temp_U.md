---
title: "How do I install Xubuntu on a pulled HD (in temp USB enclosure)?"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by malangbaba on 2007-09-05
Trying to install Xubuntu on a HD taken from a Compaq Armada M300 (PIII-500Mhz-320MB)

The M300 doesnt have a CD or floppy (and i cant do net boot). I also cannot boot off of USB, but I WONDER IF I CAN INSTALL FROM USB FLASH DRIVE IF I AM BOOTED INTO PUPPY?

So I took out the HD, put it in a USB enclosure. I was able to install Puppy this way (since it doesnt install drivers). But Xubuntu adds drivers in installation, which gives me problems when I move the HD back to the laptop....

Is there a way to do a base install? or other suggestions to get around this?

---

### Post by K.Mandla on 2007-09-05
This is kind of a weird idea, but it's the first thing that came to mind.

[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

If you can chroot into the USB drive, you should be able to install just about anything you like.

You could also look into installing from an ISO, which might give you some more options.

[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)

Search around; there are lots of options available to you. ;)

---

