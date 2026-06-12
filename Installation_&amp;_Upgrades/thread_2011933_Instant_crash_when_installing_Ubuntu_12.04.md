---
title: "Instant crash when installing Ubuntu 12.04"
date: 2012-06-28
forum: Installation &amp; Upgrades
---

### Post by ymustuknow on 2012-06-28
Hey all,
  I am hoping someone can help me out with this issue I am having.  I am trying to install Ubuntu 12.04 AMD 64bit (desktop version) on a older dual core HP computer.  A bunch of command line things pop up, but this one is right away and seems to be the issue, I think.

bug unable to handle kernel NULL pointer difference at 0000000000000128

I thought that it maybe still installing so I left it go while at work and it's still stuck on the same screen.  I did try Google and I didn't get anything.  Any ideas?

---

### Post by Lyfang on 2012-06-28
Maybe you can debug to figure out what caused this to happen, however I think your description didn't include enough information. Have you tried to use only one core of your multi-core CPU? Have you tried to boot into the Live mode? Tried an Ubuntu 12.04 LTS 32 bit installation?

---

### Post by sanderj on 2012-06-28
... and: 

try another CD with the same OS
try a CD with an older Ubuntu, preferably 32-bit. (Are you sure your system is 64-bit?)
run memtest to see if your system is 100% OK.

---

### Post by ymustuknow on 2012-06-28
> **Lyfang said:**
> Maybe you can debug to figure out what caused this to happen, however I think your description didn't include enough information. Have you tried to use only one core of your multi-core CPU? Have you tried to boot into the Live mode? Tried an Ubuntu 12.04 LTS 32 bit installation?

How do I try to debug?  I haven't installed a Ubuntu OS in a long time and don't know much about it Linux at all.

I don't know how to only use one of the two cores.

I did boot to the GUI, is this what you mean by Live mode?

I haven't tried the 32 bit version yet, but am on it.

> **sanderj said:**
> ... and: 

try another CD with the same OS
try a CD with an older Ubuntu, preferably 32-bit. (Are you sure your system is 64-bit?)
run memtest to see if your system is 100% OK.

I will try reburn the 64bit and then if that doesn't work I will try the 32bit.  

I will try another version of the OS.

Yup, 64bit processor.

How do I run memtest?  Do I need to be in this "Live mode"?


I will try to find info on all this, but if you know what I could do to do, please grace me with your knowledge.  :)

---

