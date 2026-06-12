---
title: "Upgrading from x86 to x64"
date: 2011-12-14
forum: Installation &amp; Upgrades
---

### Post by PoLoMoTo on 2011-12-14
I have accidentally installed x86 Ubuntu 11.10 on my x64 system.  I want to change to x64 and I also want to downgrade to 11.04 because from what I hear it is less glichy.  Can anyone tell me how to either uninstall 11.10 or upgrade?  Note: I also have windows on the same computer and would like to be able to use both.

---

### Post by garvinrick4 on 2011-12-14
> **PoLoMoTo said:**
> I have accidentally installed x86 Ubuntu 11.10 on my x64 system.  I want to change to x64 and I also want to downgrade to 11.04 because from what I hear it is less glichy.  Can anyone tell me how to either uninstall 11.10 or upgrade?  Note: I also have windows on the same computer and would like to be able to use both.
Download a .iso file of 64 bit Ubuntu in version you want and burn a disk and install in same partition as the 32 bit installation you have now will overwrite it no need to uninstall.
[http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)

---

### Post by garvinrick4 on 2011-12-14
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Read show me hows above:
use the "something else" to install:
Choose your partition you have Ubuntu linux in to install:
choose ext4
choose format
choose to install at /

Grub always installs in sda not sda1 or sda5 just sda (if have one drive installed)

If you need to Find your sda# in terminal:
```
sudo fdisk -l 
```(lower case L)
Now choose your linux partition to use to install in:

---

### Post by PoLoMoTo on 2011-12-14
And ill still be able to use windows right?

---

### Post by Dlambert on 2011-12-14
Any piece of software will have bugs when it's released, but to go as far to say 11.04 is "less buggy" I don't think so. Software wise you cannot compare the two, Gnome2 to 3 for example.

---

### Post by PoLoMoTo on 2011-12-14
Well i also used the two on a flash drive and i like 11.04 better, plus I've had a lot of problems with 11.10 and didn't notice them in 11.04

---

### Post by garvinrick4 on 2011-12-14
> **PoLoMoTo said:**
> Well i also used the two on a flash drive and i like 11.04 better, plus I've had a lot of problems with 11.10 and didn't notice them in 11.04
Use what you are comfortable with and yes you can run linux and windows on same drive
matter of fact you can run just about as many linux installs as you can partition your drive.
(each partition has a operating system or used as a /home or data partition if desired.)
Google partitioning for basic drive will give you lots of results to read.
Open a terminal in linux:
```
sudo fdisk -l 
```(lower case L)
Now you can see sda# for windows and linux installs. Need help just post results.

---

### Post by PoLoMoTo on 2011-12-14
I was just making sure because I noticed since i have Linux on a different drive than windows now i cannot boot directly from the windows drive so I was just making sure I could still get it when Linux boots, thanks

---

### Post by PoLoMoTo on 2011-12-14
Which option should I choose to overwrite the old ubuntu but NOT windows?

---

### Post by critin on 2011-12-15
> 
Which option should I choose to overwrite the old ubuntu but NOT windows?Post number 3 answers this question.
> 
 i have Linux on a different drive than windows

Just be careful to choose sdb if that is where ubuntu is.

---

### Post by PoLoMoTo on 2011-12-15
Yea thanks but now when I boot the computer I get "error: no such device: (really long number (MAC address?))"  "grub rescue>"  I think I just need to change the boot drive but not sure.

---

### Post by garvinrick4 on 2011-12-15
Put your CD in and use Try Ubuntu and when it boots up open a terminal.
```
sudo fdisk -l
``` (lower case L)
Then post that output of that to this thread for me.

---

### Post by PoLoMoTo on 2011-12-15
No I just re installed, before I set the device for boot installation to my second drive so when the computer booted there was nothing to boot.  Now all is well :) thanks anyway

---

### Post by garvinrick4 on 2011-12-15
> **PoLoMoTo said:**
> No I just re installed, before I set the device for boot installation to my second drive so when the computer booted there was nothing to boot. Now all is well :) thanks anyway
 Good glad you are running, enjoy your Ubuntu.

---

