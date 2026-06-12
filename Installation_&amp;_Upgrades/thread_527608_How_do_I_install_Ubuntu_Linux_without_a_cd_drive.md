---
title: "How do I install Ubuntu Linux without a cd drive?"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by s3a on 2007-08-16
I have a laptop that has a dvd-rom drive that doesn't work. The floppy drive is kinda crushed as well. I have heard that you can make a network install....how would this work? Can someone guide me step by step into doing this?

Thanks!

---

### Post by Pumalite on 2007-08-16
Try this: [http://www.wrigley.me.uk/wp/?p=71](http://www.wrigley.me.uk/wp/?p=71)

---

### Post by s3a on 2007-08-16
> **Pumalite said:**
> Try this: [http://www.wrigley.me.uk/wp/?p=71](http://www.wrigley.me.uk/wp/?p=71)
I find it kind of complicating to follow...can I add you on msn for help please?

---

### Post by Pumalite on 2007-08-16
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

---

### Post by Pumalite on 2007-08-16
[http://ubuntuforums.org/archive/index.php/t-29358.html](http://ubuntuforums.org/archive/index.php/t-29358.html)

---

### Post by s3a on 2007-08-17
Pumalite, I've found a better way to do this! I have a USB (external) DVD burner! Unfortunately the BIOS doesn't detect USB on boot, however, it detects floppies on boot (the floppy drive actually works) and I can use the floppy to tell the computer to read the external dvd drive! All I need is the software to put in there that would tell it to see the USB DVD drive and I am good! So my last request would be on help in finding that specific software.

Thanks in advance!

P.S.
Thanks for the previous help anyways.

---

### Post by logos34 on 2007-08-17
> **s3a said:**
> Pumalite, I've found a better way to do this! I have a USB (external) DVD burner! Unfortunately the BIOS doesn't detect USB on boot, however, it detects floppies on boot (the floppy drive actually works) and I can use the floppy to tell the computer to read the external dvd drive! All I need is the software to put in there that would tell it to see the USB DVD drive and I am good! So my last request would be on help in finding that specific software.

If you're thinking of Smart Boot Manager floppy then I don't think it will work booting an external USB optical drive (in fact if what I've been reading today is correct then it doesn't even support booting usb hard disks). 

 If you have windows installed you ought to try the netboot approach in that link Pumalite gave you--it should work. (You don't even have to burn a cd if you use a virtual iso utility like DaemonTools or MagicISO).  

Or there's this method (requires only network connection):
[https://help.ubuntu.com/community/Installation/LocalNet?highlight=%28OS%29%7C%28install%29%7C%28network%29](https://help.ubuntu.com/community/Installation/LocalNet?highlight=%28OS%29%7C%28install%29%7C%28network%29)

---

### Post by s3a on 2007-08-17
> **logos34 said:**
> If you're thinking of Smart Boot Manager floppy then I don't think it will work booting an external USB optical drive (in fact if what I've been reading today is correct then it doesn't even support booting usb hard disks). 

 If you have windows installed you ought to try the netboot approach in that link Pumalite gave you--it should work. (You don't even have to burn a cd if you use a virtual iso utility like DaemonTools or MagicISO).  

Or there's this method (requires only network connection):
[https://help.ubuntu.com/community/Installation/LocalNet?highlight=%28OS%29%7C%28install%29%7C%28network%29](https://help.ubuntu.com/community/Installation/LocalNet?highlight=%28OS%29%7C%28install%29%7C%28network%29)
Does this link ([https://help.ubuntu.com/community/Installation/LocalNet?highlight=%28OS%29%7C%28install%29%7C%28network%29](https://help.ubuntu.com/community/Installation/LocalNet?highlight=%28OS%29%7C%28install%29%7C%28network%29))  help me if I don't have a high speed internet connection? I see the word ftp in "tftp" which would mean a LAN connection, right? If so, then good, because I have a deskop pc with a built-in ethernet card and the laptop has one as well and I also have a crossover cable. I'm just hoping for some understanding of what I am going to do before I do it.

Thanks!

---

