---
title: "ATI drivers and NVIDIA drivers"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by rnodal on 2006-07-02
Hello:

      I have an ATI and NVIDIA pci card on my machine. They work fine but only the ati one has 3D support. If I try to install the "nvidia" driver it will remove the ATI driver. Is there a way to have both? I just want to run two different window managers on each card and have 3D support. Is there a way? Thanks a lot for your support!


-r

---

### Post by yager on 2006-07-15
Just in case no one has answered your request earlier, what you are trying to do is going to require some heavy editing of the xorg.conf file.  I am not going to even begin to pretend I know all of the edits, but I have researched a few starting points for you so you can break this problem down into bite size pieces and work through them one at a time.

The book "Ubuntu Hacks" published by O'Reilly reviews many of your issues in Hack #50.  This is 7 pages of info on the xorg.conf file and the required settings for dual screens, dual graphic cards etc.

There is also the link at [http://xorg.freedesktop.org/archive/X11R6.8.0/doc/xorg.conf.5.html#toc2](http://xorg.freedesktop.org/archive/X11R6.8.0/doc/xorg.conf.5.html#toc2)

You will need to first set up the devices for each card.
Next you will set up each monitor that you have.
After this, you define the screen for each monitor.
Lastly you pull it all together in the Serverlayout.

I hope this starts you down a productive path to resolve your wishes.  Good Luck.  It sounds like you will have a cool setup once you pull this off.

---

### Post by rnodal on 2006-07-15
FIRST OF ALL THANK YOU FOR YOUR KIND REPLAY.

I managed to setup a multi user system and everything works perfect(as it is suposed to work, not 100% my way). Don't you love ubuntu. I will post my xorg file as an example later in the forums because I know it may help other people. Any way the real challenge is whether is possible to have both card with 3D acceleration? Maybe I find the answer within your links. Any way thanks for your help. Take care,

-r

---

