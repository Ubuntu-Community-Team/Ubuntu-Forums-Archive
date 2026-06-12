---
title: "Installation of Lubuntu 16.04.3 LTS stuck near end of process."
date: 2017-11-13
forum: Installation &amp; Upgrades
---

### Post by HSovieticus on 2017-11-13
LubuntuErrorScreenScan [https://imgur.com/gallery/JCzkj](https://imgur.com/gallery/JCzkj)

Hi so I followed these instructions: [https://rtechsupport.org/kb/linux-installation/](https://rtechsupport.org/kb/linux-installation/)

I installed lubuntu 16.04.3 LTS from within the try environment on a pen drive with a persistence file of 340mb (i think), it should be installing onto 100gb of unallocated space alongside win 7. I don't know what to do. Should I try turning off my computer then prepare the drive for an alternate installer?

---

### Post by HSovieticus on 2017-11-13
I Turned It Off [https://imgur.com/gallery/Ls4Up](https://imgur.com/gallery/Ls4Up)
I got tired of waiting and I became certain it wasn't going to finish. So now what do I do?

EDIT: it seems to be working, im writing from lubuntu in firefox now but it sure is slow. it was faster when i was trying it out on usb.

how do i check if everything is fine?

---

### Post by yancek on 2017-11-13
The image you posted in your initial post is the standard message before the installation finishes and does not show any error.  How long did the installation take?

The image in your second post is simply the Grub boot menu one would expect.  It should not be slower installed to a hard drive than form usb.  Can you post some information on your hardware.  Boot your Lubuntu and open a terminal and run the command below which will output detailed hardware info which you can post here to get some help.

```
inxi -F 
```

---

### Post by HSovieticus on 2017-11-14
Hi. No it didnt show any error. It just froze at that moment and stayed there for 3 hours until i force rebooted my computer. And ya it wasn't slower than the usb with the same version, it was slower than the usb with 17.10, because i hadn't done updates yet. I reinstalled with more success using 17.10 and did some tweaking and now its running fine. I just can't get my swap to work

[https://imgur.com/iLJpSmA](https://imgur.com/iLJpSmA)
on the right console you can see the error message.
on the left you can see its not using swap.
i removed my swapfile and created a bigger swap partition and did everything in the swapwiki here, but it cant find the device.


[https://imgur.com/s8ZUJRP](https://imgur.com/s8ZUJRP)
here is fstab and gparted with info

inxi is not installed.

---