### Post by dino99 on 2012-06-28
how i'm doing installation:
[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

and remember that "burning" is best at the lowest speed. But its easier to use unetbootin if you can boot on usb (see bios choice)

---

### Post by ymustuknow on 2012-06-28
> **dino99 said:**
> how i'm doing installation:
[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

and remember that "burning" is best at the lowest speed. But its easier to use unetbootin if you can boot on usb (see bios choice)

So I should try the non-GUI install, ok.

Yea, my burner, for cds, only slows down to 16X. I used it assuming since Windows (Vista and 7) needs to be burnt at super slow speeds, so I applied it to this.  Not sure if 16X is slow enough?

I will check my BIOs and see if I can boot to USB

---

### Post by nipunshakya on 2012-06-28
^^^ Mate, first thing you need to do when u burn a ubuntu cd is that you run it in live mode. Running in live mode means making your computer boot from the ubuntu's cd.
Next thing is, during that live cd boot process, as soon as the keyboard and human logo appears on bottom screen, press any key, select the language and you will be presented with options like check disk for errors, try without installing ,etc. SElect the 'check disk for errors' and it will check for any errors in your cd and report you back. if you have errors,download another iso and burn another disk again. If not, restart to the live mode, boot from the cd atleast once selecting 'try without installing' and then see if your machine is ready to accept the ubuntu. 
Only after that you are ready to install ubuntu in your machine with less pain in your head...


Goodluck

---

### Post by Lyfang on 2012-06-28
> **ymustuknow said:**
> How do I try to debug?  I haven't installed a Ubuntu OS in a long time and don't know much about it Linux at all.

I don't know how to only use one of the two cores.

I did boot to the GUI, is this what you mean by Live mode?

I haven't tried the 32 bit version yet, but am on it.



I will try reburn the 64bit and then if that doesn't work I will try the 32bit.  

I will try another version of the OS.

Yup, 64bit processor.

How do I run memtest?  Do I need to be in this "Live mode"?


I will try to find info on all this, but if you know what I could do to do, please grace me with your knowledge.  :)

I think debugging could be done if you are able to boot a Live Session.

CPU multi-core settings found in BIOS.

Yes GUI Live mode. "Live mode is the default option when booting from CD." [https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

If you have more than 4 GB of RAM, install the 32 bit PAE kernel.

Try to verify data integrity after you have burned the CD. [https://help.ubuntu.com/community/HowToMD5SUM/](https://help.ubuntu.com/community/HowToMD5SUM/)

I suggest trying Debian "stable". [http://www.debian.org/CD/http-ftp/](http://www.debian.org/CD/http-ftp/)

Test Your Computer’s Memory For Errors with Memtest [http://www.makeuseof.com/tag/memtest-awesome-tool-test-computers-memory-errors/](http://www.makeuseof.com/tag/memtest-awesome-tool-test-computers-memory-errors/)

The Ubuntu Alternate CD ISO installation works better on low-memory systems.

---

### Post by ymustuknow on 2012-06-28
> **Lyfang said:**
> I think debugging could be done if you are able to boot a Live Session.

CPU multi-core settings found in BIOS.

Yes GUI Live mode. "Live mode is the default option when booting from CD." [https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

If you have more than 4 GB of RAM, install the 32 bit PAE kernel.

Try to verify data integrity after you have burned the CD. [https://help.ubuntu.com/community/HowToMD5SUM/](https://help.ubuntu.com/community/HowToMD5SUM/)

I suggest trying Debian "stable". [http://www.debian.org/CD/http-ftp/](http://www.debian.org/CD/http-ftp/)

Test Your Computer’s Memory For Errors with Memtest [http://www.makeuseof.com/tag/memtest-awesome-tool-test-computers-memory-errors/](http://www.makeuseof.com/tag/memtest-awesome-tool-test-computers-memory-errors/)

The Ubuntu Alternate CD ISO installation works better on low-memory systems.

Great stuff, thanks!

---

### Post by ymustuknow on 2012-06-28
I have now tried the USB way of installing both 32 and 64 bit 12.04 and the 32 bit 11.10, all failed. :-k

---

### Post by nipunshakya on 2012-06-28
> **ymustuknow said:**
> I have now tried the USB way of installing both 32 and 64 bit 12.04 and the 32 bit 11.10, all failed. :-k
While trying to install all those flavours, do u get the same kind of error messages?? or are they different....?? Have you tried 10.04?? maybe your computer is old to support latest releases??

---

### Post by Lyfang on 2012-06-29
> **ymustuknow said:**
> Great stuff, thanks!
You're welcome!

> **ymustuknow said:**
> I have now tried the USB way of installing both 32 and 64 bit 12.04 and the 32 bit 11.10, all failed. :-k

I suggest to try Debian GNU/Linux 6.0 "stable". You can use UNetbootin to make a Live USB flash drive, without having to burn a CD. Download the latest release (6.0.5), CD 1, it should be enough to start with. The most popular packages are found on CD 1. [http://cdimage.debian.org/debian-cd/](http://cdimage.debian.org/debian-cd/) /i386/iso-cd/

---

### Post by ymustuknow on 2012-07-01
> **WinuxUser said:**
> While trying to install all those flavours, do u get the same kind of error messages?? or are they different....?? Have you tried 10.04?? maybe your computer is old to support latest releases??

It would didn't give a reason that I recall.  I just will load Windows XP on it.  **I totally appreciate everyone's help**, I just don't have the time right now to spend on it, especially since it is an old computer.
:KS :D

---

### Post by nipunshakya on 2012-07-01
> **ymustuknow said:**
>  especially since it is an old computer.
:KS :D


That might be a reason... :D

---

