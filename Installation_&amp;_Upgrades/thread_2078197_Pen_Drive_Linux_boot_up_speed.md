---
title: "Pen Drive Linux boot up speed"
date: 2012-10-30
forum: Installation &amp; Upgrades
---

### Post by agvictor on 2012-10-30
Hello everyone. I have been tasked to create a USB boot stick that will launch Ubuntu and run a script to contact a server. No big deal, I downloaded Ubuntu 12.4, created my usb thumb drive with 12.4 and put the script in the start up manager. So far everything is great with an average boot time of 1m15s however I would like to decrease the time it takes to boot. I have looked at remastersys and uck but I can't get those to work with the pen drive software. I believe this may be because it is all loaded into memory. 
 
Is there a way to increase the boot? If so how? Any help would be great and thanks in advance.

---

### Post by funicorn on 2012-10-30
How do you create the usb live system ?
What is the type of  root filesystem created onto the usb partition ?
What is the type of partition filesystem on the usb drive ?

---

### Post by agvictor on 2012-10-31
> **funicorn said:**
> How do you create the usb live system ?
What is the type of  root filesystem created onto the usb partition ?
What is the type of partition filesystem on the usb drive ?

Hello and thank you for the reply. I was able to get it to work this morning and what I did was use the boot up manager to strip out some start up features which reduced the start up time by half. I now have a bootable usb stick running Ubuntu 12.4 which boots in 30 seconds and runs a python script. 

To answer your questions I used Universal USB Pen Drive with Ubuntu 12.4 on a fat32 partition with 16 gigs of space.

Thanks for the reply!

---

### Post by oldfred on 2012-11-01
I have a full install of Ubuntu in a 8GB partition on my 16GB flash and it boots in about 40sec without any real optimization.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

If using the installer version with persistence, you only need a 2 or 4GB flash drive.

And you can remove install option.
Without install option.
[http://askubuntu.com/questions/47522/how-to-bypass-try-it-install-screen-when-booting-from-usb-live-session-wit?rq=1](http://askubuntu.com/questions/47522/how-to-bypass-try-it-install-screen-when-booting-from-usb-live-session-wit?rq=1)

But you could do a full install of the minimal version which is just a kernel and network connections to let you install only those applications you need. 

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
HowTo Achieve "Ubuntu-Desktop-Minimal" 
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)
Install script for minimal
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

---

