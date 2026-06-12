---
title: "Installing program from 'tar.gz' file"
date: 2012-06-21
forum: Installation &amp; Upgrades
---

### Post by gosling1 on 2012-06-21
Ubuntu 12.04

I've downloaded a file:

PolarView-1.9.tar.gz
Unzipped it to:

'bin' folder

that opens to:

help
tides
tz
libcairo.so.w
libpixman-1.so.0
pv-icon,png
polarview
polarView.bin

I want to install this program but haven't the slightest idea how to accomplish this.

Any help will be greatly appreciated.

Thanks,

Mike Robinson

---

### Post by coffeecat on 2012-06-21
You don't install it in the conventional way. You simply run the .bin file. Open a terminal and cd to the bin folder, then:

```
./PolarView.bin 
```

**EDIT**: note the capitalisation. It's "PolarView.bin", not "polarView.bin" as you typed it. Linux is case sensitive and you'll simply get an error if you get the filename wrong.

---

### Post by flemur13013 on 2012-06-21
**"Linux Installation Instructions":**

[http://polarnavy.wordpress.com/2010/01/22/linux-installation-instructions/](http://polarnavy.wordpress.com/2010/01/22/linux-installation-instructions/)

It sounds like to need to add a couple of other things before running.

---

### Post by coffeecat on 2012-06-21
Yep - that's certainly tidier, copying it to /opt, but that still tells you to simply run the PolarView binary once you've done so. It works wherever you put it.

---

### Post by gosling1 on 2012-06-22
Thanks to all for the information. I hope that I'll be able to deal with this now.

Kindest regards,

MikeR

---

