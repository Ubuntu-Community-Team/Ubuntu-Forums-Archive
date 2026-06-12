---
title: "installing on a Satelite L675"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by pyro.stevenson on 2011-01-30
im trying to use a pen drive to install Ubuntu on my new L675D-7042. i have gone through all the steps on the website to make the bootable jump drive, boot from USB,i get the Ubuntu splash asking if i want to install or run from removable. Now from here is where it gets screwed up, no matter what i choose (either run or install) it runs through some boot script and just stops dead in the middle of it all with the last line of code being ```
[2.308605]NET: REGISTERED PROTOCOL FAMILY 1 
```there it just freezes with a blinking cursor and nothing else happens.

i have tried 2 different versions, Ubuntu. 10.10 and UNR 10.10

any help would be appreciated

---

### Post by pyro.stevenson on 2011-02-01
finally got 10.04 to launch on the LiveCD via pendrive, now im  running into a problem with my wireless card not working and trying to install the Broadcom STA wireless driver crashes when i try to ac activate it, currently im hardwired via an ethernet cable but i havent seen any fixes or ways around this problem yet, so far other then then i think my Fn keys are not working it looks great

---

### Post by OldToker on 2011-02-13
> **pyro.stevenson said:**
> finally got 10.04 to launch on the LiveCD via pendrive, now im  running into a problem with my wireless card not working and trying to install the Broadcom STA wireless driver

Hi I am wondering how you got it to install Exactly...  I have tried CD / DVD / PEN Drive  * No Option * exists for me even using F12 to boot from a pen drive I have Kubuntu 10.10 installed on my pendrive. Was going to attempt to install from the pen, but I can't find an option to boot from it.

As for your Wireless issues.. I have read in other places on the net that it's solved by using the 64bit version of *buntu.

I have a Satellite L675D-S7015  While your machine is different from mine. I believe we are/were having the same boot/install issues.  Thanks for any info you can give :)

Ok Update you need to pass this to get the computer to boot :  acpi=off

---

