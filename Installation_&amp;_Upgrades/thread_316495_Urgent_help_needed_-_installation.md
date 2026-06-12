---
title: "Urgent help needed - installation"
date: 2006-12-10
forum: Installation &amp; Upgrades
---

### Post by EShirazi on 2006-12-10
Hello everyone.

I am new to the whole Ubuntu Linux scene, and I've looked everywhere.

I have a Dell Inspiron 1100 Windows XP laptop, and I just downloaded / burned the LiveCD. But when the CD opens up on my laptop, a startup screen pops up saying "Launching browser, please wait.." 

And then a window pops up... the title of the window is Ubuntu 6.06 (DiscTree)

And it says "Boot from this CD to try Ubuntu without affecting your system. It has various amount of Open Source Windows Applications, such as Firefox and etc, and a brief tour.

But that is all... I want to INSTALL Ubuntu, the actual Operating System. 

Can someone please help a newbie and guide me through the process of installing Ubuntu?

---

### Post by Tux Aubrey on 2006-12-10
Hi and welcome!

Go with the flow - let the live CD boot through to the desktop.  You will have the option (via a desktop icon) to install it onto your harddrive. depending on your specs, this will take about half an hour.  You will only have to answer a few questions about your time zone, user name and password, before you will get to the partitioning options.  This is where you'll decide whether to go with a dual boot (Ubuntu/Windows) setup or save time now and wipe Windows off your system ;) 

If you want to dual boot, just leave the first partition alone and create a new Ext3 partition and a linux swap partition about twice the size of your RAM.  This should be fairly intuitive.

From then on, sit back and enjoy.

---

### Post by EShirazi on 2006-12-10
Thanks for the quick reply... But I'm getting no icon on the desktop to install Ubuntu. I need a complete step by step, detailed installation guide on how to do this, for I am not familiar with this type of work.

Thanks!

---

### Post by aysiu on 2006-12-10
When that window appears that says > Boot from this CD to try Ubuntu without affecting your system. It has various amount of Open Source Windows Applications, such as Firefox and etc, and a brief tour. you're still logged into Windows, right?

In order to preview Ubuntu and install it, you need to reboot your computer with the CD still in the drive. Make sure your BIOS is set to boot from CD, too. Otherwise, it will just boot straight into Windows again.

Do you know how to get into your BIOS settings? It's usually a key you press during bootup--Escape or F1 or something.

---

### Post by EShirazi on 2006-12-10
Ah, I see. Well, here's another sad problem I have.

For some reason, my primary CD drive isn't able to boot anything whatsoever, not even a Music CD. So, I have an external CD drive connected to my laptop, which isn't really doing a good job with booting the CD when I restart the computer... nothing happens.

How do I make the external CD drive as my primary CD Drive?

---

### Post by tragicglee on 2006-12-10
Reboot - keep an eye on the screen because just before BIOS loads, you *should* see a message that says something like "Press <FKEY> to enter setup", or  "<FKEY> to enter setup, <FKEY2> for boot menu". IF you get a boot menu option, go there and see if your external CD drive is listed. IF not, reboot, go into setup < *usually* F2 > and nagivate to something like BOOT DEVICES or BOOT ORDER. If the CD is listed there, change the order so its booting first. Save your changes, and exit. Your PC should then boot from the CD

---

### Post by EShirazi on 2006-12-10
Oh man, I keep running into problems.

I get to the boot screen, and where it says "Load Installer Components from CD" it says:

There was a problem reading data from the CD-ROM. Please make sure it is in the drive. If retrying does not work, you should check the integrity of the CD-ROM.

Failed to copy file from CD-ROM. Retry?

I hit yes, and the same message keeps popping up. What do I do?

---

### Post by madivad on 2006-12-10
Take the CD out of the removable drive you have plugged in and try it in the internal one.

---

### Post by EShirazi on 2006-12-10
I have, several times. But the problem is that my internal CD drive doesn't run anything.

---

### Post by tragicglee on 2006-12-11
What did you use to burn the ISO, and did you verify the data after the burn?

---

### Post by EShirazi on 2006-12-11
I used Imgburn or something. And sadly, no... How do I verify it?

EDIT: I do know how to verify it now. 

Well I'm reburning it; I am not too sure if I verified it before, I hardly doubt I did.

But what does verifying do?

---

### Post by SonicChao on 2006-12-11
Verifying makes sure that the image was downloaded correctly.

---

### Post by tragicglee on 2006-12-11
verifying will let you know if the CD is an exact match of the data it was burnt from.

---

### Post by EShirazi on 2006-12-11
okay well heres the problem

as it was verifying, an error came up saying that one of the sectors was messed up or something... the squashf file I believe? I dont exactly remember

what do I do?

EDIT: the file is ./casper/filesystem.squashfs
it keeps happening to every file I download and burn!

---

