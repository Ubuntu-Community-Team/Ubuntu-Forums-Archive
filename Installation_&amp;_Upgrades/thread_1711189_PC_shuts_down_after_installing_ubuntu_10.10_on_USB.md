---
title: "PC shuts down after installing ubuntu 10.10 on USB stick"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by Maurintius on 2011-03-21
Last night I installed ubuntu 10.10 on an usb stick to try it on my netbook.
I did this using my desktop PC which is running ubuntu 10.04.

Now, everytime I start my desktop with 10.04 on, it shuts down after about a minute.

I have just enough time to login but then PC shuts off. Fan is running on high speed also. Kept trying, but it keeps shutting down!

Must be some kind of conflict by installing 10.10 on Usb-stick!
Cause after 10.10 was installed on the usb-stick it asked me to restart my desktop and I did, but usb-stick was still plugged in!

Pc specifications are:

AMD Phenom II X4 955 - 3,2 GHz, cache L3 6 MB, AM3 socket  - 125 W - Black Edition (HDZ955FBGMBOX)                        

                            ASUS M4A785TD-M EVO - Moederbord - micro ATX  - 785G - Socket AM3 - UDMA133, Serial ATA-300 (RAID), eSATA - FireWire -  video 

VERITECH Value RAM 2 x 2 GB DDR3-1333 PC3-10666 PC-geheugen (DDR3/1333/2GB*2)

                            Seagate Barracuda 7200.11 - 320 Gb - 7200RPM - 16 Mb - SATA-300 (ST3320613AS) 

Can someone help me out?
I can't figure it out!

I'm not a computer specialist so I'm hoping one of you guys can help me out?

Thanks in advance.

---

### Post by Hedgehog1 on 2011-03-21
Will the desktop boot correctly if you boot of the USB stick with 10.10?  It should (as a **VERY** temporary measure).

My first reaction is your desktop may indeed have a mix of 10.04 with 10.10 updates, caused by the reboot going to your hard disk rather than you forcing back to your USB stick.

Lets start be getting a feel for what has been done to your desktop.

Please boot your desktop from the 10.10 USB stick or a 10.04 or 10.10 'LiveCD/LiveUSB'.

Then do this:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.


***The Hedge***

:KS

---

### Post by Maurintius on 2011-03-21
Thanks for the help!

I figured it out eventually.

Booted from live cd and try to unmount dev/sda1, didn't work.

Than I noticed there was something wrong with the process of my brother printer!

Bottom line is, After installing netbookversion of 10.10 on usb stick and rebooted my desktop, I tried to print a pdf!

Seemed the printer wanted to print from the usb drive and gave a conflict, cause my printer wasn't set for multiple users/servers.

Not sure this makes sense but the problem is fixed though!

Step by step, hour by hour we are learning more and more about Linux :)

Thanks for the help!

Regards

---

### Post by Hedgehog1 on 2011-03-21
So long as your are operational again, that is all that matters.

***The Hedge***

:KS

---

