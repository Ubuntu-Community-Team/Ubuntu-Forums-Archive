---
title: "b43 legacy firmware version 3"
date: 2011-12-01
forum: Installation &amp; Upgrades
---

### Post by hwally on 2011-12-01
While downloading ubuntu to an old hp laptop I got the message that firmware file "b43 legacy/uncode4.fw not found.  It told me to go to a website and download version 3.  I went there and realized I'm in way over my head.  I have no idea how to install or download the drivers.  It's a very complicated process.  I was hoping to bring the old computer back to life.  Should I be looking for a different o.s. more suited to noobs?  The list ended with the phrase:Asking all remaining processes to terminate. atcher checking for running unattended upgrades: stopping bluet [ok].  I'm willing to study and try.  Thank you

---

### Post by vangop on 2011-12-02
Hi!
The solution is very simple. Depending if you have access to the internet.
For your card there's 2 kinds of wifi drivers, Broadcomm's STA and open source b43.
This is a [detailed guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") on this.
The STA is easy to install, I suggest you use it. If you open additional drivers applet (you'll find it in the main menu) or run ```
jockey-gtk 
``` in the terminal. You'll have a list of available drivers, and STA should be there. Just select it and click enable.

---

### Post by lkraemer on 2011-12-02
hwally,
Most of the solutions assume that you have a Ethernet connection to get:
1.  Distro Updates - first
2.  Enable Hardware Drivers - second
3.  Download the firmware - third
4.  Then your Wifi can be enabled via Software or Hardware Switch and then used.

You obviously have some type of access, since you are posting, but you might not be able to get the older HP Laptop connected via Ethernet.  You 
can always copy the Firmware to it's destination and then try to enable the Wifi.

There are a couple of Forum Postings explaining how to do this.

[http://ubuntuforums.org/showthread.php?t=1470146&highlight=Firmware+Broadcom](http://ubuntuforums.org/showthread.php?t=1470146&highlight=Firmware+Broadcom)

Start with:  **How do I know if I have Broadcom Hardware?**


IGNORE the NDISWRAPPER Section, and don't pay any attention to the B43
or STA Driver, as your Distro version already has a defualt.  Just start at **#2 Use DEFAULT XXX Driver in 10.04** for whatever Version of Ubuntu you are using.

If you have tried to install ndiswrapper or used some other guide we may need to help you revert back to what your system was before you did any changes.  We may need the terminal commands you used or the guide's url.

Post back after you have copied the Firmware to it's proper location, or if you need more help.

LK

---

### Post by hwally on 2011-12-02
Thank you for the very patient and polite replies.  I have another,related, question.  I have a d-link wireless usb adapter.  I'll be using it permanently because I'm unable to pick up wifi without it.  I have access to the internet through another computer and can download to a cd and transfer any data that way. This computer will be in the same place permanently also.  Is there a way to bypass the internal wifi card and just set up ubuntu to always access the usb wifi.  Thanks again.

---

### Post by lkraemer on 2011-12-02
I'd suggest you first try the Broadcom Wifi in the Laptop.
You will have it working in short order.  Just start with the
How do I know if I have Broadcom Hardware, and post if you have questions.

Then download the Firmware, copy it to the Laptop by USB Flash Drive,
or burn it to a CDR, then copy it to where it will reside.  Those
instructions are at Use DEFAULT XXX Driver in 10.04.

Post if you have trouble or questions.

Last resort will be to use the USB Wifi Adapter.


Larry

---

