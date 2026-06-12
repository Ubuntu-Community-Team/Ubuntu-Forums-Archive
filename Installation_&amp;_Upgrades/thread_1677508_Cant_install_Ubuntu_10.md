---
title: "Cant install Ubuntu 10"
date: 2011-01-28
forum: Installation &amp; Upgrades
---

### Post by aholm006 on 2011-01-28
Hello,
I am trying to install Ubuntu 10 on my presario 2100 and every time i try it fails in some way.

I tried to boot from USB and it acted like it was never there

I created a Ubuntu disc but 1 of two things happens.

When i try to boot it from the disc it will go pass the logo screen and then just freeze after a few minutes.

Or if i try to do it inside of windows using the boot helper...it will say that there is an error...permission denied

"IOerror: [errno 13] permission denied

help?

---

### Post by Quackers on 2011-01-28
Have you checked that the downloaded iso is good?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that checks out ok, whilst booting from the cd (or usb) and at the first purple screen, press any key.
After choosing the language you will get a screen with some choices on it. Choose the one which checks the cd for errors.
What graphics card are you using please?

---

### Post by Rubi1200 on 2011-01-29
> **aholm006 said:**
> Hello,
I am trying to install Ubuntu 10 on my presario 2100 and every time i try it fails in some way.

I tried to boot from USB and it acted like it was never there

I created a Ubuntu disc but 1 of two things happens.

When i try to boot it from the disc it will go pass the logo screen and then just freeze after a few minutes.

Or if i try to do it inside of windows using the boot helper...it will say that there is an error...permission denied

"IOerror: [errno 13] permission denied

help?
Hi and welcome to the forums aholm006 :-)

As Quackers mentioned, check the md5sum. 

Also, do you have 4 primary partitions already?

If yes, the install will fail and you need to create space to install Ubuntu.

If possible, post a screenshot from Disk Management of the current state of the disk.

---

### Post by aholm006 on 2011-01-29
ok thanks

---

### Post by aholm006 on 2011-01-29
its says the iso is fine....it just keeps freezing in the installation process..it goes to a purple ish screen and then doesnt do anything...

i cleaned off my computer of windows...so there should be enough space

---

### Post by aholm006 on 2011-02-01
> **Rubi1200 said:**
> Hi and welcome to the forums aholm006 :-)

As Quackers mentioned, check the md5sum. 

Also, do you have 4 primary partitions already?

If yes, the install will fail and you need to create space to install Ubuntu.

If possible, post a screenshot from Disk Management of the current state of the disk.

i tried using an older version of ubuntu....it still will not respond...i tried 7.10..it begins the boot..and then when i start the install nothing happens....

i wiped out the partitions on the drive so there is nothing at all on there...did i mention this was my roommates computer..and she is hassling me to get something up an running..but as of right now..there is nothing on the hard drive?

---

### Post by de_ubntu_master on 2011-02-01
yup if using usb easiest way just formatt the drive use ubb installer look for ur ubuntu edition aka netbook remix and restart with drive in and should go to some screen looking like ubuntu a little and from the just do ya do :) use like a 2 g flash drive but u have to have to format it :P

---

### Post by aholm006 on 2011-02-01
> **de_ubntu_master said:**
> yup if using usb easiest way just formatt the drive use ubb installer look for ur ubuntu edition aka netbook remix and restart with drive in and should go to some screen looking like ubuntu a little and from the just do ya do :) use like a 2 g flash drive but u have to have to format it :P

the laptop doesnt recognized the usb drive for some reason..thats why i used a cd

---

### Post by Rubi1200 on 2011-02-02
Have you made any progress?

As asked, what graphics card do you have?

Try another version like 10.04:
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

Try the alternate CD:
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate)

---

### Post by aholm006 on 2011-02-02
> **Rubi1200 said:**
> Have you made any progress?

As asked, what graphics card do you have?

Try another version like 10.04:
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

Try the alternate CD:
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate)

not sure about the graphics card...

i tried using opensuse..and ubuntu 7.10....nothing helped

---

### Post by arpanaut on 2011-02-02
If these are the specs of the laptop:
[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=125&prodSeriesId=242202&prodTypeId=321957&prodSeriesId=242202&objectID=c00248307](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=125&prodSeriesId=242202&prodTypeId=321957&prodSeriesId=242202&objectID=c00248307)

Then a full blown Install is probably be tricky.
First 256 MB Ram, and then the graphics will be Dodgey too.

You may need to look at some other less spec. demanding distros.
Lots of them out there.

Up the Ram and you may have better luck.

---

