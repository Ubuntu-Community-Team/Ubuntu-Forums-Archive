---
title: "usb install error"
date: 2014-11-14
forum: Installation &amp; Upgrades
---

### Post by uncleguido on 2014-11-14
I'm trying to install kubuntu 14.10 kde plasma 5 from a usb stick and keep getting this error:

Starting uuid generator uuidd /etc/rc2.d/S02sddm: 4 ,: Can't open /lib/init/init-d-script saned disabled; edit /etc/default/saned

It works fine with 14.04.

I've tried unetbootin, startup disk and the dd command prompt with no success.

Any help will be appriciated.

PS: I've search the web for days now and couldn't find anything on how to resolve this error.

---

### Post by ubfan1 on 2014-11-14
Did you hashcheck the downloaded iso?  I'm not sure what a media check on the USB would do, but it couldn't hurt either.

---

### Post by uncleguido on 2014-11-14
Yes, I've checked the hashcheck and did a media check and all were ok.

---

### Post by pawelg2 on 2014-11-25
I got the same problem
Image sha256 were ok.

Tested with kubuntu-plasma5-14.10-desktop-i386.iso
on Asus Z53Series and Asus EeePC 901

and Kingston DataTraveler 2GB

First i used UnetbootIn and the same error on both laptops

Next try with usb-creator-kde 
-> error uuid generator uuidd /etc/rc2.d/S02sddm ... on Asus Z53Series
but on EeePC 901 after other error : gfxboot.C32 not a COM32R image
system started live session

---

### Post by sudodus on 2014-11-25
> **pawelg2 said:**
> I got the same problem
Image sha256 were ok.

Tested with kubuntu-plasma5-14.10-desktop-i386.iso
on Asus Z53Series and Asus EeePC 901

and Kingston DataTraveler 2GB

First i used UnetbootIn and the same error on both laptops

Next try with usb-creator-kde 
-> error uuid generator uuidd /etc/rc2.d/S02sddm ... on Asus Z53Series
but on EeePC 901 after other error : gfxboot.C32 not a COM32R image
system started live session

This error

```
gfxboot.C32 not a COM32R image
```

is due to the following bug [https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801)

Today ***Unetbootin*** works for me, as well as ***mkusb*** and ***Win32 Disk Imager***.

See this link [https://help.ubuntu.com/community/Installation/FromUSBStick#Known_Issues](https://help.ubuntu.com/community/Installation/FromUSBStick#Known_Issues)

-o-

I don't know about the error in the opening post:

 ```
Starting uuid generator uuidd /etc/rc2.d/S02sddm: 4 ,: Can't open  /lib/init/init-d-script saned disabled; edit /etc/default/saned
```

Please describe when in the booting process that it appears!

---

### Post by pawelg2 on 2014-11-25
> **sudodus said:**
> This error

 ```
Starting uuid generator uuidd /etc/rc2.d/S02sddm: 4 ,: Can't open  /lib/init/init-d-script saned disabled; edit /etc/default/saned
```

Please describe when in the booting process that it appears!

It's after 
#restoring resolver state

I looked into /var/logs/ but found no other details

Visually it's just before login screen, on my ASUS EeePc after few seconds login screen shows up and i can log in and system starts
but on Z53 it freezes

I have found temporary solution in this tread
[https://www.kubuntuforums.net/showthread.php?66855-error-when-installing-from-usb-stick](https://www.kubuntuforums.net/showthread.php?66855-error-when-installing-from-usb-stick)
> 
When the error appears go to a TTY(Ctrl + Alt + F1) and run the next command
sudo killall Xorg
Then press Ctrl + Alt + F7(Return to X) / in my case it's not necessary
 
Then login screen shows up and system starts

---

### Post by udippel on 2015-03-07
> **pawelg2 said:**
> 
I have found temporary solution in this tread
[https://www.kubuntuforums.net/showthread.php?66855-error-when-installing-from-usb-stick](https://www.kubuntuforums.net/showthread.php?66855-error-when-installing-from-usb-stick)

Then login screen shows up and system starts

Lucky you. Here any other terminal is plain black. 
My machine is a lenovo T400 with 4 GB of RAM (someone spoke about too little RAM).

What else could I do to experience Plasma 5?

---

