---
title: "upgd breezy -&gt; dapper. now I cannot open ttyUSB0 via MINICOM"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by aj_watts@optusnet.com.au on 2006-06-05
Hi all,

I just upgrade from 5.10 to 6.06. The installation seemed to go well, however MINICOM no longer works via my USB serial port. The device is in /dev as ttyUSB0 and the permissions are crw-rw-rw- after performing the list below

I have done done the following as root.

[LIST]
[*]removed the device from /dev
[*]mknod /dev/ttyUSB0 c 188 0
[/LIST]

Prior to setting the permissions (which defaulted to crw- --- ---) the error retruned when starting MINICOM was permission denied. Simple, change the permissions on ttyUSB0. WRONG!!!!!!!!!!!!!!!!!!!!!

Now I get 

minicom: cannot open /dev/ttyUSB0: No such file or directory.

which is not correct as a directry list on /dev shows the following:

ajw@ubuntu-ajw:/dev$ ls -l ttyUSB0
crw-rw---- 1 root dialout 188, 0 2006-06-06 11:11 ttyUSB0
ajw@ubuntu-ajw:/dev$

I have attached a screen shot of the device manager. It clearly shows a serial port in USB device 3.

Anybody have any ideas](*,) ?

I need help on this one as I need a comms terminal urgently, otherwise I have to shutdonw Ubuntu, start Windows, make a single change using hyperterm and restart Ubuntu.....not good, very frustrating and damn...... it used to work :)

thanks

aj

---

### Post by ranf on 2006-06-06
Are you in the group `dialout'?
Simply run
```
groups
```

or use the graphical user manager to find out.

---

### Post by aj_watts@optusnet.com.au on 2006-06-08
I checked it and I do belng to the dialout group.

Any other thoughts???

---

### Post by aj_watts@optusnet.com.au on 2006-06-12
Resolved !!!!!!!!!!!!!!!

Here is the trick.

Under 6.06 the USB device number corresponds to the USB device number -1. (i.e USB0 = 1st USB port) Therefore if you use dev/ttyUSB0 as a comms port, then you haev to be plugged into the first USB port on your machine.

e.g. I have 4 USB port (as per device manager listing). I plugged my USB serial cable into port 1 (the lowest and first port) and minicom worked. I then plugged it into the 4th port. Minicom failed.

I then added a tty device called USB3. I plugged in th serial cable into port 4 and bingo it work. It is quite reminiscent of the old way windows used to work with comm ports.

Anyway problem resolved for me. Hope this tip helps somebofy else.

---

### Post by sankari on 2008-01-30
Hello!

I have read your post "upgd breezy -> dapper. now I cannot open ttyUSB0 via MINICOM"

and I have the same problem than you.

If I open "minicom" using ttyS0 then it works
If I open "minicom" using ttyUSB0 then I get "cannot open /dev/ttyUSB0: No such device" even if "ttyUSB0" appears in my /dev list.

Reading your post, you say that plugging your USB serial cable into one of the USB then you are able to make it works. I do not have yet any USB serial cable to connect into the USB and to test what you did, but I am wondering that if "minicom using ttyS0" works without any cable connected into the RS232 interfaz, why "minicom using ttyUSB0 does not work if there is not any cable connected".

I ask this, because I am doing an application where I need to connect two devices into the 2 serial ports, but my laptop has only one, so the second one has to be used through the USB (so I need to buy the cable to convert RS232 into USB).
Before having the cable I have tested this:
open("/dev/ttyS0",O_RDWR|O_NOCTTY|O_NDELAY|O_NONBLOCK); //works
open("/dev/ttyUSB0",O_RDWR|O_NOCTTY|O_NDELAY|O_NONBLOCK); //receiving "open error 2 no such file or directory"

So after that I tried minicom resulting the above of the post.

So my question is: "ttyUSB0" can be only opened when there is something connected on it?
(because with ttyS0 you can open even if there is nothing connected on it)

Thank you in advance.

---

