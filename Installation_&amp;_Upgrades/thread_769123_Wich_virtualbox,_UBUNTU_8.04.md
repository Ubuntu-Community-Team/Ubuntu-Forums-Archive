---
title: "Wich virtualbox, UBUNTU 8.04"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by jicarre on 2008-04-26
Hi everybody,:)


I have just load the new version UBUNTU 8.04  Hardy Heron... Great !

I am asking what the best version VirtualBox and which one is easy to install... I mean with the less risk of bug I do not want disturb again my OS It is so stable now. I have been stukked with my previous UBUNTU 7.04 when I made an update to 7.10 a week ago : Because of that, I lost quite a lot of data. Virtualbox let me use Os Wind*w* XP easily and I wish,it stays like that with the new version.

Thanks for your good advises and curious to collect your experiences:KS

---

### Post by giumbolo on 2008-04-30
jicarre, I've just installed Virtualbox OSE (Open Source edition) which you can install from the Synaptic Package Manager. Under Hardy Heron, I've installed a fresh copy of Windows XP Home.
My first impressions is that it works. One bad point is that I cannot read the usb ports from XP. It seems that there are other versions which can give such a support.
I'm investigating to better understand and will post here my fuuture experiences.

By the way. Under Gutsy (7.10), I had a Virtualbox with XP, USB working, shared folder with the host machine. Everything was perfect. The problem is that I do not remember exactly which version I installed.

Ciao
Elio

---

### Post by zekica on 2008-04-30
You can always install virtualbox (PUEL version), by downloading a .deb package from [VirtualBox's Download Page](http://www.virtualbox.org/wiki/Downloads), and install it by double clicking. I have successfully installed a package for Ubuntu 7.10 on Ubuntu 8.04, and haven't had any problems since.

For USB support, you can follow instructions from: [Ubuntu's wiki for VirtualBox](https://help.ubuntu.com/community/VirtualBox#head-c40d4d80c0cb00351a492592b1ddbfe95f7ee513)

---

### Post by giumbolo on 2008-04-30
Yes, I confirm. I would add that you've to click on Binaries (all platforms) until you get here.
[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI)

download the deb, double click it, and you're done.

---

### Post by kurtfagerburg on 2008-05-02
Hope this is a related question, but it appears the ose version (1.5.6) of virtualbox doesn't support the createrawvmdk internal command needed to create a new virtual machine.  

I've been looking for a couple of days to see if an older version is available somewhere (it appears that it functioned OK in version 1.5.0 from some other forums and how-to's I've been looking at).  Also, I'm running 8.04 (and I love it!) and most of the stuff out there is for 7.10.

Here are some of the sites I've been looking at to figure out how to set up a virtual machine:

[http://ubuntu-tutorials.com/2007/10/12/how-to-install-virtualbox-open-source-edition-on-ubuntu-710/](http://ubuntu-tutorials.com/2007/10/12/how-to-install-virtualbox-open-source-edition-on-ubuntu-710/)

[http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/)

I've also checked the virtualbox downloads site and can't figure out how to enable the needed command.

Can somebody point me in the right direction?  Maybe there's another thread here somewhere that I've just missed.

---

