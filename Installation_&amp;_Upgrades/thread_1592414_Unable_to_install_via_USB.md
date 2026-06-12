---
title: "Unable to install via USB"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by NuclearThermalPropulsion on 2010-10-10
Hello,

I'd like to install 10.10 netbook edition on my Asus eee 1000, but when I choose my USB drive from the boot select screen, all I get is a single line telling me:
'SYSLINUX 3.86 2010-04-01 EBIOS Copyright (C) 1994-2010 H. Peter Anvin et al'

I have tried installing the ubuntu-10.10-netbook-i386.iso file on my USB drive many times with pendrivelinux.com's Universal USB Installer and once with the USB Creator on the .iso file, but it always gives me the same one line and nothing else. I even tried it on my Dell laptop, but still the same problem.

Any ideas?

---

### Post by JackNocturne on 2010-10-10
Its a problem with SYSLINUX boot loader

Try solution from

[http://ubuntuforums.org/showthread.php?p=9948980](http://ubuntuforums.org/showthread.php?p=9948980)


Happy Sunday:)

---

### Post by NuclearThermalPropulsion on 2010-10-10
Ok, I changed it in notepad, but now all that happens is that I get an additional line:
'Unknown keyword in configuration file: gfxboot'

---

### Post by JackNocturne on 2010-10-10
Sorry i didnt specify, the solution works if you use Ubuntu's **Start-up disk creator** ( also knows as USB-disk creator)

---

### Post by NuclearThermalPropulsion on 2010-10-10
Well, I don't have an working Ubuntu machine available (I completely screwed up my 10.04 installition a few hours ago) :'(

So I guess I should try to reinstall 10.04?

---

### Post by JackNocturne on 2010-10-10
Are you using Windows? 

I checked the pendrivelinux's Universal USB Installer from their site just now. Are you using the latest update as of today (10.10.10) ?? They have a new version(update) it seems.

---

### Post by NuclearThermalPropulsion on 2010-10-10
Yep, I did use 1.8.0.4 in the end at least. Didn't work.

They still don't have the 10.10 netbook edition in their list, though, but they plan to add it soon, I guess.

---

### Post by Mattallyc on 2010-10-10
I've had some success using unetbootin instead.
Got it to install and boot off of USB, managed to do the install to HDD but now the installed version won't boot.
YMMV...
Let me know if you get any success. The brief glimpse I got of the new version looks very nice...
Cheers,
Matt.

---

### Post by wilee-nilee on 2010-10-10
Download the ISO first then use unetbootin to load the thumb. Reformat the thumb before loading to a new fat partition.
[http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/)

The edit in wordpad of the syslinux probably doesn't save correctly, it is a gedit format.

---

### Post by NuclearThermalPropulsion on 2010-10-11
Thanks, it worked perfectly with unetbootin!

---

### Post by mörgæs on 2010-10-11
Good. Please mark the thread 'solved'.

---

