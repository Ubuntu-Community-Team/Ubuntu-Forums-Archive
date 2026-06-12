---
title: "Blank screen on boot"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by woodone on 2011-05-02
Ok  so here's my issue. I am trying to run natty narwhal from a USB drive on a
 Shuttle xpc 
w/ athlon 64 dual core 5400+ 2.80 GHz,
 2G ram,
32-bit Vista home premium
NVIDIA geforce 7025/nforce 630a

I have read all the current threads and am still unable to get to a grub screen and do not know where /how to find and modify the proper files on the key. I believe i need to try nomodeset and or incorporate the nvidia driver package into the setup, however i have very limited command line experience and more desire than ability. Any help would really be appreciated. 
Also I will provide any info you need just not sure what beyond what i gave  

A BIG THANK YOU in advance,  Woodone

---

### Post by Dutch70 on 2011-05-02
Are you talking about a usb stick aka flash/thumb drive? Or an external hard drive? Live version or Install?

What version of Ubuntu...10.10, 10.04, 11.04?

What did you use to put it on the usb?

---

### Post by pac-man on 2011-05-02
I have the same problem, when I boot to the usb key drive, all I got is a message that says: "syslinux 4.03 2010-10-22 EDD copyright (c) 1994-2010 H. Peter Anvin et al."

And that's it, I does nothing else.

I am trying to run kubuntu 11.04 on the usb pendrive, on a Lenovo  ideapad U460 with intel core i5.

Any ideas?

---

### Post by woodone on 2011-05-02
I used the program that came thru the ubuntu download site for windows. i am using a usb key and trying the live ver. 11.04

---

### Post by Dutch70 on 2011-05-02
There are a few things you can try. 

Check the md5sum of the .iso you downloaded.
[URL="https://help.ubuntu.com/community/HowToMD5SUM"]
[COLOR="RoyalBlue"]HowToMD5SUM[/COLOR][/URL]
Check the cd/usb for defects.
[[COLOR="RoyalBlue"]CDIntegrityCheck[/COLOR]]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck")

You can also try creating the usb stick with [[COLOR="RoyalBlue"]Unetbootin[/COLOR]]("http://www.pendrivelinux.com/using-unetbootin-to-create-a-live-usb-linux/") 
That site has the instructions & the download link.

---

### Post by mörgæs on 2011-05-02
Boot options are described here:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by woodone on 2011-05-02
am trying a new iso and unetbootin will update after i try it

---

### Post by woodone on 2011-05-02
Ok I have a good iso which i used to create a live usb key with unetbootin. Still have the same issue, i can hear the system bootinto the desktop but blank screen. When I try to get to boot options using any of the methods previously discussed ( shift, or e key) I do not get these options. I did try using the "tab for options" under run from this disc and editing quiet splash to nosplash text, then i believe i'm still booting, but blank screen. Can i use nomodeset in place of nosplash text or am i on the wrong track

---

### Post by Dutch70 on 2011-05-02
I think you are on the right track. :KS
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

Now let's hope that works.

---

### Post by woodone on 2011-05-02
Well thanks for the help tried nomodeset and was able to get a gui. gonna boot from the live cd/usb key in no modeset if i install will this persist or should i install the nvidia driver before the OS install

---

### Post by Dutch70 on 2011-05-02
The link I gave you tells you how to set it permanently on the install.

---

