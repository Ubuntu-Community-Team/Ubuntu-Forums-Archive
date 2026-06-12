---
title: "Problems booting ubuntu instalation on Toshiba T135-SP2910R"
date: 2011-02-09
forum: Installation &amp; Upgrades
---

### Post by Dynelight on 2011-02-09
Greetings. 
I'm trying to boot my USB drive with an ubuntu instalation so I can upgrade from 10.04 to 10.10 and the USB doesn't seem to want to boot it. 

See attached screen shot for the error I get.

I've tried: 


[LIST]
[*]Both creating the USB boot with unetbootin and the 1-2-3 installer
[*]Redownloading the file
[*]Trying 2 different ubuntu distros (Ubuntu 10.10 desktop and netbook)
[/LIST]
And I can't seem to get past that screen. As soon as I select on install to this hard drive, it freezes there.

Help is greatly appretiated.

---

### Post by dino99 on 2011-02-09
beautiful kernel panic :)

try booting by:

- removing "quiet splash": that let you know what happen while booting

- add either: nomodeset, noacpi, acpi-osi=Linux

---

### Post by Dynelight on 2011-02-09
From the bootdisk I did, I don't think I have the option of adding additional options. Is there anything else I can do?

---

### Post by dino99 on 2011-02-09
> **Dynelight said:**
> How do I remove quiet splash?

if you dont see the brub menu ( which is the default with single OS) then at end of bios booting process, hold "shift" key down. The grub menu appear, select (highlight) the booting line, then hit "E" to edit it, and look at line ending by "quiet splash": its where you make tweaks, then ctrl+x to boot. When you find the good settings then you can make them permanent by editing the grub settings into a terminal:

sudo apt-get install gksu

gksu gedit /etc/default/grub
( make here the same changes done previously)

then:

sudo update-grub

---

### Post by Dynelight on 2011-02-09
Alright. 
I can edit the booting parameters with TAB on this grub version installed on this USB drive. I tried adding the options you suggested and it paniced still.

These are the options that are there: 

>/casper/vmlinuz cdrom-detect/try-usb-true file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz splash --

I tried booting the OS from the pendrive and the same issue happened. The parameters seem to be the same. 

I know something happens when I load the OS, but I can't seem to scroll up to see what happened. Is there a parameter I can add to allow scroll, so I can give you a better input on what is going on?

Thanks a lot!

---

### Post by dino99 on 2011-02-09
some more settings to test: nolapic, noapic, irqpoll

about scrolling i cant see what to do sadly but there are somr threads about T135:

[https://launchpad.net/~toshiba-t100-series](https://launchpad.net/~toshiba-t100-series)

[http://ubuntuforums.org/showthread.php?t=1384420](http://ubuntuforums.org/showthread.php?t=1384420)

and you should use one of the latest kernel:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by Dynelight on 2011-02-09
I downloaded both isos right off the ubuntu site. Those should have the latest kernels. Am I mistaken?

---

### Post by Dynelight on 2011-02-09
dino before we go on I would like to thank you for your time. 

I tried the extra options you have mentioned. They did not work. 

The threads that you have pinpointed to me don't quite seem to address my issue. 

Here's my scenario, a little bit more detailed: I currently have 10.04 sucessfully installed in this computer, along with Win 7. This computer had a water spill, I took it to service and the keyboard works just fine now. The problem is that now, when I use my keyboard on linux, I have an awful latency between keystrokes. 

Since I installed 10.04 a while ago, and I figured a good format could resolve the issue, I figured I could upgrade to 10.10

I used both unetbootin to create a USB disk with Ubuntu Netbook Remix and Ubuntu Desktop (I tried both alternatives) but whatever I do I keep getting that kernel panic. 

I can't seem to scroll thru the log to give you guys a better input on what is going on. 

Any other help or ideas are warmly welcomed and thank you again for your time.

---

### Post by Dynelight on 2011-02-09
So I tried with yet another tool to create the USB bootable (the one included in the ubuntu CD) and still no go...

Whenever I can get my hands on another pen drive I will try.

Any other ideas are more than welcome..

---

### Post by Dynelight on 2011-02-10
Solved it. I resorted into upgrading from 10.04...
The keyboard problem was some accessibly issue that was enabled. 

I'm still baffled as to why I couldn't boot from the USB but oh well...

---

