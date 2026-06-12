---
title: "Major installation problems"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by h0bbit51 on 2008-01-25
So, here's the deal. I have a CyberPowerPc, and it is about 1 year old. I checked all of the hardware that it currently has, and there were no problems with incompatibility with Linux. So I created an installation CD, and loaded it up. While runninig on the Live CD thing, I experienced no problems. After testing it for a while I told it to install the OS, using the entire hard disk. I then went to bed for the night, because it was getting late. When I woke up in the morning it told me that the installation was successful and that I should restart my computer now. So I did. But when it was starting up, it made it past the BIOS and then froze. I have turned it off and on countless times, and tried everything I can think of. My computer will now no longer load any CD either (I retried the LiveCD and even tried my Windows installation CD). So basically, my computer will not start and there is nothing that I can think of to do about this. Does anyone have a suggestion of what could have caused this problem and what I can do to fix this? The only thing left that I can think of is having my local computer professional completely wipe the hard drive and start over, but I would really not like to do this. Thanks in advance for any help you may be able to give.

---

### Post by david_kt on 2008-01-25
Could try to remove any external disk (usb), if any. If there isn't any and still could not boot from CD, could you enter bios and change the boot sequence (boot from CD first)?

In one of my PC,sometimes boot sequence could change by itself, I also do not why. So, you should manually change it to boot from CD again if you want to boot from CD.

DK

---

### Post by h0bbit51 on 2008-01-25
There are no USB ports in use, and I have tried to boot from CD first by changing boot order. Even with this, after the BIOS screen it just displays a black screen with a blinking underscore in the upper left. Thanks for the idea though.

---

### Post by david_kt on 2008-01-25
Then try to remove your harddisk (unplug the cable from your harddisk) and try to boot (from CD), see if this work.

If not, try to remove the battery on your motherboard, after remove it for a few seconds, put it back and go to Bios and make sure to boot from CD is selected and then boot again.

If those 2 actions do not solve your problem, that might be some hardware failures.

DK

---

### Post by h0bbit51 on 2008-01-25
Well, taking the hard drive out and then booting from a CD seems to work (I am using a laptop BTW, if that changes anything). The thing I need to figure out now is how to make the hard drive work again. Any ideas on how I can get it to work again?

---

### Post by david_kt on 2008-01-25
That is good, that means the problem is only on your harddisk. But I am not sure why the harddisk problem preventing you to boot from CD though.

What you could try is to install your harddisk to dekstop computer as second harddisk. You need an adapter to plug it to desktop computer. After that you could erase it using gparted or any other software and then put it back to your laptop.

DK

---

### Post by h0bbit51 on 2008-01-25
Yeah, I was thinking that would be the way to go. Thanks for all of your help!

---

