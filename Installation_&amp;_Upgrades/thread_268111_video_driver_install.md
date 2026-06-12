---
title: "video driver install"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by linuxnoob40 on 2006-09-29
i know this has been covered a billion times. howvere im not doing something right .
i have downloaded the video driver i want to install and opened a terminal and typed sudo aptitude install (driver name here )  but it just reports back that it cant find a file by that name. as ill paste and demonstrate

 sudo aptitude install NVIDIA-FreeBSD-x86-1.0-8774.tar.gz
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "NVIDIA-FreeBSD-x86-1.0-8774.tar.gz"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

what am i doing wrong here??

---

### Post by _teo_ on 2006-09-29
> **linuxnoob40 said:**
> 
 sudo aptitude install NVIDIA-FreeBSD-x86-1.0-8774.tar.gz


Why FreeBSD? You maybe need NVIDIA-Linux-x86-1.0-8774-pkg1.run from [http://www.nvidia.com/object/linux_display_ia32_1.0-8774.html](http://www.nvidia.com/object/linux_display_ia32_1.0-8774.html)

---

### Post by pseudonym on 2006-09-29
Hi,

For a start, you've downloaded the wrong driver. What you have is for Free BSD, a completely different operating system.

what you really should be doing is following the ubuntu howto [here]("https://help.ubuntu.com/community/Latest_Nvidia_Dapper"). Its very comprehensive and user friendly.

---

### Post by linuxnoob40 on 2006-09-29
first of all i wanted the most recent driver not the august driver.  second the only driver for amd is the 64 bit one,  im  using 64 bit processer but 32 bit ubuntu ( the 64 bit ubuntu wouldnt install right ) now isnt IA for intel processer or wil it work for amd as well??

---

### Post by pseudonym on 2006-09-29
Don't worry that it says in that howto its only for drivers 8756 and 8762. It will work with the current driver 8774. IA32 is for any 32-bit linux operating system, it doesn't matter which processor. I'm using it on my AMD 32-bit system. Because you've installed Ubuntu 32-bit, you should get the IA32 driver from nvidia.

HTH

---

### Post by linuxnoob40 on 2006-09-29
ok have downloded the IA 32 bit driver now i get an error (could not open the file etc etc etc)

---

### Post by _teo_ on 2006-09-30
> **linuxnoob40 said:**
> ok have downloded the IA 32 bit driver now i get an error (could not open the file etc etc etc)

Did you follow the [Latest Nvidia Dapper]("https://help.ubuntu.com/community/Latest_Nvidia_Dapper") guide?

---

### Post by linuxnoob40 on 2006-09-30
i went through the guide and have done what it says but i dont see a change in anything and the file i downloaded still says the same error. does ubuntu update the driver automatically with the newest available? there are so many things that i still just dont get about linux...

---

### Post by _teo_ on 2006-10-01
> **linuxnoob40 said:**
> i went through the guide and have done what it says but i dont see a change in anything and the file i downloaded still says the same error.
Which method did you follow? I do follow method 2 (a modified version). Also at which point does it say that the file is missing? Try to be more descriptive please.

One way to prove the driver is there is to look at your Applications menu for System Tools submenu. Under it you will find NVIDIA X Server Settings item. Other way is: while booting at some point just before the login screen is shown a white page will be shown for a while with NVidia logo on it.

> **linuxnoob40 said:**
> does ubuntu update the driver automatically with the newest available?
No. I do this manually for my video card.

> **linuxnoob40 said:**
> there are so many things that i still just dont get about linux...
Don't give up!

---

