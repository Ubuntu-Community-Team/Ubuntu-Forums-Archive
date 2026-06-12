---
title: "Scan on 14.04"
date: 2014-08-13
forum: Installation &amp; Upgrades
---

### Post by JLUbunt on 2014-08-13
Hello
I am using a Brother Printer Scanner MFC-9120CN on Ubuntu 12.04 it is connectect via the network using a static IP address. It works well with scan2pdf and simple scan. I have installed 14.04 on another computer typed in the IP address in the Printer place and the printer workes well but neither simple scan or scan2pdf can find the scanner using 14.04. I've seen in the software manager reviews of scan2pdf that it stops working after upgrading from 12.04.  
I plan to upgrade when I can have the capacity to scan.  It could be that I need to type in the IP address specifically for the scanner part of 14.04. I do not know how. Or are there other scanning utilities I could try? Any ideas would be appreciated. ;)

---

### Post by plucky on 2014-08-15
> **JLUbunt said:**
> Hello
I am using a Brother Printer Scanner MFC-9120CN on Ubuntu 12.04 it is connectect via the network using a static IP address. It works well with scan2pdf and simple scan. I have installed 14.04 on another computer typed in the IP address in the Printer place and the printer workes well but neither simple scan or scan2pdf can find the scanner using 14.04. I've seen in the software manager reviews of scan2pdf that it stops working after upgrading from 12.04.  
I plan to upgrade when I can have the capacity to scan.  It could be that I need to type in the IP address specifically for the scanner part of 14.04. I do not know how. Or are there other scanning utilities I could try? Any ideas would be appreciated. ;)

[Brother Website:Scanner Driver Install for Network](http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&redirect=on)

Have you installed the driver?

---

### Post by JLUbunt on 2014-08-16
Hello Plucky

You guesed right I had not installed the scanner driver.  Have now and it all works.  Thanks.  For those, like me, who are not tech minded and are not particularly confident with using the terminal. There are 2 files to install from the Brother page brscan and scan=-key-tool. After accepting the agreement you can install them by clicking on install from the window it opens in. That is what I did and it worked. Adding the Network information was a bit more fiddly for me. It has a good example see below but because of my limited termial skills took me a few goes.  Looking at the example below.  I'm not sure why I had so much trouble. Maybe I should have saved it, in a wordprocessor, with the details of my scanner and cut and pasted it back into the terminal. 
$ brsaneconfig2 -a name=SCANNER model=DCP-540CN ip=192.168.3.3

---

### Post by JLUbunt on 2014-08-16
Hello
it all worked on the new installation of lubuntu as above.  I then upgraded my main computer Ubuntu 12.04 to 14.04 it lost the scanner as I've seen in other Threads.  I tried the same process as getting it to work with Lubuntu. Have not yet been successful. My other computer is a 32 bit AMD. My main computer is an intel 64bit.  The error messages seem to be that the dirver is the Wrong architecture,  I'm pleased that I can scan on one.  thanks

---

### Post by plucky on 2014-08-17
> **JLUbunt said:**
> Hello
it all worked on the new installation of lubuntu as above.  I then upgraded my main computer Ubuntu 12.04 to 14.04 it lost the scanner as I've seen in other Threads.  I tried the same process as getting it to work with Lubuntu. Have not yet been successful. My other computer is a 32 bit AMD. My main computer is an intel 64bit.  The error messages seem to be that the dirver is the Wrong architecture,  I'm pleased that I can scan on one.  thanks

There are 32-bit and 64-bit drivers on the Brother website.Download and install the appropiate .deb driver for your system.

---

