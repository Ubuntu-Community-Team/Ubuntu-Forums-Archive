---
title: "does the inspiron 1525 work with the new 10.4 LTS"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by Anditsu on 2010-08-18
I have reviewed the latest release from Ubuntu and have decided to try and upgrade to 10.4 from 8.04. In honoring the ancient tradition of common sense I began to plan for the upcoming changes to the system. In order to do this I need to know a few things. First I need to format a drive to back up the system awaiting to be upgraded,but am unsure about the file system employed by Ubuntu; I assume it's ext3. Of course, the next big question is hardware compatibility. Will my current system run the new 10.4 LTS? I've checked with the HCL and the Inspiron 1525 is not listed as certified by the developers. How could this be? After all, I did buy it with 8.4 pre-installed from. It's madness to think they would have trouble supporting it! Has anyone tryed to install 10.4 on an inspiron 1525 box? If so what was the outcome?  

Anditsu

[http://webapps.ubuntu.com/certification/make/Dell/laptops/](http://webapps.ubuntu.com/certification/make/Dell/laptops/)

---

### Post by the.scarecrow on 2010-08-18
I have a Dell Inspiron 1750 that is about 3 month old now and I duel boot 10.04 and Windows 7. Ubuntu 10.04 works perfectly on my computer using the 64bit version. The only difficulty was the need to install the Broadcom driver for WiFi to work.

That said, the hardware in your 1525 could differ considerably and you talk about upgrading from 8.04 to 10.04. I always make complete backups and do a complete fresh install rather than upgrade.

You will be moving from ext3 to ext4 which is a significant change.

First burn a bootable CD or make a bootable USB and thoroughly test 10.04 on your PC prior to attempting to do an install. (I prefer a bootable 4GB USB with a persistance file that will allow you to make and keep some configuration changes for testing but don't attempt to do the upgrades as this will be too much for your USB)



Only upgrade after any issues using your bootable USB have been resolved.

---

### Post by dFlyer on 2010-08-18
I have a Dell Studio 1735. Everything works great with 10.04. I would recommend before your upgrade to backup all your data files. I would also use the Dell-Recovery-Media Creator to create the Dell Ubuntu Install Recovery partition. It will also install most dell software (WiFi, Nvidia etc drivers). The below link will explain how to make the recovery media.

[http://en.community.dell.com/dell-blogs/Direct2Dell/b/direct2dell/archive/2009/11/09/dell-recovery-tool-enhancements.aspx](http://en.community.dell.com/dell-blogs/Direct2Dell/b/direct2dell/archive/2009/11/09/dell-recovery-tool-enhancements.aspx)

---

### Post by Trinity33 on 2010-08-18
> **Anditsu said:**
> I have reviewed the latest release from Ubuntu and have decided to try and upgrade to 10.4 from 8.04. In honoring the ancient tradition of common sense I began to plan for the upcoming changes to the system. In order to do this I need to know a few things. First I need to format a drive to back up the system awaiting to be upgraded,but am unsure about the file system employed by Ubuntu; I assume it's ext3. Of course, the next big question is hardware compatibility. Will my current system run the new 10.4 LTS? I've checked with the HCL and the Inspiron 1525 is not listed as certified by the developers. How could this be? After all, I did buy it with 8.4 pre-installed from. It's madness to think they would have trouble supporting it! Has anyone tryed to install 10.4 on an inspiron 1525 box? If so what was the outcome?  

Anditsu

[http://webapps.ubuntu.com/certification/make/Dell/laptops/](http://webapps.ubuntu.com/certification/make/Dell/laptops/)

i had two acers one dont remeber the version but it was old i think i bought it about 4 years ago and i installed 10.04 and its working not with compiz etc but it does the other latop i have i acer 5735 newer model and the same lucid is working perfect on it 

my last laptop i have is msi gt725 and that one i had really a lot of trouble do you know why? cuz the more advanced devices cpu ddr3 ati 4850 hdmi and intel sound u got the more problems u will experience getting everything working properly i learned that ubuntu run a way better on older computer.

---

### Post by Anditsu on 2010-08-21
> **the.scarecrow said:**
> I have a Dell Inspiron 1750 that is about 3 month old now and I duel boot 10.04 and Windows 7. Ubuntu 10.04 works perfectly on my computer using the 64bit version. The only difficulty was the need to install the Broadcom driver for WiFi to work.

That said, the hardware in your 1525 could differ considerably and you talk about upgrading from 8.04 to 10.04. I always make complete backups and do a complete fresh install rather than upgrade.

You will be moving from ext3 to ext4 which is a significant change.

First burn a bootable CD or make a bootable USB and thoroughly test 10.04 on your PC prior to attempting to do an install. (I prefer a bootable 4GB USB with a persistance file that will allow you to make and keep some configuration changes for testing but don't attempt to do the upgrades as this will be too much for your USB)



Only upgrade after any issues using your bootable USB have been resolved.



I have made a bootable CD-R and after the boot up, I got an I/0 error. I have sent for offical copy from Ubuntu, to rule any problems that might have come from a bad disk or me making it wrong. Do you have any other ideas.

---

### Post by the.scarecrow on 2010-08-22
I prefer to use a bootable USB but thats not so easy to create if you don't have a working Linux installation to make it with. I can't remember if 8.04 had the "Startup Disk Creator" to make a USB from your downloaded .ISO.

You need to download the x386 desktop version then make an image copy to a blank CD. Making a good IMAGE copy can be difficult I find using cheap budget CDs best and burn the image as slowly as possible.

A couple of tips:-
First verify your .ISO using the md5sum check.
Verify your CD after burning it using the option on the CD.

Then it should boot okay use "Try Ubuntu without installing it"

---

