---
title: "Installing on netbook: no GUI and no livecd"
date: 2013-02-09
forum: Installation &amp; Upgrades
---

### Post by Oliiive on 2013-02-09
Hello and sorry to bother but I need some help

I tried to install and to livecd those distribs
XUbuntu 12.10 386
XUbuntu Amd64
Ubuntu 12.10 Amd64

on live cd, 2 shows check list (ok, with just sounddriver fail, the third doenst show anything

On running after install, both just shows text admin prompt, I log on and tried all the stuff (startx, sudo startx, sudo service lightdm start, without any success.

On the startx, it says error no screens found or something like that.

I'm stuck , would be happy to use Ubuntu, I use it on my desktop pc but can't with my netbook
I have Acer Aspire One D270, 1G ram, Atom N2600 (64 bits capable)

You can tell me anything, including walk to the moon, but would be happy to run Ubuntu on my netbook, because Win7 and firefox are sooooooooo slow!

Olivier

---

### Post by BicyclerBoy on 2013-02-09
Your h/w is the newest atom cedarview/trail graphics which is not open source like most intel graphics.

To get it to boot & at least display desktop GUI, you need kernel 3.5 & latest intel drivers (cedarview).
I don't have this h/w but have advised others who were met with success.

You can get all this and more (no trip to the moon included unfortunately) from xorg-edgers ppa.

Expect a rocky ride with cedarview driver..

---

### Post by Oliiive on 2013-02-10
Thanks for the tip. Have you an idea how to get my ubuntu works? 

I don't know how to get to have anything from xorg-edgers ppa.

What's the procedure? Thanks!

---

### Post by grahammechanical on 2013-02-10
This will tell you how to install this PPA:

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")

For you information, 12.10 does have the Linux 3.5 series kernel. New installs of 12.04.2 also get kernel 3.5

Regards.

---

### Post by Oliiive on 2013-02-11
I use a loooooong internet key (of 56 HZFh7724jn characters) to connect to internet... Tried to connect with iwconfig wlan0 key s:xxxx stuff, without any success... I'm tired to not solve my problem and remain with no GUI... Someone told me to try the 13.04 dev, I will but if still no interface, I give up and will use mandriva (or remain in w7), with my hard and deepest regrets.

---

### Post by U202E on 2013-02-11
> **Oliiive said:**
> 
On the startx, it says error no screens found or something like that.

^^do you have a GUI when using the live cd?
the no screens found could occurs if: it doesn't recognize the gpu; you have no unity/xfce/lightdm installed; you didn't use sudo startx...

how does tty7 look like? (by pressing ctrl+alt+f7) if it's 100% black the x-session isn't started, if tty7 is the cli showing up after booting up there is something strange.

have a look at this page: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=682221](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=682221)
there is a shortcut to restart the x-session: ctrl+prtscreen+K (found that somewhere on the internet)

---

### Post by Oliiive on 2013-02-11
.... solved. installed Ubuntu 13.04, runned with success with the gui, and changed Unity to XFCE

---

