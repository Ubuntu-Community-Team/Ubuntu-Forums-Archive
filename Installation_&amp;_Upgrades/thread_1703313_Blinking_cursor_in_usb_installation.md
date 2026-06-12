---
title: "Blinking cursor in usb installation"
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by fuzzyangel on 2011-03-09
Hi
I am trying to install any version of ubuntu (I even tried so far another version called jollicloud) but the result is always the same...

The computer is a Dell Mini 9. I have pulled out it's SSD because it has broken.

I managed to install about some months ago an ubuntu netbook version (10.04, not sure) which all worked fine from a 8GB usb stick 
Here are my steps:
1. Download ubuntu either netbook or standard version
2. Make a bootable flash with Unetbootin from ubuntu or other programs from windows
3. Put the flash disk and the second 8GB flash to the dell mini 9
4. Boot Ubuntu live from the first flash (sometimes I think I must put the second flash after the boot so it finds only the live version... If I have put both flashes sometimes it won' t boot)
5. install ubuntu to the other flash (to the 8GB flash drive)
6. reboot

and then...only a blinking cursor is appearing to the top left of the screen with nothing else happening...
Shift does not do anything.
I have some suspicion that there is no Grub at all but I am not sure for this.

I am sure there is a way to make it because I ve done it before, but I don't remeber how!

---

### Post by mörgæs on 2011-03-09
Hi, welcome to the fora.

It sounds like you need to add boot options:
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[http://www.ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://www.ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

---

### Post by fuzzyangel on 2011-03-09
Finally I managed to install the 10.04 netbook version which did install and work flawless...
I noticed that this time after the installation of 10.04 the cursor started blinking a while, then the graphic environment changed to higher resolution, the cursor started ths blinking again for a few seconds and then it started loading.
I didn't have to mess with the suggested options from mörgæs like "nomodeset".
I must say I did not expect to deal with it as I think it has nothing to do with it because as I mentioned I installed it a few months ago without having to do any workaround.

Anyway, I am happy to have it done. 

Mörgæs thanks for your answer, it was a nice time doing some diving in ubuntu's basics...
I will keep hanging around as I really like Ubuntu
:D

---

### Post by mörgæs on 2011-03-09
Good to hear that you got it solved, and that you are planning on staying here. Once you have answered the first questions chances are that you will never stop...

---

