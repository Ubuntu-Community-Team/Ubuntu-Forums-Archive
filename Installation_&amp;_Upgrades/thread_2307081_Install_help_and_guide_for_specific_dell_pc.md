---
title: "Install help and guide for specific dell pc"
date: 2015-12-21
forum: Installation &amp; Upgrades
---

### Post by Paul_Noonan on 2015-12-21
Hi I'm new to Ubuntu but very excited to be apart of this community and help develop Ubuntu. I'm currently delve loping my own skills in graphic design and would love to help create anything that will help. Basically on all hands on deck and ready to make Ubuntu. Currently fighting cancer so I do have a lot of things im going thru but want to spend my way to much free time In making Ubuntu. The next greatest thing which I think it's right there.anyways to the point at hand. 

so I currently own two computers one is brand new Mac 5k with rentina display
the other is a Dell Inspiron 14z 5423

i would like to install Ubuntu on the Dell Inspiron 14z 5423

i just recently bought a new hard drive for set Dell so basically need help with where to even start.


the specs on the 14z 5423 that I own(there 5 different ones I feel like)

the specs: 
I-5 1337u
6gb of ram
500gb hard 3.0 sata drive
32gb ssd
there computer is working fine other than just getting a news harddrive which is the exact same one as the one stated above.

Im sick of Windows don't not don't not want a dual boot for this laptop.
so basically I need a guide that tell me what to do on Mac to get everything ready for me then to power on my Dell and make Ubuntu run. If there's anything I didn't answer please ask away.

thanks for stopping by

---

### Post by Bucky Ball on 2015-12-21
*Thread moved to **Installation & Upgrades**.*

Welcome. Just wondering where the Mac comes into all this. You have no OS on the Dell?

If that's the case, you can create a bootable DVD or USB on the Mac just fine then boot from that on the Dell.

First download the [Ubuntu ISO from here]("http://www.ubuntu.com/download/desktop"). 14.04 LTS is a good place to start. 

Use something like [UNetbootin]("www.unetbootin.sourceforge.net") or [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") to make the bootable USB or burn the Ubuntu ISO image to a DVD with whatever you use in Mac to do that. 

When you're done, boot to the install media on the Dell. You will get a list of options. Best to choose 'Try Ubuntu' which will take you to a 'live' session where you can take a test drive and install from there if all good.

You might not like Ubuntu. There are other flavours of Ubuntu that a worth a look if you don't. Xubuntu, Lubuntu, Ubuntu Mate, Kubuntu, and more, are all options. All look different and one of those may suit your needs better.

Note: If there is an OS on the Dell, then all of the above applies, exactly the same procedure. Other thing is to double check that UUInstaller works on Mac.  UNetbootin does (but make sure you download the Mac version, top right button on the link I gave).

Here's links to Xubuntu and Lubuntu respectively if you want to experiment a little:

[http://xubuntu.org/](http://xubuntu.org/)

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

So, to sum up, there is nothing you need to do to the Mac. Just download UNetbootin, the Ubuntu (or another flavour) ISO, plug in a blank USB (you should wipe it and format to FAT32 prior to creating the Ubuntu installer), run UNetbootin and point it to the Ubuntu ISO. Hit 'Burn' and wait till it's cooked.

Switch off the Dell, plug in the newly minted USB, boot to the BIOS or list of boot devices, choose the USB and you're, hopefully, off and racing! :)

Good luck and just ask if/when you hit a brick wall. :)

---

