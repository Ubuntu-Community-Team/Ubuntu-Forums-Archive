---
title: "Mouse problem in Ubuntu 5.04"
date: 2005-08-23
forum: Installation &amp; Upgrades
---

### Post by ismxray on 2005-08-23
I installed the Ubuntu 5.04. In the LiveCD mode, I can use both serial Mouse and USB mouse, but after I installed to disk, the serial cannot be used any more.

I also have a USB wireless mouse, which cannot be used either in the LiveCD mode or after installed in hard disk. Should one mannully insert the module to make it work?

---

### Post by glug101 on 2005-08-23
If the module is not loaded, the mouse will not work.  Give it a shot!  Hey, it won't break anything :)  If that is the solution you can add the module to>  /etc/modules

Have fun!

---

### Post by ismxray on 2005-08-23
The problem is that I don't know which module I should include.
In the /etc/modules there already have "mousedev" and "psmouse".
Which modules is for the serial mouse and which is for the USB wireless mouse? Thanks!

---

### Post by glug101 on 2005-08-25
Grrr.... The easy answer never works anymore!!

Ok, this sounds like you may need to edit your xorg.conf file.  (going on memory here, but I believe it's in /etc/X11/xorg.conf)  There are setup programs that can make this easier (xorgsetup?), however it might come down to a manual config of the xorg.conf file.  The serial mouse shouldn't need any special kernel drivers (sorry I didn't catch that on my earlier post) and the usb one should have the drivers installed by default. (hid and usbcore are the only ones that come to mind right now)  It's been awhile since I've worked with serial devices on linux, but I believe that the serial ports live in /dev/tty*.  That is where x should be looking for a serial mouse.

I'll try to look up the specifics, but be advised that this will be well into next week since my wife and are going away this weekend and we are also looking for a place to live at the end of september. (no offense meant, but Ubuntu forums takes a backseat to those two items ;) )

Take care!

---

### Post by glug101 on 2005-08-25
I stand corrected, perhaps you do need a kernel driver for a serial mouse.

[http://www.ubuntuforums.org/showthread.php?t=59808](http://www.ubuntuforums.org/showthread.php?t=59808)

(never heard of sermouse before.......)

---

### Post by i_netguru on 2005-09-01
Leave 2 mice, I am not able to use my serial mouse properly. After setting the xserver settings, my mouse is identified but not working properly.
What the hell is this? Any clear cut answer for the problem please?

Now I have a new problem. I have been trying several solutions told on the forum and finally my mouse worked for sometime. Now after rebooting, it again started gving problem. This time it says Xserver settings not recognised.
Oh! Any takers for this to solve?

---

### Post by Maier on 2005-09-02
Try posting your xorg.conf in here, i think the "Guru's" will have a better chance to se if something is wrong :)

---

### Post by i_netguru on 2005-09-03
[QUOTE=Maier]Try posting your xorg.conf in here, i think the "Guru's" will have a better chance to se if something is wrong :)[/QUOTE]

Certainly. Gurus 2 are students of life. I could restore the Xserver settings. But now mouse behaves eratically. By the way is there any way out to copy the conf file onto a floppy or memory stick? My FDD is not recognised.

I dont have a net connectivity on that machine.

OH!
 ](*,)

---

### Post by Maier on 2005-09-03
Allthough im still a huge rookie regarding the opens source world.. 

I would advice you to mount your floppy, and then cp your xorg onto the disk.

mount /mnt/floppy/

cp /etc/X11/xorg.conf /mnt/floppy

perhaps with some adjustment here and there, m not that familiar with those darn commands yet :)

GL

---

### Post by i_netguru on 2005-09-05
Hi
the floppy fails to respond. But one good news. When I changed the mouse type to Microsoft(though it is a Logitech mouse) and opted for no 3rd wheel, it started working.

The floppy drive is still not working and mp3 is not playing. It says plugins not loaded. What plugins & from where - not known.

Further R&D is on.
thanks. :grin:

---

### Post by Maier on 2005-09-05
Well your mp3 problem should be able to get fixed pretty easy, if you just follow the ubuntuguide :)

---

