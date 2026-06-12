---
title: "Ubuntu 8.4 won't install from CD"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by jmacg on 2008-07-01
I am a complete Linux newbie who knows his way around Windows but is unable to install Ubuntu 8.04 on a HP Compaq Celeron 2400/512Mb RAM/40Gb HDD that I got as 'bare bones' - no operating system. 
 
Twice now I have downloaded the Ubuntu ISO file and burned the image to a CD. The computer boots up OK with the CD and shows a menu with the option of running from the CD or installing to the hard drive. Neither option works. Both options put a Ubuntu logo on the screen, which goes back and forth for a few minutes, then is replaced by a pageful of error messages that whiz past forever. The messages are similar, though not identical.
 
**One reads:** 
[4415.[next number garbled in the screen photo I took]] SQUASHFS error: sb_bread failed reading block 0x93427
[4415.[next number garbled in the screen photo I took]] SQUASHFS error: unable to read page, block 24cfb209, size [data missing on my photo]
 
**Another reads:**
d, srclength 131072, avail_in 0, avail_out 25887
[362.[next number garbled in the screen photo I took]] SQUASHFS error: sb_bread failed reading block 0x9574d
[362.[next number garbled in the screen photo I took]] SQUASHFS error: unable to read page, block 24cfb209, size d30a
[362.[next number garbled in the screen photo I took]] SQUASHFS error: zlib_inflate returned unexpected result 0xfffffff
 
There shouldn't be any problem with the Ubuntu disk - each time after downloading the ISO image I checked it for integrity twice - after the download (using Ubuntu's checksum method) and after I burned the image (using the test on the menu that comes up when I boot from the disk). One of the options that came up when booting from the Ubuntu disk was a memory test. I ran that, but it was very slow. After a couple of hours it was still going and had done 18 passes with no errors. I killed the test at that stage. I think I can safely say that the computer's memory is OK.
 
Another reason why I think the Ubuntu install CD is OK is that it booted and ran Ubuntu just fine in my laptop. Possible there is a hardware problem in the desktop PC, but I found an old disk with Puppy Linux on it, and that booted just fine and ran Linux.

---

### Post by dominiquec on 2008-07-01
My guess is that you have a problem with your CD-ROM drive, causing it to barf in some areas when reading your CD.

If your ultimate goal is to get Ubuntu installed, you might want to try the MinimalCD version of Ubuntu ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)). Less than 10MB, so if PuppyLinux got through, it should, too.

---

### Post by jmacg on 2008-07-01
Thanks Dominique - I will try that. Hopefully if there is a problem with my DVD drive, it won't affect the Minimal CD I will produce. The annoying thing is that the DVD drive is the one thing in that computer that's brand-new!

Incidentally, is there any reasonably easy way that ISO image can be put on a USB flash drive and installed from that rather than from the DVD drive?

---

### Post by dominiquec on 2008-07-01
Hi, jmac:

Unfortunately, it's not something I've tried before, so I'm not qualified to give an answer on that.  However, this might help: [http://www.pendrivelinux.com/?s=hardy](http://www.pendrivelinux.com/?s=hardy)

---

### Post by wpshooter on 2008-07-01
> **jmacg said:**
> Thanks Dominique - I will try that. Hopefully if there is a problem with my DVD drive, it won't affect the Minimal CD I will produce. The annoying thing is that the DVD drive is the one thing in that computer that's brand-new!

Incidentally, is there any reasonably easy way that ISO image can be put on a USB flash drive and installed from that rather than from the DVD drive?

Have you tried cleaning your CD drive, although you say it is new.

Also, have you checked to see if there is a firmware update available for your CD drive ?

P. S. - Might want to try a different brand of CD, sometimes drives have preferences as to certain brands of CDs.

Good luck.

---

### Post by VMC on 2008-07-01
Reboot from "LiveCD" then use the "media check" feature and see what it says first.

---

### Post by wpshooter on 2008-07-02
> **VMC said:**
> Reboot from "LiveCD" then use the "media check" feature and see what it says first.

I think they said they had already done that.

---

### Post by jmacg on 2008-07-06
> **dominiquec said:**
> My guess is that you have a problem with your CD-ROM drive, causing it to barf in some areas when reading your CD.

If your ultimate goal is to get Ubuntu installed, you might want to try the MinimalCD version of Ubuntu ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)). Less than 10MB, so if PuppyLinux got through, it should, too.
Dominiquec - thanks very much for your suggestion - I was able to get back to that PC last weekend and successfully installed from the minimalCD version. 

John

---

### Post by jmacg on 2008-08-05
Follow-up: though I managed to install Ubuntu using the MinimalCD version, the installation only lasted a couple of weeks before it refused to carry on booting after I typed my password in. I'm not sure I can blame Ubuntu though. Other people in this thread suggested I might have had a faulty DVD drive. I now suspect my original MinimalCD installation was not 100% and contained the seeds of its own demise. I had an old CD drive lying around and I put that in the computer. This time the full installation disk ran perfectly and the computer has been going fine ever since. Long may it continue to do so!

---

### Post by tekorei on 2008-08-23
I think it's a Hardware problem, I got the same SQUASHFS error during my installation, I swapt my DVD-DRIVE and it worked, good luck

---

