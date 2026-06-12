---
title: "Cannot install Ubuntu 12.04/12.10"
date: 2012-06-01
forum: Installation &amp; Upgrades
---

### Post by eminemix on 2012-06-01
The last version of ubuntu I can install is 10.10.

I've tried installing 12.04 (x32/x64) from usb stick and 12.10 (x32/x64) from DVD (they don't fit in a 700MiB CD).

After i choose on what partition I want to install and click next the screen goes black and i get "Assuming write drive write through".

The DVD stops spinning, everything is stuck.

I'm using MSI EX620 notebook.

Chipset	Intel®PM45+ICH9M
Memory 4GB.
CPU: Core2 Duo P7350.

Any ideas? I know I can install 10.10 and then upgrade to 12.04 but i don't want to do that.

---

### Post by codingman on 2012-06-01
Hello, and welcome to the forums!

I suggest not installing 12.10 right now, it's very unstable and buggy. Are you trying to do dual boot? Give some information on exactly what you did to get to the partition part of the installation, information lways helps the reader ;).

---

### Post by eminemix on 2012-06-01
> **codingman said:**
> Hello, and welcome to the forums!

I suggest not installing 12.10 right now, it's very unstable and buggy. Are you trying to do dual boot? Give some information on exactly what you did to get to the partition part of the installation, information lways helps the reader ;).

Hello,

Thank you for your fast reply. I have a partition of 10GB for linux, and 2GB for swap, everything went fine for the last 5 years.

Yesterday, I lost all hope with Ubuntu and I tried to install linux mint, but i got the same crash (i think it's because linux mint is based on ubuntu?). Fortunately, linux mint is more verbose with errors. Check the photos (Sorry for the bad quality).

I've now figured it out that a second before the crash i get that menu with timezone. (I guess that what's causing this error).

Photo links:
[http://0x0x.info/screenshots/one.jpg](http://0x0x.info/screenshots/one.jpg)
[http://0x0x.info/screenshots/two.jpg](http://0x0x.info/screenshots/two.jpg)

I've posted my problem [here](https://answers.launchpad.net/ubuntu/+source/ubiquity/+question/195961). Seemed like the right place.

---

### Post by dino99 on 2012-06-01
i should set / to 12/15 Gib, 10 is a bit to narrow, and try with boot options

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

often nomodeset or noacpi do the trick

---

### Post by eminemix on 2012-06-01
Thank you for your reply. I did what you said but still no luck (stuck in the same step).

---

### Post by nuttzo31 on 2012-06-02
Have you tried installing using the alternate live cd in text mode?

---

### Post by nuttzo31 on 2012-06-02
Searching on google it seems some people have had success by removing the ubiquity slide show from the livecd before installng, open a terminal and type
sudo apt-get remove ubiquity-slideshow-ubuntu and then try installing again, can't hurt to try

---

