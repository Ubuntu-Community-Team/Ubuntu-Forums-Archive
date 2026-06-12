---
title: "Quick coulple of questions"
date: 2005-03-09
forum: Installation &amp; Upgrades
---

### Post by JaZzY JeF on 2005-03-09
Hi,

Just installed Ubuntu.  Figured out how to get my Geforce 6800 GT working by typing the commands below.

sudo apt-get install nvidia-glx

sudo nvidia-glx-config enable

Now, does this download the latest driver from Nvidia?

If not how do I uninstall the drivers?  I want to use the latest drivers.  Whenever I try to install them it says I have to stop using the GUI first.  How do I do that?

Also, how do I mount the other two partitions I have on my hard drive?  The partitions are on the same drive I have Linux installed on.

Thankyou in advance for any help you can provide me

Jef

---

### Post by llama on 2005-03-09
mounting drives is covered in.

[http://ubuntuguide.org/](http://ubuntuguide.org/)

if you are using warty the drivers are version 61.11. the hoary rep's have version 66.29 in which you maybe able to install in warty but i havent tried.

also did you change your XF86Config file to use the nvidia driver? i had to change it manually to get them working.

---

### Post by JaZzY JeF on 2005-03-09
I downloaded warty i think.  Got it from this website.  Where do I get Hoary from?  Is that better?

To get my video card to work I just typed... 

sudo apt-get install nvidia-glx

sudo nvidia-glx-config enable

...at the command prompt.

Cheers,

Jef

---

