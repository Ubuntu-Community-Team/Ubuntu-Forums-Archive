---
title: "Installation Problems on Compaq Desktop"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Vladeschav Sibul on 2007-10-21
Well the other day I decided to give Ubuntu 7.10 a try - you know just to see what its like.
Now, this would be my first experience with Ubuntu, albeit I used to use Knoppix in the past, this is my first experience with the Ubuntu flavor of Linux.

So, I download Ubuntu 7.10, and burn it onto a disk - thus creating a live CD.
I went a head and went to "my computer" and sure enough there it is, sitting there in the E drive with the Ubuntu thumbnail prominently displayed. So I go ahead and click it, it starts up and everything is going well. The resulting display tells me that this is an Ubuntu 7.10 live CD, that I am to leave it in my CD drive, and that when I reboot my computer I should be cheerfully greeted with and Ubuntu 7.10 installation setup. So I go ahead and reboot my computer.

So at this point I'm getting pretty excited, this is it, this is what I have been waiting for. So my trusty Compaq boots up and, to my great dismay, I am met with the familiar Windows XP startup display instead of the Ubuntu setup. Now at this point I'm a bit concerned but its no big deal - I'll just have to manually boot it from the CD drive. So I go ahead and reboot my computer, Press "esc" during the initial bios display which causes the boot menu to appear. So I select the dvd drive, where the live CD resides, and hit enter, but alas I am met yet again with Windows XP, Ubuntu is nowhere to be seen. I go ahead and reboot again, but this time I go into the bios and prioritize the DVD drive over the default boot drive, and again I am met with Windows.

I try and try again to no avail. Eventually I decided to come to this most excellent website to seek advice in hopes of solving my predicament. 

Any help would be greatly appreciated, thanks.

---

### Post by ntetreau on 2007-10-21
I don't want to sound alarming, but it seems you have mis-burned the CD!  If the CD was booting but crashing, you would never see the Windows XP logon.  So either your CD is not used as the first booting device (you seem confident that it is when you press ESC and choose it I presume) or it is not finding a bootable CD image on the disk.   Is it possible that in your great excitement (it is exciting!) you may have burned it wrong?

---

### Post by Vladeschav Sibul on 2007-10-21
This could be very true, I suppose I was rather hasty in the burning of the CD. I was using Infrarecorder as Ubuntu suggested, but I didn't manage to find any .iso files in the isolinux folder, so instead I burned the contents of the temp folder that was created when Ubuntu downloaded (about 695 mb) directly onto the CD itself. In searching the internet, before deciding to entreat the experts at Ubuntuforums, I saw a screenshot of what the Live CD file should look like (albeit it was for Fiesty Fawn) and it did indeed resemble the abomination of a live CD (or at least what I thought was a live CD) that I had created and yes, I had also gone through considerable trouble to reconfigure the boot settings in bios to prioritize the CD drive over the default boot drive. So this idea of a mis-burned CD is a very real (and somewhat disturbing) possibility.

If anyone would care to enlighten me on the names and locations of the kernel and root iso files that I am supposed to create an image of I would be greatly indebted to you.

---

### Post by ntetreau on 2007-10-21
I would try to burn it again using the right burning software if I was you.  I mean you could be hours fixing this CD instead of enjoyng fixing the little things that will make your Ubuntu installation perfect!  Please burn it again using Nero on Windows or Brasero on Linux!

---

### Post by Vladeschav Sibul on 2007-10-22
Oh yeah, I don't know if it makes much of a difference, but I'm trying to install the 32-bit version of 7.10 on my computer which has a 64-bit processor.

---

