---
title: "Selection screen hangs"
date: 2015-07-11
forum: Installation &amp; Upgrades
---

### Post by Andrew_Herrera on 2015-07-11
Hi guys, I'm trying to install Lubuntu.  Here are the steps I took in order after I burnt the ISO to my CD. 
1. Turned on my computer 
2. Displays "starting bootlogo" 
3. Chose English as my language
4. Selection screen comes up showing "Try Lubuntu without installing", "Install Lubuntu ", " Check disk for defects",  "Test memory",  and "Boot from first hard disk". 
5. Chose the first option. 
6. Computer starts making noise for a while then does little to nothing. 
Selection screen is still showing after about 30 minutes with no progress. The indicator light is off, but the CD is still appearing to spinning. Essentially I'm hung. Is there a way I could fix this? So far, I'll try reformatting and burning the ISO. 
Thanks!

---

### Post by Bashing-om on 2015-07-11
Andrew_Herrera; Hi !

I personally do prefer (l)ubuntu for older hardware on the desktop.
However, (l)ubuntu no longer fits on a 'CD' , do you mean that you burned to a DVD ?
And also did you:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

Once these checks are done, then we look at hardware compatibility issues (nomodeset boot parameter ?) .

I assure you
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by Andrew_Herrera on 2015-07-11
Hi, 
Oh what I did was use a CD-RW and burned using ImgBurn. Was that the wrong thing to do there?
BTW: I checked the md5 checksum and they matched

---

### Post by Bashing-om on 2015-07-11
Andrew_Herrera; Hey !

Nope, Last I checked ( yeah I did the same same burning to a CD ) the burned image is 6 bytes to large to fit. A CD is 700MB capacity, just a tad too small.

[INDENT][INDENT]been there, done the same
[/INDENT][/INDENT]

---

### Post by Andrew_Herrera on 2015-07-11
Okay thanks man!  Will have to get a DVD tomorrow. Cheers!

---

### Post by ajgreeny on 2015-07-11
Or use a USB if you have one.

It will install quicker and is a more worthwhile way to test the live system before you install at a much faster speed than a live DVD.

---

### Post by Andrew_Herrera on 2015-07-11
I actually do have a couple lying around. Might try my luck there. Thanks

---

### Post by Andrew_Herrera on 2015-07-11
Got it to work on my USB via Rufus, and after a quick workaround using PloP Boot Manager, Lubuntu is up and running! Fantastic! Thanks guys.

---

### Post by Bashing-om on 2015-07-11
Andrew_Herrera; Outstanding !

You do good work ->

[INDENT][INDENT]let the good times roll
[/INDENT][/INDENT]

---

