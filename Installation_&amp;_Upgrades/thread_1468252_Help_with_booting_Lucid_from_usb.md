---
title: "Help with booting Lucid from usb"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by G. Rodrigues on 2010-05-01
Hi all,

A little background first (skip to "Clean install from usb" if not interested): 2 weeks ago I moved from windows to ubuntu 9.10. I could not get win xp to connect to the internet via wireless and windows 7 does not have support for the usb wireless I have, so no internet either. Took the ubuntu 9.10 live CD installed it and lo and behold, internet working right out of the box (and also sound -- on windows I had to do some considerable rummaging through the internet (in another computer) to get the right drivers).

So things were going nice. Or not. My biggest gripe is with LaTeX and LaTeX editing. The TeXlipse plugin for Eclipse is clunky and slow and a couple of features were not working. Gedit + LaTeX plugin misses some important things. TeXworks was troublesome to get running because Karmic comes with Texlive 2007 which has no synctex support, so I had to go hunting for a suitable repo and upgrade it. And then again Texworks lacks some important features. I could go on and on with my testing of various editors, suffice to say that the most promising was Kile - but it was clunky and slow, forward/inverse search was not working with okular, etc.

Clean install from usb: Given the new release of lucid lynx (texlive 2009 for default, forward/inverse dvi search seems to be working with okular, etc.) I thought, what the heck, why not do a clean install and try again with Kile? Since Kile is a KDE app I opted to download Kubuntu. Next I used usb-creator on 1GB usb drive. I went to the BIOS settings and set the booting order as:

USB-HDD, CD-ROM, HDD

Plugged the usb drive, booted and... nothing. Just a black screen with a box of text with some of the characteristics of the computer and the cursor blinking in front of "DDR SDRAM at Bank: 0 1". My suspicion is that this is not a problem of ubuntu per se, but because my computer is old (5, 6 years), booting from the usb may need a little help. Of course, I can still update Ubuntu to Lucid from the internet and then install the kde desktop, but I prefer to do a clean install and start from scratch. So can anyone help me out here?

For the record, I have an AMD 1.5Ghz with 1.5G ram, motherboard VIA-KM266. Feel free to ask any extra details.

Note: I have also tried UNetBootbin instead of the usb-creator which just reinforces my suspicions that this is not an ubuntu problem per se.

---

### Post by razy60 on 2010-05-01
Did you make any other changes in your BIOS, If not revert them back to the way they were, on restart, you should have an option something like F12 to choose a temporary boot device select it insert your usb(or insert it before you start your PC), and select the usb option. 
 Hope this helps

Raz

---

### Post by G. Rodrigues on 2010-05-02
I made no other changes to the BIOS, but none of the F keys worked. Also tried the ESC key but to no avail. I do have the very vague memory that there was a key to bring up such a booting menu, but this is all very hazy. Any ideas? Thanks in advance.

---

### Post by wilee-nilee on 2010-05-02
In the bios of my net book is a turn on or off the f12 prompt for choice of boot. It could be just a bad load to the usb did you delete the usb partition and make a new or reformat before you loaded it. Did you check the md5 sum.

---

### Post by G. Rodrigues on 2010-05-02
Did all the steps mentioned: partitioned the pen drive anew (FAT system), checked the md5 sum of the Kubuntu download, etc. Also rummaged through the BIOS trying to find some kind of option that would allow me to select on the fly a booting device but found nothing. But I am definitely not technically savvy, so take this last sentence with a grain of salt. 

If nothing else works, I will just update ubuntu as normal and work from there. Then when I get my hands on a lucid lynx live CD (have to wait some 6-8 weeks for that), do a clean install.

---

### Post by emarkay on 2010-06-18
See:
[http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/](http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/)
Tests if you can boot from USB

---

### Post by C.S.Cameron on 2010-06-18
With UNetbootin you can choose to install to C:\, (Frugal install), then the next time you boot your computer you get the option to install Ubuntu.

---

