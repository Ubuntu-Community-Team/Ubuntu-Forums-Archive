---
title: "Ubuntu 10.04 Wubi"
date: 2011-08-01
forum: Installation &amp; Upgrades
---

### Post by b1lancer on 2011-08-01
Hello everyone!

I tried installing Ubuntu 10.04 LTS on my girlfriend's lenovo using a live disc. First we tried it out to show her the wireless would work fine (her previous lenovo was not ubuntu friendly at all). She's interested in keeping her windows 7 partition along with the lenovo recovery partition, so I tried doing a dual boot install. I manually moved the cursors setting the disk space on each partition, and we allowed Ubuntu to do the rest. Much to my dismay, the installation failed.

I've done some reading over the internet, and I think in our case it would be best to use a Wubi installation. We're interested in using 10.04, so where can we find a wubi installer of Ubuntu 10.04?

Also, any ideas why the installation might have failed? The iso was downloaded off the ubuntu main site, and we burned it using infrarecorder. 

Thanks all!

---

### Post by bcbc on 2011-08-02
The 10.04 version of wubi.exe is on the CD you burned (desktop cd iso for 10.04). You can also find it here: [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

If you insert the CD while running windows, the wubi menu will appear. Note if the reason your other install failed was due to a bad burn then you shouldn't run wubi.exe from the CD (or even have the CD in the drive).

Wubi.exe will download the desktop cd iso for 10.04 again by default, however as already mentioned it will also check the CD drives - and if that fails, it looks for the ISO in the same folder as wubi.exe. So if you have a good copy, place it in the same folder as wubi.exe and run from there.

---

### Post by b1lancer on 2011-08-02
Sounds great. Thanks for the link.


i was also wondering: isnt there a  way to check the cd to see if it's good? I recall it's one of the options as you load the cd, correct? So I could run that cd check, and if it's good, pop the cd into the cd drive running windows, and go from there?

---

### Post by bcbc on 2011-08-02
> **b1lancer said:**
> Sounds great. Thanks for the link.


i was also wondering: isnt there a  way to check the cd to see if it's good? I recall it's one of the options as you load the cd, correct? So I could run that cd check, and if it's good, pop the cd into the cd drive running windows, and go from there?
You need to press any key as the cd loads - when you see the keyboard icon at the bottom. That will give you the extended menu that includes the 'check cd' option.

---

