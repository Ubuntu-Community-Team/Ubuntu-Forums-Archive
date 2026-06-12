---
title: "Dual Boot issues Vista &amp; Ubuntu"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by Chrisoldinho on 2008-01-07
Basically everything worked flawlessly when GRUB was installed.

However stupid me decided to put EasyBCD on instead. Vista works fine, but since I don't "really" have any idea about EasyBCD or Linux, when I came to add that I didn't really know what to press other than to select the partition I had installed Linux on.

Now when I select Linux Ubuntu from the boot menu I get an error message stating the OS cannot boot.

I now have 2 options, fix EasyBCD so that Ubuntu does boot (ideal scenario) or use GRUB as that worked to begin with.

If I do go back to GRUB can I just have it show 2 menu options - Vista & Ubuntu (none of this recovery mode or anything like that. I don't want a cluttered boot menu) . And change the default OS to Vista & set a timeout at say 10 seconds.

Thanks, Chris.

---

### Post by forestpixie on 2008-01-07
there  is a ubuntu page somewhere that is an easy easybcd tutorial - but I can't remember where it is - you can search for it here

this might help though [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

### Post by Chrisoldinho on 2008-01-07
I read this:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

As i've only just installed Ubuntu, it might be worth me re-installing it again and following this guide.

Since i'm going to do this, what size would you recommend to set the swap partition to?

I have set the main Ubuntu Partition to be 10GB.

Chris.

---

### Post by forestpixie on 2008-01-07
depends on your ram size and what you're going to use ubuntu for 

I have 1Gb ram and same of swap

---

### Post by Chrisoldinho on 2008-01-07
It's a laptop, Dell Inspiron 1720. Basic specs are as follows:

Intel Core 2 Duo T7500 (2.2Ghz)
2GB DDR2
160GB HDD
NVIDIA GeForece 8600M GT 256MB

This is going to lead onto my next question actually once I have got it all installed and working...

The NVIDIA Drivers. I downloaded them from the NVIDIA web site .run file. When I ran it in a Terminal it says I need to be logged in as Root to install the drivers, but to my knowledge that is disabled by standard.

Is there an easier way to get the latest NVIDIA drivers installed with support for the 8600M GT.

Thanks, Chris.

---

### Post by forestpixie on 2008-01-07
if you're not going to be doing any memory intensive stuff - vidoe editing or running servers I'd go with 512Mb myself as swap, but if you've got room do 1Gb - you can always add or remove later

As far as the video driver goes - I have an old nvidia card so do it through the restricted driver manager - you could try using envy, it's [here]("http://albertomilone.com/nvidia_scripts1.html") - worksd ok in most instances I believe 

and to run the install as root use sudo

hope that helps

don't forget to mark thread when you're happy :)

---

### Post by Chrisoldinho on 2008-01-07
I'll let you know how it goes this evening. Thanks for the help.

---

### Post by Chrisoldinho on 2008-01-08
It's working like a treat **_finally._**

Took 2 installs. But got there in the end. Followed your helpful hints and used EasyBCD to dual boot. I even have Dell Media Direct working as well :)

---

### Post by forestpixie on 2008-01-08
excellent glad you're sorted

---

