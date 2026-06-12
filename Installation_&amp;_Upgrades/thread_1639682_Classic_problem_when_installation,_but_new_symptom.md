---
title: "Classic problem when installation, but new symptoms may."
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by b2ee on 2010-12-07
Hi Guys,

I'm struggling to install Ubuntu 10.04 in a desktop

I believe the problem is related with the graphic card drive or similar since in other laptops and desktops, the installation is ok.

I did search for a while on web and the forum, but couldn't find an answer. Sorry if the problem is duplicate with others. 

The symptom:

When starting with LiveCD, 

First screen =>
I saw a Ubuntu color ( may called African Red) with a small keyboard and little people shape as usual.

Second screen =>
then second screen is "ubuntu" characters in the middle with five loop processing points at below, and then after a while, suddenly the screen became bulk of colors-mixed-points with "ubuntu" characters still at the background, and then stopped for ever.

I ever pushed "Ctrl" once the First screen and I can go into that screen which can let me chose boot parameters. I used "F6" to delete "quiet splash --", and then "Try Ubuntu without installing". And then I can see "No or unsupported WMI interface", and then dropped to the Second screen mentioned above.

I got a similar one at [http://ubuntuforums.org/archive/index.php/t-498725.html](http://ubuntuforums.org/archive/index.php/t-498725.html), but I don't know how to access the command line mentioned in the link ( it said some recover mode, but I couldn't find where it is). 


Any help is appreciated.


B2ee

---

### Post by wilee-nilee on 2010-12-07
From the live cd hold the shift down right after power on, then when you get to the try or install screen hit f6  then nomodeset, ctrl-x to boot.

Also your link is from 2007 not a good reference for you.

---

### Post by b2ee on 2010-12-07
> **wilee-nilee said:**
> From the live cd hold the shift down right  after power on, then when you get to the try or install screen hit f6   then nomodeset, ctrl-x to boot.

Also your link is from 2007 not a good reference for you.

Thanks  for the reply. 

In progressing....

Let you know once done.




b2ee

---

### Post by b2ee on 2010-12-07
Finally I made it.

The graphic driver is the key. 

When Ubuntu(10.04) starts up, 
--> push "shift" down after power on until going into GRUB loader,  and black-white screen of GRUB version will prompt out 
--> chose "recovery mode" 
--> chose "ntroot" to go into the CLI with network enable ( so can  apt-get) 
--> "sudo apt-get gcc build-essential"
--> "sudo apt-get install nvidia-glx-96" ( my VGA card is nVidia NV18  GeF4 MX 4000).
--> then reboot --> it works at my PC.

Thanks everyone.

---

