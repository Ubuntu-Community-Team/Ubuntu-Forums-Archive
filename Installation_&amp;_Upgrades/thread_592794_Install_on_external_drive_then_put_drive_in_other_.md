---
title: "Install on external drive then put drive in other laptop"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by miloskorac on 2007-10-26
Hello,

Is it possible to install Ubuntu on external usb hard drive, and then to put that drive into laptop?

Laptop does not have CD or floppy.
Do you know any other methods how to deploy Ubuntu on drive (empty one) and to be bootable, so when computer starts, installation of Ubuntu can start (from the hard drive)?

Thank you,

Milos Korac

---

### Post by ddrichardson on 2007-10-27
Yes, providing the hardware is similar. You may have to mess around getting X working, but it shouldn't take much more than```

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```from a virtual terminal.

---

### Post by miloskorac on 2007-11-09
I dont understand you??

What terminal?

Your answer is confusing...

---

### Post by miloskorac on 2007-11-09
What files should I put on empty external usb drive, so that booting that drive I can install ubuntu over it, from a folder on that drive. (no cd, no floppy) . 

Can you make a list of files, and installer, and necessary steps for installing a ubuntu.

---

### Post by bulldog on 2007-11-09
When you have installed and switch the hdd into the laptop,boot in recovery mode.
This will bring you to a console where you have to login.
Now perform the ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Answer the questions you get and if done reboot.
This will configure the xorg.conf file to the new specs.
 with a little luck you can boot now.

---

### Post by miloskorac on 2007-11-24
What files should I put on empty external usb drive, so that booting that drive I can install ubuntu over it, from a folder on that drive. (no cd, no floppy) .

Can you make a list of files, and installer, and necessary steps for installing a ubuntu.

Can you please give a proper answer, and not writing some codes that I have to execute on installed ubuntu.

Read:

Empty drive (blank)

External USB

No Cd

No Floppy

Connected on Windows XP laptop


Thank you

---

### Post by felin on 2007-11-24
> **miloskorac said:**
> 
Can you please give a proper answer, and not writing some codes that I have to execute on installed ubuntu.
I believe Bulldog and ddrichardson are trying to help you. They have taken time to read your post and respond to it. They are referring to the use of a terminal: [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

---

### Post by Pumalite on 2007-11-24
You can try a 'vanilla' xorg.conf file in your external. With Generic Monitor,all the regular defaults and 'vesa' as the driver.
Your chances then increase that the external will just boot.

---

