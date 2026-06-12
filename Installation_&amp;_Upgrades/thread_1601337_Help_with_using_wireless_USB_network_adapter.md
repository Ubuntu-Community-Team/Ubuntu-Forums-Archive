---
title: "Help with using wireless USB network adapter"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by J03_66 on 2010-10-20
Hi, I just started using Ubuntu 10.10 recently. and Im not really sure how most of this stuff works. I could probably figure most of it out myself, but I have a question about using a wireless USB stick for internet.

I do not have internet on my desktop (the computer with linux on it) and the only way i can get it is by using a Dynex Wireless G USB Network Adapter. 

I do not have the disk for it. and Im guessing linux doesnt have the autoinstall thing that windows has (no offense to linux, im starting to love it more than windows). I have the driver for it on my windows computer. I was wondering if i could run the driver from a usb thumb drive.

If not, then how can i get the network adapter to work?

---

### Post by P4man on 2010-10-20
Have you tried plugging it in? 
Most USB wifi adapters just work. Plug it in and click on the network manager icon top right (Or right click first and make sure wireless is enabled).

If thats a no go, then we need to know exactly what chipset is used in that wifi card. Keep it plugged in, open at terminal (applications > accessories > terminal) and type

```
lsusb
```

Copy paste the output to an usb stick and post it here, or just type the relevant line.

---

### Post by J03_66 on 2010-10-20
yeah, i plugged it in, and it wasnt being detected or something. Ill try that command

beback soon:guitar:

---

### Post by J03_66 on 2010-10-20
so this is what i got...


Bus 001 Device 005: ID 4317:0720 Broadcom Corp. Dynex DX-BUSB

---

### Post by P4man on 2010-10-20
Some googling suggests there is little to no hope to get that one working under linux, not even with ndiswrapper (windows drivers). I wont stop you or anyone from trying, but I suggest you buy another one or stick with windows.

---

### Post by J03_66 on 2010-10-20
aw lame.. 

alright D:  

luckily today i found an Internet cable underneath my staircase... it was like the linux gods wanted me to connect to the internet :O

---

