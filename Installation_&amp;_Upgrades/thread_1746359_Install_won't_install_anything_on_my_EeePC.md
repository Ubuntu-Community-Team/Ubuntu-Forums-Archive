---
title: "Install won't install anything on my EeePC"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by mordicus123 on 2011-05-01
Hello! :)

I am currently trying to install Xubuntu on my EeePC. 

I created a live-usb using Unetbootin. The USB seems to be working fine, since Windows recognized it as being a Xubuntu install.
I changed my boot priorities so that my USB device comes first.
When I boot, I get this line : SYSLINUX 4.02 debian-20101016 (...) followed by a "_".
And that's it.

What should I do?

The live-usb seems fine, since I get this one line... and it's probably not a problem with the boot order, otherwise it would load something else. I'm really lost, any help would be greatly appreciated!

Edit: problem solved, I formatted the usb device again and it worked! Thanks everyone for the help! :)

---

### Post by mörgæs on 2011-05-01
It can take several minutes to get past this stage. How long did you wait?

---

### Post by mordicus123 on 2011-05-02
I've waited 45 minutes... ](*,)

---

### Post by Dutch70 on 2011-05-02
Check the md5sum of the .iso you created the usb stick from.
[[COLOR="Red"]HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")
Check the cd/usb for defects.
[[COLOR="Red"]CDIntegrityCheck[/COLOR]]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck")

Btw, what are your hardware specs?

And what do you mean *"windows recognized it"*? 
Are you trying to install Ubuntu into windows via Wubi aka windows installer?

---

### Post by mörgæs on 2011-05-02
Good that you got it solved. Please mark the thread solved using 'thread tools'.

---

