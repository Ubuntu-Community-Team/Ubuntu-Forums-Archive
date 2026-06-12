---
title: "LiveCD I/O Error on laptop, fine on desktop"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by Vudusu on 2008-01-28
I'm trying to get Ubuntu on my Compaq Evo N600c, which has incomplete installs of two OSs--in other words, no OS. Often I can't get it to boot from the CDROM drive at all, resulting in the message Error Loading Operating System. When I can get it to boot from the livedisc, choosing *start or install* or *check cd integrity* gets me the I/O error: > Could not find ramdisk image: /casper/initrd.gz The memory test will run properly.

I checked the disc's integrity on my desktop machine and it passed. Any ideas where I can go from here? Would running a zero fill on the hard drive help? Could it be the CDROM drive? 

I don't have any other OS I can try loading on it.

---

### Post by apaciq on 2008-01-29
How much ram does your laptop have? To run live cd, it needs about 256mb of ram....could  be that the laptop doesn't have enough ram...
i had errors on the dell laptop, but no probs with 7.04...i just let it run and it installed ok..strange....but check how much ram you have...

---

### Post by Vudusu on 2008-01-29
The laptop has 256M of RAM, and I've installed Ubuntu on it before. First I had Ubuntu partitioned, then I went with full Ubuntu install (for whatever reason...not like I needed the partitioned space), then tried to put Windows back, which wouldn't finish installing, then tried Ubuntu again, but I had the wrong Live CD (text based) and stopped the install, and here I am now :P

I've tried it at least ten times, and I get the same error every time.

---

### Post by MasterAslan on 2008-01-29
Try the alternate cd to do a text mode install.  Thats what worked when I had this error in the past.

---

### Post by apaciq on 2008-01-29
Did you get a chance to totally wipe the hard drive?  Try and see if this will work for you...i had to format my laptop when i had initial errors...seems to help....I am sure someone who has  better understanding of ubuntu will come along and help out...don't give up on it yet...

---

### Post by Vudusu on 2008-01-30
Text-based install got me past the I/O error, but I'm up to installing the base system and every file is coming back as corrupt. I checked CD integrity on my desktop system before I tried the install.

A zero-fill format seems like the next step, but I'll need to know the brand of hard drive to get the right software for that, and the only way I can think to get that info is opening up the laptop.

Can I even run a zero-fill on a system with no OS?

Is there any other option for formatting the drive on a system with no OS?

---

### Post by MasterAslan on 2008-01-30
Download the UBCD which has lots of hard disk tools.  You will find a few that can do 0 fill format.  It doesn't really matter if its one from your drive manufacturer.

---

### Post by apaciq on 2008-01-30
Starting to wonder if the hard drive on the laptop is going bad....If you are familiar with windows utility programs, you can check the integrity if the hard drive...i think you can try BartPE to check on this...can't remember which i used to check on my windows machine...there could be a bad sector that is causing install problems...but who knows...

Anyone have any ideas to help with this?

---

### Post by Vudusu on 2008-01-30
> **apaciq said:**
> Starting to wonder if the hard drive on the laptop is going bad....If you are familiar with windows utility programs, you can check the integrity if the hard drive...i think you can try BartPE to check on this...can't remember which i used to check on my windows machine...there could be a bad sector that is causing install problems...but who knows...

Anyone have any ideas to help with this?

I ran a self-check on the drive via the set-up menu. As far as Windows utilities, again, my machine has **no OS**.

> Download the UBCD which has lots of hard disk tools. You will find a few that can do 0 fill format. It doesn't really matter if its one from your drive manufacturer.

I'll try to find this UBCD. The only means I have of getting programs to the laptop is via burned CDs/DVDs--will I be able to run these utilities from a disc with no OS?

---

### Post by apaciq on 2008-01-30
Yes,,you should be able to run the diagnostics with out any OS on the hard drive...try UBCD and go from there...

---

### Post by Vudusu on 2008-01-30
Oy, I keep getting "boot failed" from the UBCD. I get the copyright header for a minute, then this error:


> isolinux: Disk error DF, AX = 42E7, drive 9F
Boot Failed, retry?

---

### Post by apaciq on 2008-01-30
try  Super F-disk(?)  according to what i have read on some problems on the forums...super fdisk will clean out any residual imprints of any OSes and sometimes this is the cause, but don't give up, since there will be a solution somewhere...

---

### Post by Vudusu on 2008-01-30
Super Fdisk's bootable CD just resulted in an unresponsive cursor, and I also tried burning one of UBCD's formatting utilities as a standalone, and that didn't work either. It's hit or miss just getting the laptop to boot from the CD drive--usually takes several restarts. I'm starting to think it's a hardware problem.

---

### Post by Vudusu on 2008-01-30
I managed to wipe the hard drive, but it didn't help. The Alternative LiveCD still reads as corrupt and fails the integrity test on the laptop, but works on my desktop PC. I'll try downloading and burning a new copy of the CD, but I'm not optimistic.

---

### Post by apaciq on 2008-01-30
Starting to suspect that the cd-rom  drive is faulty? Really don't have much of way of helping at this moment...but according to what you wrote...looks like you may have a faulty drive as you are suspecting....

---

### Post by apaciq on 2008-01-30
just dawned on me that i had a similar problem when i tried to install gutsy...didn't have prob with fiesty...what i did was swap out the cd-rom with a cd-rw/dvd combo drive...tried fiesty...worked...tried gutsy..gave me i/o errors then it installed ok...worked from then on...put the original cd-rom drive again..laptop couldn't read the gutsy cd....took out the media out...rebooted fine....able to play music....and see other media..henceforth...still using it today...Don't know why it happened but it did...If I am forced to reinstall again....i will do it this way since it worked for me...
help anyone??

---

### Post by Vudusu on 2008-01-30
I tried a DVD rather than a CD and made it a little farther, but still failed integrity on the laptop and can't install. 

I think it's the DVD-R/W drive--it's not operating consistently. My method of getting the laptop to boot from that drive has been basically stalling at the setup screen until the drive gets up to speed, and if the timing's off, I have to restart and try again. Often it takes half a dozen restarts to get that drive to boot, and success has no connection to any changes in settings or what disk is in the drive. 

I don't have another laptop drive to swap out. Could it be the drivers? Would I be able to load new ones from a boot disk?

---

### Post by apaciq on 2008-01-31
you can try re-seating the cd drive module, by taking it out then sorta slam it in , but not to hard where you will render it totally useless..or it could be that the lens are dirty(?)..Or..read the reply on your other post by using a usb....is this the same laptop??

---

### Post by MasterAslan on 2008-02-02
really sounds like your cd drive is failing to me.  Do you have a USB stick that you can use?

---

### Post by Vudusu on 2008-02-03
I don't have a stick and the laptop wouldn't boot from USB anyway. Looks like I'll have to track down another drive to make it work, if that's really the problem.

---

