---
title: "Upgrade Ubuntu 8.04 to 10.04, fglrx problem?"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by Crash Dummy Dave on 2010-07-06
I am trying to upgrade from Hardy to Lucid. During the upgrade I got the following message:

"This computer is currently using the AMD 'fglrx' graphics driver. No version of this driver is available that works with your hardware in Ubuntu 10.04 LTS."

That made me choose to quit the upgrade, because I demand the same flawless video I have in Hardy. Previously a friend had brought his flash drive with the live CD on it and booted my computer from that without installing it, as a trial. The video seemed to work, but I did not have game or video applications to test the video well.

Obviously something worked to let my ATI radeon xpress 200 graphics onboard chip to work without installing any additional video driver. So, what happens with an **upgrade** to Lucid? Will the fglrx driver just disappear and be replaced with whatever Lucid now supplies, or do I need to take extra steps? I do not want Lucid badly enough to have a messed up computer.

---

### Post by mörgæs on 2010-07-07
Which screen card do you have? Please post the output of 

```
hwinfo --gfx
```

---

### Post by Crash Dummy Dave on 2010-07-08
Thanks for replying. Here is the output you requested:

12: PCI 105.0: 0300 VGA compatible controller (VGA)             
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1002_5954
  Unique ID: ul7N.QHCb6UE_i0B
  Parent ID: vSkL.dQFUNbiC_g9
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:05.0
  SysFS BusID: 0000:01:05.0
  Hardware Class: graphics card
  Model: "Hewlett-Packard Company Radeon XPRESS 200 5954 (PCIE)"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x5954 "Radeon XPRESS 200 5954 (PCIE)"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x2a26 
  Driver: "fglrx_pci"
  Driver Modules: "fglrx"
  Memory Range: 0xd8000000-0xdfffffff (rw,prefetchable)
  I/O Ports: 0xee00-0xeeff (rw)
  Memory Range: 0xfddf0000-0xfddfffff (rw,non-prefetchable)
  Memory Range: 0xfdd00000-0xfdd1ffff (ro,prefetchable,disabled)
  IRQ: 21 (476 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001002d00005954sv0000103Csd00002A26bc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: radeon
  Driver Info #1:
    XFree86 v4 Server Module: fglrx
    3D Support: yes
    Extensions: dri
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #26 (PCI bridge)

Primary display adapter: #12

---

### Post by mörgæs on 2010-07-08
Sorry for asking, after reading again I can see that you already mentioned the card name in the first post...

ATI has dropped support for this card, so you will not find any closed source drivers for 10.04. Of the supported Ubuntus, only 8.04 includes the closed source driver.

An open source driver is shipped in all new Ubuntus. There are mixed reports on how well it works - some get a great performance, some don't. I guess that the best advice is simply doing a clean install (not upgrade) of 10.04 and see how it works on your gear. In case of emergency you can just revert to 8.04.

You will need to do this exercise sooner or later anyway, since support for 8.04 (the desktop version) is ending in April 2011. 


[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by Crash Dummy Dave on 2010-07-08
Thank you for the information. If I have trouble, I'll replace the video card to a card supported better. As you say, I will eventually need to move forward.

---

### Post by mörgæs on 2010-07-08
You are welcome. 

Please post your findings when you install 10.04; there may be others facing the same problem.

---

### Post by Crash Dummy Dave on 2010-07-08
I marked this thread as solved too soon, so I changed that until I actually make this work. I will be doing an upgrade first, not a fresh install to see what happens. I can always start over to do a fresh install. I will be trying that in a a couple of days, and I will post the results here.

---

### Post by Mark Phelps on 2010-07-09
> **Crash Dummy Dave said:**
>  I will be doing an upgrade first, not a fresh install to see what happens. 

If you're currently running FGLRX drivers and you do an upgarde, there's a chance that you won't get a video display after the upgrade because those drivers will not work with 10.04.

You should remove those drivers and replace them with the open source drivers before you do the upgrade.

---

### Post by Crash Dummy Dave on 2010-07-09
Mark, your answer gets to the heart of the **upgrade** question. I was wondering if the upgrade would automatically replace my driver with a driver of some sort for the video, and I understand that you are saying that it will not, but that there is one available in open source, and that I need to use it. 

I want to upgrade to avoid reinstalling all the applications. If Ubuntu offers "upgrade" then it should work or be discontinued. I feel it will work. A fresh install is always available if this fails.
 
I remember that when I first installed 8.04, I was new to Ubuntu and couldn't understand why every time I started Ubuntu and logged in that I kept getting returned to the login screen. I found out on my own (the forums had only questions about it and no answers) that the problem was that there was no video driver. The only one I could find at that time for my video card was proprietary. The reason that I was being continually returned to the login was that Ubuntu would not start without a video driver.

There was a work around for this that I found on my own. In 8.04 on the first login screen in the lower left corner was a button for "options". After clicking that I selected "select session". On the next list I checked "failsafe gnome". When I did that I got video, and Ubuntu started and ran fine without a video driver installed. I then looked around and found the proprietary driver available in system/administration/hardware drivers. I am hoping that 10.04 still has this "failsafe gnome" option in case I have video problems after upgrade to 10.04.

I'll change to the open source driver in 8.04 using the instructions here:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

My card is supported in the list there.

It will be two more days before I will have time to work on this.

---

### Post by Crash Dummy Dave on 2010-07-14
Thanks to both of you for your help.

I finished the upgrade from 8.04 to 10.04 without a problem in the video driver. I uninstalled the fglrx driver using the directions in the link I gave in my last post. Then I restarted the computer, and when the login screen appeared I right clicked the icon in the lower left corner of the screen and selected to change sessions, and changed the session to failsafe gnome. I needed to do this because I now had no video driver. I then logged in.

I continued without a video driver in the failsafe gnome session and started the upgrade. When the upgrade was completed, the radeon driver had been installed by the upgrade.

I noticed by using the synaptic package manager after the upgrade to 10.04 that there was an fglrx driver in the repositories list, but it was not installed. I know nothing about that driver, and I am not installing it, but it seems strange that it is there in the available list, and the description stated it was supported until 2013, but the upgrade had told me that there was none available.

It is not possible to install the radeon driver in 8.04; therefore to upgrade you have to do it driverless. The upgrade then installs the right open source driver. By upgrading you can keep most all customizations and do not have to reinstall all your apps.

---

### Post by HenneBaby02 on 2010-07-14
i downgraded back to 8.04 for the same reason lol

---

### Post by JHCKX on 2010-07-15
The fgrlx driver is for ATI proprietary drivers. They've stopped making these for older cards like the Xpress 200m but continue to support other cards.

I have a Packard -Bell EasyNote MZ35 laptop with a Radeon Xpress 200M video card. I've never used 8.04 but I've heard suspend/hibernate did work with 8.04 and fgrlx, is that true? I did find that Ubuntu 9.04 graphics performance with an open source driver seemed better than Ubuntu 8.10 with fgrlx. Unfortunately, for me Ubuntu 10.04 graphic perfomance is worse than using 9.04, see [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/576125](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/576125). My solution was to install the xorg-edgers PPA. That gives me beta versions of the video drivers (with a risk of system instability). But for me, so far there have been few problems (but not none, in two weeks).

Instructions can be found at [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
Basically

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update

Then run "update" from the "Administration" menu.

At your own risk of course ;)

---

### Post by Crash Dummy Dave on 2010-07-15
Thanks for the suggestion. I'll look into that.

For me in 8.04 using the fglrx driver, everything about the video worked as well as in any other operating system using that on-board chip (not a separate card). I never tried hibernate or suspend, which were unnecessary for me.

I have been using the radeon driver now for a few days, and my video is working and very sharp. The problem is that with 8.04 and fglrx I could get more textures and effects in online video games, such as runescape where the video is now less detailed- torches don't flicker, some texture and lighting detail missing. On the whole except for higher end video games, the radeon driver is fine. It is certainly good for movies.

This is a cheap video chip anyway, and I will probably go to the nVidia card when I get wealthy enough, since Ubuntu 10.04 seems to support that better.

Until then I'll either leave things as they are, or take your suggestion, or try the fglrx driver that was offered by the Canonical partner repository in 10.04, if I find that my video chip is supported to use it.

It is good to know that there are alternative options. Thanks.

---

### Post by alphacrucis2 on 2010-07-15
> **Crash Dummy Dave said:**
> Thanks for the suggestion. I'll look into that.

For me in 8.04 using the fglrx driver, everything about the video worked as well as in any other operating system using that on-board chip (not a separate card). I never tried hibernate or suspend, which were unnecessary for me.

I have been using the radeon driver now for a few days, and my video is working and very sharp. The problem is that with 8.04 and fglrx I could get more textures and effects in online video games, such as runescape where the video is now less detailed- torches don't flicker, some texture and lighting detail missing. On the whole except for higher end video games, the radeon driver is fine. It is certainly good for movies.

This is a cheap video chip anyway, and I will probably go to the nVidia card when I get wealthy enough, since Ubuntu 10.04 seems to support that better.

Until then I'll either leave things as they are, or take your suggestion, or try the fglrx driver that was offered by the Canonical partner repository in 10.04, if I find that my video chip is supported to use it.

It is good to know that there are alternative options. Thanks.

I wouldn't rule out ATI. The latest Catalyst driver (10.6) which hasn't yet made it into the Ubuntu repos is pretty good with the newer HD cards. A good place to ask about this sort of thing is the Phoronix forums. They have sections dedicated to NVIDIA and ATI proprietary and OSS drivers. Anyway my HD3400 (not exactly state of the art either) works brilliantly with Catalyst 10.6. Definitely don't try to use Catalyst (fglrx)  drivers that work in Lucid (10.04) on your current card - these drivers do not support the old Radeon Xpress cards at all.

---

### Post by Oriana on 2010-07-24
Before you restart the computer after adding the xorg-edgers' ppa to your repos, make sure you install the ppa-purge package! I wound up having to do so after the fact, and if having a non-responsive computer is annoying, think about the idea of having your backup being a osx 10.1 powerpc g3 that only runs internet exploder for mac. Anyway, you can install the program by downloading the .deb from the site, or, after the xorg-edgers ppa has been added, 

```
sudo apt-get install ppa-purge
```

and later (when xorg-edgers, or whatever ppa you want to remove, doesn't work out)

```
sudo ppa-purge xorg-edgers
```

Reboot, happy compy!

---

### Post by SnappyU on 2010-12-18
John, I also own the same Easynote MZ35 notebook and have been on 9.04 after karmic proved to be disastrous!

I've been trying to install 10.04 or 10.10 recently, but am facing much difficulties with the thumbdrive install.

Did you install with a CDR-iso burn or thumbdrive?

Please advise.  Much thanks!

> **John2.Hendrickx@gmail.com said:**
> The fgrlx driver is for ATI proprietary drivers. They've stopped making these for older cards like the Xpress 200m but continue to support other cards.

I have a Packard -Bell EasyNote MZ35 laptop with a Radeon Xpress 200M video card. I've never used 8.04 but I've heard suspend/hibernate did work with 8.04 and fgrlx, is that true? I did find that Ubuntu 9.04 graphics performance with an open source driver seemed better than Ubuntu 8.10 with fgrlx. Unfortunately, for me Ubuntu 10.04 graphic perfomance is worse than using 9.04, see [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/576125](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/576125). My solution was to install the xorg-edgers PPA. That gives me beta versions of the video drivers (with a risk of system instability). But for me, so far there have been few problems (but not none, in two weeks).

Instructions can be found at [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
Basically

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update

Then run "update" from the "Administration" menu.

At your own risk of course ;)

---

