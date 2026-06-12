---
title: "system lock up"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by der flyer on 2010-12-26
Have installed ubuntu on a separate partition on single hard disk and system initially worked on a dual boot basis with windows xp. However after installing most recent series of updates computer is failing to boot.

Error message is 'error : no such device : 6937cabe-f115-455b-a248-6f8d46f80682.'
prompt showing is 'grub rescue>' 

am now unable to access either windows or ubuntu.

any advice appreciated

---

### Post by noah++ on 2010-12-26
It sounds like your GRUB is booting by device ID. I'd hope it would be impossible, but it sounds like your disk's ID has changed -- or at least the way it is referenced has changed so that GRUB is confused.

At boot time, can you try **e**diting the boot commands for your Linux menu entry? If there is a **root=** argument with that long ID number, change that ID number to **/dev/sda2** or whatever /dev device is right for your system. (If you don't know, you might experiment with **sda1**, **sda3**, **hda1**, **hda2**, etc.) Then you can boot into Linux and work on making permanent corrections.

---

### Post by karthick87 on 2010-12-26
Boot from a live cd and edit the grub file, and comment out the following line by putting # in-front
```
sudo gedit /etc/default/grub
```> GRUB_DISABLE_LINUX_UUID=trueSo that it will look like,
> #GRUB_DISABLE_LINUX_UUID=trueNow update the Grub,
```
sudo update-grub
```

---

### Post by der flyer on 2010-12-27
Many thanks to all those who looked at this and especially for the response. Unfortunatley despite trying all of the options on this and other threads it was not possible to access the hard drive. I had purchased a new drive in the hope that I would be able to access the old one as a slave, it will not even let me do that so a major catastrophy. Am in the process of reinstalling everything but needless to say I will not be returning to ubuntu any time soon.

---

