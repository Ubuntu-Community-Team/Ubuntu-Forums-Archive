---
title: "New HD installation problems"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by thatguy7 on 2011-09-29
I recently got a new hard drive and decided to install ubuntu on it. My disk drive is broken so I have to use a flash drive, I put the iso file on the drive, set the bios to boot usb first, and went to install but when I booted up the screen said boot error and then went on to booting the disk drive and hard drive(both empty). I've tried booting on my laptop as well as my grandmothers PC to run the trial thing and both worked fine. Any ideas whats wrong?

---

### Post by matt_symes on 2011-09-29
Hi

How did you put the iso file onto the drive ? 

Did you use a program such as unetbootin or multiboot ?

What os did you use to put the iso onto the usb stick ?

Kind regards

---

### Post by thatguy7 on 2011-09-29
I used a program called Universal USB Installer, it was recommended by the ubuntu website. And the computer I used was a windows 7 laptop.

---

### Post by oldfred on 2011-09-29
If it worked on the other PCs then it should be installed correctly.

In you PC how do you select to boot from USB. My desktop has a variety of USB boot options, none work for a flash drive. I have to choose hard drive and the flash drive is seen as a hard drive.

Do you have a one time boot key (f12 on my system) or in BIOS options on which hard drive to boot?

---

### Post by thatguy7 on 2011-09-29
in BIOS below the boot order theres an option that says boot usb first and I enabled that. And the system definitely activates the flashdrive because the light on it blinks, up until the computer says boot error

---

### Post by oldfred on 2011-09-30
This is older info which I thought had been fixed, you can try unetbootin:

Bugs in usb-creator unetbootin is an alternative if usb-create does not work
[https://bugs.launchpad.net/ubuntu/+source/usb-creator](https://bugs.launchpad.net/ubuntu/+source/usb-creator)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by thatguy7 on 2011-09-30
I redid it using unetbootin and I still get the screen that says boot error and nothing else. but, just like before, it works fine on my laptop, just not the desktop

---

### Post by oldfred on 2011-09-30
Do you have an f12 or other one time boot key.

When I tried booting my USB flash using any of the USB options I got boot errors. But when I choose a hard drive and it saw the flash drive, which I chose, it booted.

---

### Post by thatguy7 on 2011-10-01
Just tried it and got boot error again

---

### Post by oldfred on 2011-10-01
We have seen some users that certain BIOS or certain flash drives just do not seem to work together. I have used both Kingston and Microcenters house brand without issue. What brand flash drive is it. I prefer flash now as it is reusable, but do you have a CD drive?

---

### Post by Quackers on 2011-10-01
I had to enable external booting in my bios and then had to choose USB HDD for 2 of my flash drives to be recognised.

---

### Post by thatguy7 on 2011-10-01
my brother broke my disk drive so flash is my only option. and the flashdrive is my 32gb patriot xporter

---

### Post by Hakunka-Matata on 2011-10-01
> **thatguy7 said:**
> [COLOR=Red]my brother broke my disk drive[/COLOR] so flash is my only option. and the flashdrive is my 32gb patriot xporterCome on now, we've all heard that one before..................

---

### Post by Quackers on 2011-10-01
My point is that 2 of my flash drives are not recognised by my bios as flash drives. They are recognised as USB HDD's

---

### Post by Hakunka-Matata on 2011-10-01
quackers, i was just trying to wind-up thatguy7 a bit....................

---

### Post by Quackers on 2011-10-01
I understand :-)
I'm just making sure that the OP knows that bioses can be quirky in the way they recognise devices.

---

### Post by thatguy7 on 2011-10-01
haha he really did, he always left it open and one day it snapped off. and i went in to boot options and selected it specifically so theoretically it shouldnt matter what its recognized as as long as its selected right?

---

### Post by thatguy7 on 2011-10-01
The version I'm trying to install is natty narwhal, is it possible id have better luck with an older version?

---

### Post by oldfred on 2011-10-02
Some suggest the 10.04.3 version as it is the long term support.

Is this an older computer and are you installing 32 bit or 64bit?

---

### Post by thatguy7 on 2011-10-02
Its a few years old and im using the 32bit version

---

### Post by thatguy7 on 2011-10-15
I finally gave up on using usb and borrowed my uncles disk drive. and the same thing happens, it skips right over the disk and trys to boot the blank hard drive

---

### Post by oldfred on 2011-10-15
A few BIOS require you to both change BIOS boot order and then also use f12 or whatever key to choose to boot another device.
Are you sure CD was burned correctly?
Did you check that ISO is correct?

---

### Post by thatguy7 on 2011-10-15
yeah. i checked it over and then tried it in my laptop. it worked fine

---

### Post by oldfred on 2011-10-15
Someone just reported that the fast boot or quick boot setting in BIOS interfered with booting a USB flash drive. Check that setting in your BIOS.

---

