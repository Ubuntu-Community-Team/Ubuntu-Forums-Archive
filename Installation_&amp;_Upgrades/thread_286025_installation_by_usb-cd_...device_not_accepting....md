---
title: "installation by usb-cd: ...device not accepting..."
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Wayfarer on 2006-10-27
I tryed to install Ubuntu 6.10 to my Laptop but there is one problem.... My laptop doesn't have any internal CD-devices, so only way is to use external (USB) CD-device.

When I push the button Start/Install Ubuntu (or something like that.. that first button anyway...), the next message will appear:

```

/bin/sh: can't access tty; job control turned off 
(initframs) [17179601.192000] usb 4-3: device not accepting address 3, error -110 
[17179611.728000] usb 4-3: device not accepting address 4, error -110 
[17179622.264000] usb 4-3: device not accepting address 5, error -110

```


I had the same problem with Ubuntu 5.10 but this time I will solve it :D 
Ok.. It might be possible to install Ubuntu by hard disk, but before that, I want to try something else.. is there something else?

---

### Post by tchapin on 2006-12-27
I'm having the same sort of problem. Anyone have any ideas?

---

### Post by tchapin on 2006-12-27
So, when I was getting that particular error, I was trying to install 6.10. BTW, this is a Dell D400 w/ external USB CD drive.

Now, I'm attempting a 6.061 install, and it's behaving differently. I got the messages: "PCI: Failed to allocate I/O resource #7:1000@10000 for 0000:00:1e.0" and a "Buffer I/O error on device sr0, logical block 178792", but it does appear to be installing....

---

### Post by markusheinzer on 2007-01-05
seems that I had the same problem. See my thread for this:
[http://ubuntuforums.org/showthread.php?p=1940129#post1940129](http://ubuntuforums.org/showthread.php?p=1940129#post1940129)

---

### Post by John Wiersba on 2007-01-10
I got the same kind of errors, too, when installing 6.10 Edgy Eft:

[17179703 336000] buffer I/O error on device sr0, logical block 357566
[17184002 028000] buffer I/O error on device sr0, logical block 304737
[17184002 028000] buffer I/O error on device sr0, logical block 304738

I have a Dell d820 laptop with an internal  (USB??) DVD+/-RW drive.  I got the first error during the start up of the installation CD.  The next two errors I got when I was shutting down after installing.  

It appears that my installation went successfully (I am able to log in, etc), so I am only mildly worried about these errors.  But it is a wart on the installation process.  Since I just installed, I would be certainly willing to reinstall at this point.  Other than this problem and a few glitches in the gparted partitioning and the timezone setting, things went quite smoothly.  However, it appears that there are at least a few other things missing; for instance, my wi-fi wasn't detected and/or configured.

---

