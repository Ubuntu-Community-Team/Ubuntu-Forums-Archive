---
title: "Moving from windows 98"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by Win98Rocks on 2007-04-12
I have an old compaq presario 1200 that up untill yesterday ran windows 98. I decided to pass the laptop on to my son (its the machine I learned to code upon... wiping my eyes here).

So I restarted the machine in dos mode and typed in the famous words "format c:" and accepted my choice.

Now to my problem:
I do not have a boot disk, and I want to install edubuntu.

But what to do?

I dont have internet access on the compaq machine, but I installed smart boot manager 3.7.1 using a floppy.

I have a copy of edubuntu from [http://releases.ubuntu.com/edubuntu/6.06/](http://releases.ubuntu.com/edubuntu/6.06/) I chose PC (Intel x86) install CD since it says "Choose this if you are at all unsure" which I was.

How do I install edubuntu?

---

### Post by matthew on 2007-04-12
If the laptop will boot from a cd, put the cd in the drive and go from there.

You may need to enter and change the laptop's bios setting for boot order. Usually that involves pressing F5, Esc, or something else shortly after turning the machine on...look for a message at power up that tells you what to press.

---

### Post by Win98Rocks on 2007-04-12
It will not boot from cd drive, I downloaded the edubuntu and burned it as a file, when I check it looks fine. I tried to change the boot from floppy to cd drive but still nothing happens.

---

### Post by bernied on 2007-04-12
You need to burn the iso file as an image, not as a file.
When you look at the cd, is there just one file (.iso) or many?

Do you have any other live cds? Like a Windows install or recovery disk?
Do any other live cds boot?

Does the live cd work on another machine?

---

### Post by Win98Rocks on 2007-04-12
Ok so I need to burn the iso as if it had been an actual jpg or gif image?

---

### Post by bernied on 2007-04-12
Sorry, by image I mean disc image, not picture-type image.

This is done differently depending on what software you are using to burn the cd.
For instance, I use K3b and there is an option to 'Burn CD Image'. Other software will offer to burn an .iso image. Some CD-burning tools won't do this at all. If you have to resort to using Windows, there is a freeware program called [ImgBurn](http://www.imgburn.com/).

---

### Post by az on 2007-04-12
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by bernied on 2007-04-12
And, just in case the problem is that you really can't boot from a CD on your old beast...
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

---

### Post by Motoxrdude on 2007-04-12
Do you have another computer that can burn CDs? If you do and it runs windows, download [deepburner free edition]("http://www.deepburner.com/download/DeepBurner1.exe") and install it. Get your Edubuntu ISO ready and put it somewhere that you can remember (I usually put mine on the desktop). Start up deepburner and select "Burn an ISO image" (or something close to that, i can't remember the exact name). Now it will ask you where the ISO is, locate your EDUbuntu ISO and select OK. Now go ahead and burn it.
Once that is done burning take the CD out of the drive, label it and put it in your laptop. Turn your laptop on. If you see a Ubuntu logo with a menu then you are good to go, if not you need to change your laptop's bios so that it boots from the CD. Restart your laptop and as soon as it turns on press either F2, F1, Esc, F8, F10, Delete, or F12. Every computer is different, but usually one of those will work. If you do get into the bios look around for something that says "Boot Order" and make sure that  your CD drive is the first boot device. Save and Exit.
Restart your laptop and if the ubuntu logo pops up then great, it works! Go ahead with the install.
O and btw, how much ram does that laptop have?

---

