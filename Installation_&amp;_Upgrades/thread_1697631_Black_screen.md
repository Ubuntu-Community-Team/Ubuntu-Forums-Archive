---
title: "Black screen"
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by raptor9 on 2011-03-01
Hi guys i need some help i donwloaded ubuntu 10.10 and used the option to install it in windows, the install ran smoothly and asked to reboot the pc, here is were the problem is on startup i get asked Windows 7 or ubuntu, if choose ubuntu i get another 3 options ubuntu, ubuntu safe mode or windows7, if i choose either of the ubuntu options i only get a blank screen. I tried uninstalling and installing again but same problem.

---

### Post by runeh76 on 2011-03-01
Hi

Dont worry, Lets see ur partitions info:

Boot info script:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by sikander3786 on 2011-03-01
Welcome to the forums :-)

I think putting in the nomodeset parameter will help.

> From your Bios screen, press and hold down Shift key until you see the Grub menu. Highlighting the first entry there, press 'e' to edit it. Using arrow keys, navigate to words "quiet splash", delete them and type "nomodeset" in their place (without quotes). Press Ctrl + X to continue boot. Hopefully, you'll see the desktop this time.

Once on the desktop, make sure you are connected to the Internet. Now go to System > Administration > Hardware Drivers (Lucid) or Additional Drivers (Maverick) and check if any proprietary drivers are available for your graphics card. If there are any, activate the current/recommended one's and the problem should go away forever.

As you can see the Grub menu automatically, you don't need to press the <Shift> key while booting.

Source: [http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

Let us know how that goes :-)

---

### Post by raptor9 on 2011-03-01
thanks for the info sofar ill report back whein i get back to the pc

---

### Post by raptor9 on 2011-03-02
> **sikander3786 said:**
> Welcome to the forums :-)
 
I think putting in the nomodeset parameter will help.
 
 
 
As you can see the Grub menu automatically, you don't need to press the <Shift> key while booting.
 
Source: [http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)
 
Let us know how that goes :-)
 
Update report, i entered nomodeset and could enter ubuntu, i then istalled the driver for nvidia and restarted, now i get the following, it goes to were i select user and enter my password and then freeze with only a background picture.

---

### Post by sikander3786 on 2011-03-02
Please post your hardware specs including RAM and processor.

---

