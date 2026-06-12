---
title: "Ubuntu burning to USB"
date: 2014-12-09
forum: Installation &amp; Upgrades
---

### Post by sai7 on 2014-12-09
Hello, I'm new to this community so please bare with me and what I have to say.

Ok, so I have downloaded the recent version of Ubuntu. I wanted to install it on to my PC so I can have dual booting, but there's a problem. So I can't boot into USB because I didn't format and make it boot-able. I can't boot into CD because my only CD I have can only hold 700 MB and the recent version of Ubuntu is 938 MB or so. So I ended up using a VM for my school that already has Ubuntu installed. Since I have a spare SD card that's 2 GB, I decided to format it and burn Ubuntu onto it. I've burned it all the way from 1 PM this afternoon and it's 8 PM now. I'm stuck on 96% for the past 30 minutes or so.

I'm in the files and I see that most of the files are burned onto the SD card. Is it safe to assume that Ubuntu will work properly if I cancel the process and disconnect the SD card? Or should I just let it keep burning because I don't see the progress anymore.

When it was at like 50% or so, it always tells me how much time remaining I have and how much storage it's going to be using, but since it's on 96%, it won't even show those results anymore.

I don't want to restart the burning process all over again because I've been burning Ubuntu onto the SD card for almost 6 hours now.

---

### Post by Darth Riker on 2014-12-09
> **sai7 said:**
> Hello, I'm new to this community so please bare with me and what I have to say.

Ok, so I have downloaded the recent version of Ubuntu. I wanted to install it on to my PC so I can have dual booting, but there's a problem. So I can't boot into USB because I didn't format and make it boot-able...

Hi there. In regards to your USB did you do the following to make a bootable live USB: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) ?

Additionally - did you make sure that when you boot your PC it is set to boot from USB?

---

### Post by sai7 on 2014-12-09
> **Darth Riker said:**
> Hi there. In regards to your USB did you do the following to make a bootable live USB: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) ?

Additionally - did you make sure that when you boot your PC it is set to boot from USB?

I actually followed these steps.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Right now, I'm still on the burning process. I haven't even started booting yet. My concern is re-burning all over again if I disconnect the SD card from the VM and then boot it up. Before, my PC was really laggy when the progress was still active. Now my PC is less laggy which means that the progress has halted some how.

I would really like to get a confirmation if it's safe to assume that I should be able to disconnect the SD card from the VM and use the SD card to boot.

---

### Post by Darth Riker on 2014-12-09
> **sai7 said:**
> I actually followed these steps.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Right now, I'm still on the burning process. I haven't even started booting yet. My concern is re-burning all over again if I disconnect the SD card from the VM and then boot it up. Before, my PC was really laggy when the progress was still active. Now my PC is less laggy which means that the progress has halted some how.

I would really like to get a confirmation if it's safe to assume that I should be able to disconnect the SD card from the VM and use the SD card to boot.

Considering that it appears that the installation to the SD Card hasn't actually completed (in fact - it appears that it has frozen) my personal opinion is that if you tried to disconnect the SD card from the VM and boot with it - it would fail.

