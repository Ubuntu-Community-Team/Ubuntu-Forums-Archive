---
title: "problem installation in 10.10"
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by cs09b016 on 2011-03-26
im unable to install 10.10 on my laptop, all the installation process is  fine but after RESTARTing, terminal opens with sequence of  commands...after that BLACK SCREEN appears   
but everything is fine when i run it from live cd.

in 10.04 and other versions it opens the desktop after restarting but LAN cable and WIRELESS are not detected.

my laptop details
DELL INSPIRON N4010

plz help
:confused::confused::confused:

---

### Post by Hedgehog1 on 2011-03-26
Please read and follow the 'blank screen problems' thread below. 

You will be changing the 'nomodeset' boot parameter.

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

You might need to to enter other boot parameters There are 6 of them. You may have to do them one-by-one until you get video.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)  (Common Kernel Options Section)

***The Hedge***

:KS

---

### Post by mörgæs on 2011-03-26
Actually there are lots and lots of boot parameters, but the 6 mentioned above will most likely solve the problem.

[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by cs09b016 on 2011-03-27
didnt work...........

---

### Post by mörgæs on 2011-03-27
What didn't work? Please post the exact steps you have tried.

---

### Post by cs09b016 on 2011-03-29
[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

i tried the options mentioned in this page.....but the same black screen problem persists after restarting.

plz suggest the sequence of steps to get it right .....

---

### Post by Dutch70 on 2011-03-29
You may need to check the md5sum of your downloaded .iso.
[[COLOR="Blue"]https://help.ubuntu.com/community/HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")

And check the cd.
[[COLOR="Blue"]https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck[/COLOR]]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck")

---

### Post by mörgæs on 2011-03-29
If you can make a successful boot with the live CD, you don't have to test it further. The CD works.

Which boot options did you try?
Did you manage to get one boot working (and only the reboot failing)?

---

