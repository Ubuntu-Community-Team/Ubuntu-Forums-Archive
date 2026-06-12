---
title: "XCDROAST/DVD/CD Creator"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by jkeelsnc on 2008-04-04
Hello there.  I have an ISO image I want to burn.  I know that the burner works perfectly cause I just used it under windows last night to burn the Ubuntu 7.10 CD.  However, I tried to install XCDRoast to burn another ISO image it has.  Unfortunately, it tells me that the program must be configured in Superuser mode first.  However, Ubuntu does not seem to have allowed me to add a root password which would be the way that I would normally open XCDRoast and configure it.  One other thing, I also tried CD/DVD Creator in Ubuntu which recognizes my CDR140X Sony drive.  However, even though I have a blank disk in the drive, when I try to burn the image it says "please insert blank media" and even after closing out CD/DVD creator and reinserting my BLANK disk it still says that i need to put in blank media so that doesn't seem to be working either.  Any ideas?

---

### Post by Partyboi2 on 2008-04-05
try starting xcdroast from terminal (Applications>Accessories>Terminal)
```
sudo xcdroast
``` The password will be the one you use to login with.
More on sudo [here]("https://help.ubuntu.com/community/RootSudo")
[http://people.brandeis.edu/~kunz/TechTips/xcdroast.html](http://people.brandeis.edu/~kunz/TechTips/xcdroast.html)

---

### Post by jkeelsnc on 2008-04-05
OK, I tried running XCDROAST from the command line as follows

"sudo xcdroast" which then prompts for a password.  I entered my password and I get the following mesages:

"** (xcdroast:5899): WARNING **: No /usr/bin/icedax installed


** (xcdroast:5899): WARNING **: (Invalid lib-directory? Check -l option)"

What does this mean?

Thank you for your help by the way.

---

### Post by jkeelsnc on 2008-04-05
OK now. I installed the ICEDAX package in synaptics.  Now XCDROast runs but it has sat fot the last two hours with the message "starting to scan for devices" and has not finished apparently.  I know that the CDR drive is fine cause it worked under windows perfectly when burning the Ubuntu ISO. :)  Any ideas?

Thanks!

---

### Post by timfelgentreff on 2008-04-20
Try Brasero. X-Cd-Roast has quite a few issues in Ubuntu atm. Brasero is clean and intuitive and has recently become the default Gnome-Burning-Application anyway.

---

### Post by jkeelsnc on 2008-04-23
Never mind now.  I am using K3B which is a nice program and works flawlessly with my CDRW.  I don't like XCDRoast.  It seems to be a buggy bunch of crap. LOL :)

---