Did you read this Ubuntu Wiki Page about Booting From SD: [https://help.ubuntu.com/community/BootFromSD](https://help.ubuntu.com/community/BootFromSD) ?

I'm not exactly clear on why you are using an SD Card over a USB stick though.

---

### Post by sai7 on 2014-12-09
> **Darth Riker said:**
> Considering that it appears that the installation to the SD Card hasn't actually completed (in fact - it appears that it has frozen) my personal opinion is that if you tried to disconnect the SD card from the VM and boot with it - it would fail.

Did you read this Ubuntu Wiki Page about Booting From SD: [https://help.ubuntu.com/community/BootFromSD](https://help.ubuntu.com/community/BootFromSD) ?

I'm not exactly clear on why you are using an SD Card over a USB stick though.

Alright, that's all I needed to know. I haven't read up on that yet, but I think I should. Also, it's because the only thing I have that is an empty device is the SD card that's 2 GB. I have about 2 USB that can hold the Ubuntu installation, but when I tried to use the default Startup Disk Creator, the USB partition said there wasn't any space left when in fact, I have 3.81 GB left of free space on my USB drive.

So I decided to use the SD card. I reformatted it to FAT32, plugged it in and the SD card said it was good to burn Ubuntu on.

I just recently installed Ubuntu on my VM too so I know how it's suppose to work, but without a CD that's rewritable or even have enough space, I can't really burn Ubuntu on. I guess I should just wait this out and buy a CD that's rewritable because I don't think the SD card nor the USB drive is bootable. I've changed the directions in where my Windows boots up first, but I still can't boot up the USB drive that I have plugged in the back of my PC.

---

### Post by sammiev on 2014-12-09
How old is your computer and the specs please.

---

### Post by Darth Riker on 2014-12-09
> **sai7 said:**
> Alright, that's all I needed to know. I haven't read up on that yet, but I think I should. Also, it's because the only thing I have that is an empty device is the SD card that's 2 GB. I have about 2 USB that can hold the Ubuntu installation, but when I tried to use the default Startup Disk Creator, the USB partition said there wasn't any space left when in fact, I have 3.81 GB left of free space on my USB drive.

So I decided to use the SD card. I reformatted it to FAT32, plugged it in and the SD card said it was good to burn Ubuntu on.

I just recently installed Ubuntu on my VM too so I know how it's suppose to work, but without a CD that's rewritable or even have enough space, I can't really burn Ubuntu on. I guess I should just wait this out and buy a CD that's rewritable because I don't think the SD card nor the USB drive is bootable. I've changed the directions in where my Windows boots up first, but I still can't boot up the USB drive that I have plugged in the back of my PC.

Hmm. In regards to your USB it sounds like you wanted to use a USB drive on which you already had other data. I think the best way to use this USB, and store other data on it, is to first copy the data already on the USB drive to your PC, and then partition the drive and put Ubuntu on it as outlined in this article: [http://www.howtogeek.com/97177/how-to-put-ubuntu-linux-on-a-usb-thumb-drive-without-the-mess/](http://www.howtogeek.com/97177/how-to-put-ubuntu-linux-on-a-usb-thumb-drive-without-the-mess/)

---

### Post by sai7 on 2014-12-10
> **sammiev said:**
> How old is your computer and the specs please.

It's only a year old. My specs are

Processor: AMD Phenom(tm) || X2 521 Processor 3.50 GHz
Installed Memory (RAM): 4.00 GB (3.25 GB usable)
System type: 32-bit Operating System, x64-based processor

Indexing rate is 3.5.

> **Darth Riker said:**
> Hmm. In regards to your USB it sounds like  you wanted to use a USB drive on which you already had other data. I  think the best way to use this USB, and store other data on it, is to  first copy the data already on the USB drive to your PC, and then  partition the drive and put Ubuntu on it as outlined in this article: [http://www.howtogeek.com/97177/how-to-put-ubuntu-linux-on-a-usb-thumb-drive-without-the-mess/](http://www.howtogeek.com/97177/how-to-put-ubuntu-linux-on-a-usb-thumb-drive-without-the-mess/)

Well yeah, I did before, but I found out that it's best to format the USB so that the installation can be done.





Any who. Thanks both of you. I actually asked my brother for a CD and he gave me an empty one that's 4.6 GB and it was empty so I burned Ubuntu on it and now I've successfully installed it onto my PC. I have dual booting now.

---

### Post by Darth Riker on 2014-12-10
> **sai7 said:**
> Any who. Thanks both of you. I actually asked my brother for a CD and he gave me an empty one that's 4.6 GB and it was empty so I burned Ubuntu on it and now I've successfully installed it onto my PC. I have dual booting now.

Glad you were able to sort it out in the end.

P.S. Make sure to mark the thread as Solved (using Thread Tools ... I think :P)

---

