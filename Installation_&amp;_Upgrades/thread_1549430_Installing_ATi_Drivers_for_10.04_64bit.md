---
title: "Installing ATi Drivers for 10.04 64bit"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by Gizmodo on 2010-08-09
So Ive decided to give Ubuntu a shot after many years of being abused by a Window.. Although it looks good so far Ive yet not managed to install drivers for my HD5850.

Whats really stopping my is that I'm reading the instructions and I came across a little "must have" list, here is how it goes..

```
The following packages must be installed in order for the ATI CatalystTM Linux driver to
install and work properly:
    XFree86-Mesa-libGL
    libstdc++
    libgcc
    XFree86-libs
    fontconfig
    freetype
    zlib
    gcc

```Now my question is, how can I reach them? Ive already got the latest ATI Driver and I believe I know how to install it but I dont want to until Ive found a soltion for this little "problem".

All suggestion are welcome!

*** Update ***
Within a minute after posting this, I decided to check out what Ubuntu Software Center had to say about these programs, Ive got all installed except "**xfree86-libs**".

---

### Post by alanwalterthomas on 2010-08-09
Welcome.

The easiest way to have install the ATI driver is through System > Administration > Hardware Drivers. Ubuntu should detect your card, suggest the driver, & you'll have the option to activate it. After you reboot it should work well.

When you need a package just try "sudo apt-get install _____"
Try Applications > Accessories > Terminal & type
sudo apt-get install xfree86-libs
Then type your password.

If you're a little more adventurous & want to make sure you have the most recent driver you can download it from ATI's support website under drivers & follow this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)
(According to the above site there's a new PPA repository where you can get more up-to-date drivers with much less work, I'm looking into it now. [https://launchpad.net/~ubuntu-x-swat](https://launchpad.net/~ubuntu-x-swat))

---

