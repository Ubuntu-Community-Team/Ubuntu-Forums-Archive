---
title: "Ubuntu installation error"
date: 2013-09-12
forum: Installation &amp; Upgrades
---

### Post by rami5 on 2013-09-12
Hi ( Im new )
I kinda fixed up an old Laptop ( Toshiba Satellite L300 23K ), and desided to install Ubuntu on it for a change ( no previous experience with Linux whatsoever )

Im having troubble with the installation process
Note that the Laptop's OS ( Windows ) is damaged, and can not start

#1
I downloaded Ubuntu ( version 12 sumthin', 64bit )

#2
I burnt the iOS file to a CD-R ( using windows 7 )

#3
I inserted the CD into the Laptop, and booted from CD-drive

#4
Here is where the problem comes...

Im presented with a Terminal/ DOS screen which eventually displays some text/ error message
[IMG]https://dl.dropboxusercontent.com/u/3537859/004.JPG[/IMG]

Pressing any keyboard button writes a bunch of text and end us at this error:
[IMG]https://dl.dropboxusercontent.com/u/3537859/005.JPG[/IMG]

...
This is the 3rd time i tried the CD boot.
The very first time i got an I/O error instead of the above
( The ubuntu screen "UBUNTO + ....." evry other time i hit the keyboard )

...
What am i doing wrong?
How can i install Ubuntu?

---

### Post by VMC on 2013-09-12
Are your sure the hard drive is ok? Since Windows is damaged, try re-formatting. Looks like its havine issues with the partitions.

---

### Post by rami5 on 2013-09-12
I dono, the Hardrive is there but if its the physical Hardware or the Windows Software which is the root cause i cant say.

I was hoping maybe someone around here would recognize the error output, so that the problem cound be isolated somewhat

...
I have 2 options when starting the laptop
#1 Setup Utility
#2 Boot Menu

Im currently viewing the Setup Utility, but cant see any options for Formating any where
However, it says
"Hard Disk Drive: None"

I guess this is it :P

---

### Post by VMC on 2013-09-12
Those 'udev blkid' are pointing to bad or can't read partitions. 
What are you using now? If you have a livecd you can use the Disk Utility (*palimpsest* from a terminal) command to format the hard drive.
So its Dash home then type disk and it should appear.

---

### Post by rami5 on 2013-10-03
:D
I have aquired a new 1TB SSHD hardisk and installed it, yay!
So the CD worked now, and i have the option to (A) try or (B) install ubuntu

When installing i get the option to install some 3rd party software stuff ( related to Flash MP3 stuff )
Im not a big fan of installing all and any thing i dono what is.

Is the something i should install or should i skipp it?
Can i choose to install it at a later time?
And why has my Usernam changed? ( Here on the forum )

---

### Post by rami5 on 2013-10-03
Also, installation complete before i could read al the introduction slides.
Can i read them again somewhere?

---

### Post by Bucky Ball on 2013-10-03
Welcome. For the forum name change, post in ***Forum Feedback & Help*** and one of the admins will fix you up.

Yes, you can install third-party drivers (if required) and software whenever you like.

The slides don't say much you can't find out by researching or asking here (if you're talking about the slides that show while you are waiting for Ubuntu to install). ;) 

There might be a site somewhere that gives you the screenshots, not sure. 

Enjoy the OS, the forums and the learning curve. Good luck.

PS: Not the slides, but plenty of info nonetheless:

[https://duckduckgo.com/?q=intro+slides+ubuntu+install](https://duckduckgo.com/?q=intro+slides+ubuntu+install)

---

