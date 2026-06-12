---
title: "Completed Install but error in loading X windows..... can anyone help?"
date: 2005-08-01
forum: Installation &amp; Upgrades
---

### Post by garthranzz on 2005-08-01
I was able to succesfully install Warthy WarthHog 4.01
but after it loads the GDM it shows an error that it cant load X windows.

I have a Duron 900 Mhz Proc.
              256MB Memory
              ATI 9250 128MB Video Card

I look at the error log and it says
that it cant find Mach64, error loading device/device does not exist.
I think its the videocard. uhm....can anyone help?
Thank you fer readin this far. ---Newbie

---

### Post by heimo on 2005-08-01
Sounds like your X has wrong graphics card driver selected. I haven't used Warty - is there a reason for you to use this older version, instead of Hoary Hedgehog 5.04? I'm not sure, but one of these could probably fix your problem: on console, type 
 ```

sudo dpkg-reconfigure xserver-xfree86 
or 
sudo dpkg-reconfigure xserver-xorg 

``` 
and be sure to select correct video card driver - ati or vesa should work.

---

### Post by az on 2005-08-01
Be sure to do 

sudo /etc/init.d/gdm stop

before you run 

sudo dpkg-reconfigure xserver-xfree86

from the console.  This terminated the X session and allows for better hardware autodetetion.  It would be interesting to know if this bug exists in Hoary, the more recent version of Ubuntu.  Warty uses xfree86 and Hoary uses xorg...

---

