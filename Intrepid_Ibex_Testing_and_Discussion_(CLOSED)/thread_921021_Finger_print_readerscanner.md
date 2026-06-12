---
title: "Finger print reader/scanner"
date: 2008-09-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by firstc624 on 2008-09-15
was wondering if anyone else has a fingerprint reader that you have gotten working.

I have a t61 and it has a built in scanner but i do not know how to make it work under ubuntu.

was wondering if this is something sooommmmeone has worked out, or if there is something i can to to help the comunitiy in terms of test data.

thanks

firstc624

---

### Post by avb on 2008-09-15
there is 2 project that working on making fingerprint scanners to work
[https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger)
[http://www.reactivated.net/fprint/wiki/Main_Page](http://www.reactivated.net/fprint/wiki/Main_Page)

they both provide a pam library which will allow you to pass authentification via your fingerprint scanner instead of a password.

---

### Post by ronsig on 2008-09-30
hey
i tried the Howto
[https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger)

but when i get to the testing part 

i get this
[INDENT]sudo tf-tool --acquire
[sudo] password for (username): 

ThinkFinger 0.3 ([http://thinkfinger.sourceforge.net/](http://thinkfinger.sourceforge.net/))
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>

Initializing...USB device not found.
[/INDENT]

i just dont under stand why because the fingerprint reader on my new lenovo t500 laptop ain't a usb device 

can anyone help me

---

### Post by rockin_goliath on 2008-09-30
I don't mean to burst your bubble, but why do you want it working? A fingerprint reader on a device that is covered with your fingerprints isn't any where near as secure as a good password. Although, maybe you are looking for something else with your fingerprint reader other than security.

---

### Post by taavikko on 2008-09-30
> **ronsig said:**
> hey


i just dont under stand why because the fingerprint reader on my new lenovo t500 laptop ain't a usb device 

can anyone help me

What does **lsusb** say, 
many extra devices on a laptop are connected by usb via motherboard.

---

### Post by UbuWu on 2008-09-30
Fprint packages can be obtained from debian experimental and might come handy.

---

### Post by ronsig on 2008-10-01
```
lsusb
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 014: ID 08ff:2810 AuthenTec, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

this is what i get

---

### Post by macroshaft on 2008-10-01
The entry in lsusb labelled AuthenTec is your scanner, it is a USB device.

My AuthenTec scanner can read fingerprints but it takes about 600 attempts to get a successful scan and even then another 600 successfulls to match the scan with the registered scan.

Sufficed to say the pam module is far from perfect, I gave up and disabled it in the end as it ALWAYS drops back to the password prompt, it hasn't yet actually given me access to anything by fingerprint.

---

### Post by thonuz on 2008-10-01
The Sony Vaio finger print scanner won't work I heard. I know Toshiba and Lenovo does though. For me I just like to see all my hardware in use whether its any good or not.

---

### Post by macroshaft on 2008-10-01
Point taken, I have the HP TX1000.
Wireless - sort of working (ndiswrapper)
Fingerprint reader - working after many, many headaches
Touchscreen - Working but nearly threw the laptop out the window while doing this!

Now the touchscreen has broken and they want me to prove it's a hardware fault by wiping the hard disk and restoring windows. Doesn't the fact that it stopped working in windows and linux symultaniously prove that??
Apparently not - it might be a virus or driver issue (at that point I just put the phone down)

---

### Post by ronsig on 2008-10-02
> **macroshaft said:**
> The entry in lsusb labelled AuthenTec is your scanner, it is a USB device.



I guessed that but i need to make tftool recognise the devise 
and yes i am at bit of a newbie to Linux so i might need help to some basic stuff

---

### Post by lrc3 on 2008-10-03
I remember I installed Ubuntu hardy 8.04.1 on Thinkpad T61p and it was very straight forward.


Now, I installed tf-tools/KUbuntu 8.10 beta on Thinkpad X200 but it doesn't recognize the device.

---

### Post by beercz on 2008-10-21
I have the Authentec 2501 fingerprint sensor working on my Lenovo 3000 N200 laptop running Intrepid.
 
I followed master_kernel's [how to guide]("http://ubuntuforums.org/showthread.php?t=760018").
 
Hope this helps.

---

