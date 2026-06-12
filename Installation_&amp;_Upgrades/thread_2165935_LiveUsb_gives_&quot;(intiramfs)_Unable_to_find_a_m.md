---
title: "LiveUsb gives &quot;(intiramfs) Unable to find a medium containing a live file system&quot;"
date: 2013-08-07
forum: Installation &amp; Upgrades
---

### Post by Tom 6 on 2013-08-07
Hi :)  
In a LiveUsb session (with persistence) i updated using 
sudo apt-get upgrade
but it seemed to get stuck doing the "linux headers".  The whole system froze-up.  Prolly because i had too many things open a the same time.  I couldn't even get a command-line to open to allow me to run 
sudo reboot 
or anything.  

So, i had to force the notepad to shut-down by holding the on/off button.  

Now the LiveUsb-stick wont boot-up and gets stuck on a command-line saying 

"
BusyBox v1.20.2 (Ubuntu 1:1.20.0-8ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.  

(intiramfs) Unable to find a medium containing a live file system
"

Is there any easy way to get the Usb-stick working again or will i get need to start from scratch again?  
Regards from 
Tom :)

---

### Post by Tom 6 on 2013-08-07
Hi :)
Ooops, my first post was very confused.  I doubt this will improve matters much!  The LiveUsb was using Ubuntu 13.04, 64bit but i doubt it makes much difference if it was something completely different.  

I have a 2nd 8Gb Usb-stick so i am wondering if i could make that a LiveUsb and then just copy&paste the initramfs from the new one onto the older one?  Is that likely to blow-up my machine or create problems?

Regards from 
Tom :)

---

### Post by Tom 6 on 2013-08-07
Hi :)
Ooops, my first post was very confused.  I doubt this will improve matters much!  The LiveUsb was using Ubuntu 13.04, 64bit but i doubt it makes much difference if it was something completely different.  

I have a 2nd 8Gb Usb-stick so i am wondering if i could make that a LiveUsb and then just copy&paste the initramfs from the new one onto the older one?  Is that likely to blow-up my machine or create problems?

Regards from 
Tom :)

---

### Post by Tom 6 on 2013-08-07
Hi :)
WOW!! That was unbelievable!  I made a LiveUsb from another Usb-stick that was only a tiny bit smaller than the one causing me troubles.  

Then i dug through the folders and found the init file and dragged that onto the broken Usb-stick.  

Ta'dahhh, as if by magic the broken Usb-stick started working! :)
Regards from
Tom :)

---

