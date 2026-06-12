---
title: "Lightscribe on Ubuntu 11.10"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by Oldhacker on 2011-10-16
So far, I have had no problems installing apps that I used on Ubuntu 10.04

However, I downloaded Lightscribe system software and the simple labeler from lightscribe's website and my attempt at installation does not appear to be working as the files are not found. I was using:

sudo dpkg -i --force architecture /home/brooks/Downloads/lightscribeApplications-1.18.15.1-linux-2.6-intel.deb

sudo dpkg -i --force architecture /home/brooks/Downloads/lightscribe-1.18.24.1-linux-2.6-intel.deb

sudo ln -s /usr/lib/lightscribe.so.1 /usr/lib32/

sudo ln -s /usr/lib/lghtscribe.so /usr/lib32/

sudo ldconfig

(That is what worked successfully on my Ubuntu 10.04)

Something has changed in this new edition of Ubuntu???

---

