---
title: "Install to 2GB compact flash"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by xenomorph99 on 2008-04-17
Hi,

I've been trying to install Ubuntu to a CF (IDE adaptor) but I wish to only install a cut down version with Gnome (or XFCE), Firefox (or Epiphany), Thunderbird. 

I don't wish to install the server edition so I tried the alternate install expecting it to ask me what packages I'd like to install but it didn't - this, presumably, would have failed eventually as I only have a 2GB flash card (I tried to install Ubuntu desktop but that ran out of disk space).

So, two questions:

a. How do I, preferably without using the server edition, install Ubuntu with just the items I require?
b. Will I see any performance differences between running from Flash vs HDD?

Rgrds,
X

---

### Post by greenstar on 2008-04-17
I don't know why you're avoiding the server edition, as it's likely the best way to accomplish your goal. Install it, then just add the packages you want. You can even use Reconstructor to roll your own custom Ubuntu once you have it the way you like. The other option is to do a basic install from the Alternate CD, then remove those packages you don't want. None of the discs will let you choose exactly which packages are installed.

I'm not sure about the speed question. To the best of my knowledge, you should configure your Ubuntu install to minimize disk writes to foster longer life for your CF card. Excessive writes to the CF card *will* shorten it's life.

Good Luck

Greenstar

---

### Post by picopir8 on 2008-04-17
search the net for "ubuntu mini.iso" and you will find the net installer.  It is a 10MB iso image that downloads all packages on the fly during the install.

The installer will only install the basic version of ubuntu (cli only, no gui).  From there simply "apt-get install xubuntu-desktop".  I think the total install is about 1.6GB, IIRC.

If you want something a little leaner, dont install xubuntu-desktop, instead do a "apt-get install xorg gdm fluxbox" to get a barebones fluxbox gui.  The total install w/ fluxbox is a little under 800MB.  Then just add the apps you want.

Flash boots up a bit slower than HDD but is should not be too noticeable.  And though flash lasts longer nowadays, it will still wear out after about 300k reclaims.  So if you intend to use this for personal use you should be okay because you will likely replace it before it wears out.  But if you are making some sort of network appliance, you will need to move /tmp, /var, and parts of /etc to a ramdisk and then mount the flash card in readonly mode so you dont wear out out the disk prematurely.

---

### Post by kerry_s on 2008-04-17
> **xenomorph99 said:**
> Hi,

I've been trying to install Ubuntu to a CF (IDE adaptor) but I wish to only install a cut down version with Gnome (or XFCE), Firefox (or Epiphany), Thunderbird. 

I don't wish to install the server edition so I tried the alternate install expecting it to ask me what packages I'd like to install but it didn't - this, presumably, would have failed eventually as I only have a 2GB flash card (I tried to install Ubuntu desktop but that ran out of disk space).

So, two questions:

a. How do I, preferably without using the server edition, install Ubuntu with just the items I require?
b. Will I see any performance differences between running from Flash vs HDD?

Rgrds,
X

using the alternate cd you need to type> install server < which is just a base install, has nothing to do with a actual server. double check in the menu for the command, it might just be "server", not sure it's been a while.

after that you need to install a gui->
sudo apt-get install xorg
you need a window manager or desktop, i'll do xfce4->
sudo apt-get install xfce4
you might want a login manager->
sudo apt-get install gdm

reboot(ctrl+alt+delete)

and continue building from the gui.

---

