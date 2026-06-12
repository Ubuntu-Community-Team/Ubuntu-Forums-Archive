---
title: "Retina MacBook 13.04 install to USB, please help"
date: 2013-02-03
forum: Installation &amp; Upgrades
---

### Post by dk1990 on 2013-02-03
Hi everyone, I am new to the forum, I searched the forum and can't really find what I'm looking for.

I currently have dual boot Win 7 and OSX

I am trying to install 13.04 Amd64 mac daily to a USB 3.0 drive (not from, but to)

I made a bootable liveCD with Pendrive Linux tool in win 7.
When I restart holding option key, boot from USB, get into liveCD, run install, use my whole 32GB drive as the destination and pick Erase before install. (Drive previously preformatted with OSX to GUID table)

When I restart with option key and select USB, it just boots me to windows partition.

I started from scratch again, and followed this guide:
[http://linuxmacbookproretina.blogspot.com.au/2012/12/ubuntu-1304-daily-build-macbook-pro.html](http://linuxmacbookproretina.blogspot.com.au/2012/12/ubuntu-1304-daily-build-macbook-pro.html)
I was stuck at step 3, I couldn't find where to copy files/ link UUID to.

When I boot with rEFInd installed, I show 2 linux boot options (LiveCD drive is now out, so its doubled from one drive) and on both i keep getting initrd fails and screen is just left at that, (says type help for command list)

Can anyone please help?

I would prefer to have only Intel video card on, not nVidia, but it's not a big deal, my main concern is finally booting full ubuntu from external

---

### Post by nsicad on 2013-02-11
> **dk1990 said:**
> Hi everyone, I am new to the forum, I searched the forum and can't really find what I'm looking for.

I currently have dual boot Win 7 and OSX

I am trying to install 13.04 Amd64 mac daily to a USB 3.0 drive (not from, but to)

I made a bootable liveCD with Pendrive Linux tool in win 7.
When I restart holding option key, boot from USB, get into liveCD, run install, use my whole 32GB drive as the destination and pick Erase before install. (Drive previously preformatted with OSX to GUID table)

When I restart with option key and select USB, it just boots me to windows partition.

I started from scratch again, and followed this guide:
[http://linuxmacbookproretina.blogspot.com.au/2012/12/ubuntu-1304-daily-build-macbook-pro.html](http://linuxmacbookproretina.blogspot.com.au/2012/12/ubuntu-1304-daily-build-macbook-pro.html)
I was stuck at step 3, I couldn't find where to copy files/ link UUID to.

When I boot with rEFInd installed, I show 2 linux boot options (LiveCD drive is now out, so its doubled from one drive) and on both i keep getting initrd fails and screen is just left at that, (says type help for command list)

Can anyone please help?

I would prefer to have only Intel video card on, not nVidia, but it's not a big deal, my main concern is finally booting full ubuntu from external

I am also the same situation. i.e. installing ubuntu 13.04 into usb external drive with no success. 

I suggest run first ubuntu 13.04 using usb pendrive before trying before installing into your usb 32 drive or hard drive.

This guide (below) has little use in installing ubuntu in external drive (i.e. not about external drive installation all).

[http://linuxmacbookproretina.blogspot.com.au/2012/12/ubuntu-1304-daily-build-macbook-pro.html](http://linuxmacbookproretina.blogspot.com.au/2012/12/ubuntu-1304-daily-build-macbook-pro.html)

This guide (below) might help you.

[http://velenux.wordpress.com/2012/07/12/grub-failing-to-install-on-debianubuntu-with-gpt-partitions/](http://velenux.wordpress.com/2012/07/12/grub-failing-to-install-on-debianubuntu-with-gpt-partitions/)

Anybody in this forum manage to install 13.04 in external usb drive in windows system in laptop or desktop?

Edit:

Now, I managed to run ubuntu in external drive using the link (above) and this link below.

[https://help.ubuntu.com/community/Grub2/Installing#ChRoot](https://help.ubuntu.com/community/Grub2/Installing#ChRoot)

---

### Post by Umbra Diaboli on 2013-02-13
This process worked for me a couple of weeks ago on Windows:

[LIST=1]
[*]Download Ubuntu 13.04 64-bit Mac.

[*]Rename the image to: ubuntu-12.10-desktop-amd64.iso

[*]Download the USB installer: [http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

[*]Choose Ubuntu 12.10 Desktop from the drop down list - then choose the location of your USB and create.
[/LIST]

You are fooling this program into installing Ubuntu 13.04 in the USB.

Sadly I dont know how to do this on a Mac.

Edit: I forgot to mention, I use a 15" rMBP, I have a separate partition with Windows 7 installed.

---

