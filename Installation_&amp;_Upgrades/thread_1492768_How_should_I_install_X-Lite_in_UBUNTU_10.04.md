---
title: "How should I install X-Lite in UBUNTU 10.04?"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by ShanAJ on 2010-05-25
Is it possible to install X-Lite soft phone in UBUNTU 10.04???
If so how should I do it???
Are there any other alternative softwares in UBUNTU 10.04, like X-Lite???

Thanks.

---

### Post by lechien73 on 2010-05-25
X-Lite 2.0 for Linux is available for free download from CounterPath:
[http://www.counterpath.com/x-lite-download.html](http://www.counterpath.com/x-lite-download.html)

It works fine under 10.04 for me, but I find that the voice quality isn't great. You could try Ekiga instead, which can be installed through Applications -> Ubuntu Software Center.

---

### Post by dzsobacsi on 2010-07-14
I have managed to install X-lite under Ubuntu 10.04.
It is not the most user friendly programme I have ever seen but it works fine with my VoipCheap accout.
That's how I did it:

1./ Download Xlite from here:
[http://www.counterpath.com/x-lite-3.0-for-linux-download.html](http://www.counterpath.com/x-lite-3.0-for-linux-download.html)

2./ Download and install libstdc++5:
[http://packages.ubuntu.com/jaunty/i386/libstdc++5/download](http://packages.ubuntu.com/jaunty/i386/libstdc++5/download)

3./ Unpack Xlite

4./ Execute ./xtensoftphone

5./ To config use this guide
[http://www.voipcheap.com/en/sipp.html](http://www.voipcheap.com/en/sipp.html)

---

### Post by BatteryKing on 2010-08-18
I am running 64-bit Ubuntu 10.04 and these instructions don't work, failing on the libstdc++5 lib.  I installed the 64-bit version of this lib before hand and made sure ia32-libs were installed to no avail.  I found a guide on installing 32-bit libraries on a 64-bit system, but I am already using the 64-bit version of libstdc++5 for a different application and I don't want to create a mess.

Any suggestions for 64-bit installs?

---

### Post by jackdale on 2010-11-09
Just to add to those who suggested ekiga,

I use a virtual machine ruunung trixbox to provide asterix/pbx to my network (bridged) to create a private phone network.

On my mac I use x-lite, but it is buggy  (there is no ekiga for mac)
On my Ubuntu desktop I use Ekiga.

Ekiga is easy to use and can do video.

X-lite is not open-source

Ekiga just works out-of-the-box (32bit or 64bit) and is easy to install from the software centre.

Perhaps the only advantage of x-lite over ekiga is that x-lite is prettier.

---

