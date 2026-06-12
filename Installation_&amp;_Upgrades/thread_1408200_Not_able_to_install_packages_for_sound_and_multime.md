---
title: "Not able to install packages for sound and multimedia"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by samarjeetsaigal on 2010-02-16
I had installed Ubuntu 9.04 yesterday evening and made a dual boot with windows Vista. After installing the Ubuntu i opened update manager and started the updates and after half hour, some of the updates were done but the sound and multimedia package was not installed. Then i played a song and ubuntu asked me to install 2 packages for that and after i made a confirmation to that, it shows that it is unable to install the package.

If anyone could tell me how to install these packages i'll be very thankful to him and so that i could listen some songs while i work on my laptop.

Thanks in Advance
Samarjeet Singh Saigal
Roar the Voice, Save Tigers

---

### Post by Letian on 2010-02-16
try this on command line
$sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly 

if it doesn't work. please post the message you get so we can work from there.

---

### Post by dE_logics on 2010-02-16
See if you have some broken packages installed.

Do - 

> dpkg --configure -a

> apt-get --fix-broken

I've never tired the last one though.

---

