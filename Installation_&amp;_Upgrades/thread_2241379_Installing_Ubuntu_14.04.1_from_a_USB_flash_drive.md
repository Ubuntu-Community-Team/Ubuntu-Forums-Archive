---
title: "Installing Ubuntu 14.04.1 from a USB flash drive"
date: 2014-08-25
forum: Installation &amp; Upgrades
---

### Post by AleksaK on 2014-08-25
So I followed a youtube tutorial on how to install Ubuntu alongside Windows 8.1. Basically I downloaded the .iso file from your website, used Universal USB installer to extract it, or whatever, to the USB drive (which was formatted). Then I restarted, entered BIOS, changed boot order so that usb drive goes first. Then I got this screen (yes, I took them all with my phone, couldn't find any other way):
_ -- attachment 1_
If you can't see the first option, it says 'Try Ubuntu without installing. Now there are two scenarios. The first one is when I press 'Try without installing', it does what it says it does, takes me to some kind of preview version, I can access some features. But when I press Install Ubuntu, instead of taking me to the installation process (like the one I've seen in the tutorial), it takes me to...well this:
[-]("http://i58.tinypic.com/2096jyb.jpg")- attachment 2
It differs a lot from what I get in the Try version, because I can't actually do anything. No side bar, no nothing, just those couple of buttons in top right which can't really do much. So I'm wondering why can't I get to the normal installation wizard?
Any ideas?
Thanks in advance!

---

### Post by kansasnoob on 2014-08-25
I only get an Error: 403 when I try to view those pics.

---

### Post by AleksaK on 2014-08-26
Sorry about that, fixed it!
EDIT: This is really weird. Where ever I upload the first image it won't let me access it from here...
EDIT2: I attached it...

---

### Post by kansasnoob on 2014-08-27
I suspect a bad live USB, but let's check. When you first boot the live image you should enter the advanced boot options - be sure to run Check disc for defects:

[https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)

There are links on this page showing how to create a live USB from various OS's:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

There's a review of Try Ubuntu here:

[http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install](http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install)

And Install here:

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

Since you plan to dual-boot with Windows please beware of this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

