---
title: "Can't install ubuntu. Bios error?"
date: 2016-08-16
forum: Installation &amp; Upgrades
---

### Post by clonezonedude on 2016-08-16
Hi all

The other day, my laptop overheated in ways never happened before (I couldn't grab it for a good 10 minutes)

When I got this under control, I went to boot my ubuntu with no success

I tried to install 16.04 from a pendrive, only to get errors that included corrupt hdd, and prompts to reboot

I finally decided to reboot, but now I can't even get to the test before install ubuntu from my pendrive

Here are 2 pics I took. I don't know what to do, and I really need my computer to work plz!!

Please help me

Thanks in advance

[IMG]http://i68.tinypic.com/112fzvb.jpg[/IMG]
The error I get from trying to boot from the pendrive

[IMG]http://i63.tinypic.com/1076t7r.jpg[/IMG]
No matter what I pick, it takes me back there after 30 seconds of blank screen

---

### Post by ubfan1 on 2016-08-16
Can you take your hard disk out of the laptop, put it into an USB enclosure, and read it on another machine?  What does the SMART report say about the disk?  (smartmontools package, sudo smartctl -a /dev/sd?
Can you put a new or blank known working disk into your laptop and install Ubuntu from the pendrive?  Take the problem and divide it into two parts, the disk, and everything else and see if you can narrow it down.  Hopefully, both are not bad, but sounds like things got fried.

---

### Post by Bucky Ball on 2016-08-16
In your second screen, the USB is not there to select. Are you sure you created the install USB correctly?

When you severely cook a laptop there is a reasonable chance that the hard drive or one (or more) of the other components are fried. How are you creating the USB?

---

### Post by clonezonedude on 2016-08-17
> **ubfan1 said:**
> Can you take your hard disk out of the laptop, put it into an USB enclosure, and read it on another machine?  What does the SMART report say about the disk?  (smartmontools package, sudo smartctl -a /dev/sd?
Can you put a new or blank known working disk into your laptop and install Ubuntu from the pendrive?  Take the problem and divide it into two parts, the disk, and everything else and see if you can narrow it down.  Hopefully, both are not bad, but sounds like things got fried.

I was thinking of buying a hard drive... I don't have a usb enclosure... should I invest on the enclosure or the drive straight out?

I put the laptop to sleep, but some how it turned on on its own inside of my laptop case, and fried because it was in my car all day... thanks God, it didn't ignite... I would have lost car and laptop)

Hopefully is only the hdd :(

---

### Post by clonezonedude on 2016-08-17
> **Bucky Ball said:**
> In your second screen, the USB is not there to select. Are you sure you created the install USB correctly?

When you severely cook a laptop there is a reasonable chance that the hard drive or one (or more) of the other components are fried. How are you creating the USB?

Yep, screen 2 is without the usb (I took it out before turning the laptop on). I was using the USB to try to install 16.04... I repartitioned to get rid of all the ,,broken" stuff and start on a clean slate

I tried unetbootin, but the resulting usb wasn't working well for some reason, then I tried the kubuntu live usb creator (I was using kubuntu as back up os, in case something like this happened)

The second creator was the one that got me the Ubuntu live test running

---

### Post by clonezonedude on 2016-08-18
Should I just buy another hard drive? Would it work if I install ubuntu on a external?

---

