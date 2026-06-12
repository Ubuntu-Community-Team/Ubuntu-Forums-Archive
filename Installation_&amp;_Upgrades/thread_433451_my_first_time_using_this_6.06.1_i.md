---
title: "my first time using this 6.06.1 i"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by chris-004140861 on 2007-05-05
how do i boot this and is it a live cd please post asap as i have be told this is good thank you i hope this works

---

### Post by jfinkels on 2007-05-05
> **chris-004140861 said:**
> how do i boot this and is it a live cd please post asap as i have be told this is good thank you i hope this works

Burn the Ubuntu .iso image to a disk, put it in your cdrom drive, restart your computer (make sure your BIOS is set to boot from cdrom drive before booting from hard drive!), choose "Start or Install Ubuntu"  when given the option and you will be in the Ubuntu LiveCD environment.

I am assuming you have the standard Ubuntu desktop iso.

---

### Post by chris-004140861 on 2007-05-05
what do i do when my pc is booting up in bios (white writing on a black background) i press f11 chouse cd then is there a option for live cd will be very grateful if u can help me use this

---

### Post by jfinkels on 2007-05-05
> **chris-004140861 said:**
> what do i do when my pc is booting up in bios (white writing on a black background) i press f11 chouse cd then is there a option for live cd will be very grateful if u can help me use this

Pressing F11 while the computer is starting up brings you to the Setup page for the BIOS, correct?

Once you are there, find something that says "Boot Order" or something similar. Make sure the boot order has the CDROM drive before any hard drive, change it if necessary and save the changes. Then exit and reboot.

Your computer should now boot into the Ubuntu CD. You will see an "Ubuntu" logo after a while with some text options on the screen. Select the first option, that says "Start or Install Ubuntu". This will bring you into the Live CD environment.

I'll be checking back here often so I will see when you make a new post :D

---

### Post by chris-004140861 on 2007-05-05
ok  i read about the f11 thing i'll give it a try but my cd drive is not listed dvd drive yes

---

### Post by chris-004140861 on 2007-05-05
that did not work please could u run me the intire thing as in press del then conrol  because of it been my first time using this i know not much about it

---

### Post by jfinkels on 2007-05-05
> **chris-004140861 said:**
> ok  i read about the f11 thing i'll give it a try but my cd drive is not listed dvd drive yes

Your DVD drive is most likely both a DVDROM and CDROM drive :) sorry for being unclear, there.

---

### Post by chris-004140861 on 2007-05-05
still not working

---

### Post by jfinkels on 2007-05-05
Your boot order shows your cdrom drive before your hard drive and its still not working?

Is your "DVD drive" capable of reading the CD? Which Ubuntu iso file did you download? Did you burn the iso image to the disc correctly (i.e. when you view the files on the disc you should see many files...if you see one file, you did not burn the disc correctly)? Did you burn the disc at a slow speed?

Maybe take a look at this [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) if you need to learn more about burning an iso image to a disc.

---

### Post by chris-004140861 on 2007-05-05
it has all the files on it i checked that it was done by extrating using undisker then windows copyed it i dont know i dont think the pc likes the idea of another os

---

### Post by chris-004140861 on 2007-05-05
i might be in with a stroke of look i have found something in a pc mag i'll keep u posted on it thanx for your help so far

---

### Post by jfinkels on 2007-05-05
> **chris-004140861 said:**
> i might be in with a stroke of look i have found something in a pc mag i'll keep u posted on it thanx for your help so far

Hmm putting in a different disc to boot from probably won't have any effect if your system fails to boot at all from your DVD/CD drive. I hope things work out for you with this tricky drive, I don't know why your system fails to boot from the disc. Let me know if it works with a different boot CD.

---

### Post by chris-004140861 on 2007-05-05
do u know where i could find some guid which will take me throght instaling it on to my speret drive NOT THE WINDOWS ONE

---

### Post by jfinkels on 2007-05-05
> **chris-004140861 said:**
> do u know where i could find some guid which will take me throght instaling it on to my speret drive NOT THE WINDOWS ONE

I think what you're asking here is for a guide for installing Ubuntu on your second hard drive. You still need to be able to boot from your disc drive for this to happen, so we first need to figure out why you can't boot from your disc drive.

Did you download an .iso from this page [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) ? Which one did you download? When you wrote the .iso image to a disc, did you do it at a slow speed?

From the BIOS, try to disable booting from your hard drives completely, and see if the system is able to boot from the DVD/CD drive.

---

