---
title: "[SOLVED] Please help me about: &amp;amp;amp;quot;buffer I/O error on device fdo, logical bloc"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by shewenhao on 2008-03-24
Hey, guys,

I am a new fan of ubuntu. So last weekend I tried the Ubuntu by following this [http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install/]("http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install/") 
 to install the ubuntu 7.04 live CD on my 4G USB flash drive. I guess it is a good idea to have trial. And this way could help me to save the change on the USB.

I am using IBM T43 and follow the process very well but when I reboot the linux from flash drive these error pop up:


[*****.*********]Buffer I/0 error on device fd0, logical block 0
[*****.*********]Buffer I/0 error on device fd0, logical block 0
[*****.*********]Buffer I/0 error on device fd0, logical block 0
[*****.*********]Buffer I/0 error on device fd0, logical block 0
................
..........
....

([****.*********]) is the increasing number
And this error just continues, and seems like forever. in the same time, my IBM harddisk keeps running. Seems like the linux running test on the sector of linux and found something bad. But I have no idea......


Why I guess it may be caused by my IBM T43 is that I successifull installed this ubuntu live cd on my usb by using another desktop. Totally no problem. 


Thank you very much for help. Waiting for you nice reply!:popcorn::popcorn::popcorn:

---

### Post by shewenhao on 2008-03-24
Any body knows?? Thank you!

---

### Post by shewenhao on 2008-03-24
scanning my harddisk, seems no problem. How do you guys think about it?:)

---

### Post by dannyboy79 on 2008-03-24
fd0 is most always the floppy disk. do you have a floppy disk in the floppy drive that has bad sectors on it?

---

### Post by shewenhao on 2008-03-25
Hi, thank you very much for reply. I am using the IBM T43 LAPTOP and I never try to use any external floppy disk. It is really strange, right? How could ubuntu check my floppy? It is out of fashion, right..? Thank you so much. But do you have any comments to fix it? May be deleting the floppy setting somewhere in BIOS?

Waiting for your reply~:popcorn:

---

### Post by shewenhao on 2008-03-25
I disabled the floppy option in the bios. Yeah!!! It works!!! thank you dannyboy79

---

