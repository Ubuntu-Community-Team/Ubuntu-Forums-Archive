---
title: "Lucid upgrade killed mouse, nipple mouse and touchpad"
date: 2010-02-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by eggnogg on 2010-02-23
Hello,

after running apt-get upgrade, my mouse no longer works under x
neither does the touchpad nor the nipple mouse

(thinkpad r51)

what do i do?

---

### Post by eggnogg on 2010-02-23
my /var/log/Xorg.0.log file has the following lines:

Cannot locate core pointing device
Cannot locate core keyboard device

Look at this link: [http://linux.derkeiler.com/Mailing-Lists/Fedora/2008-09/msg02187.html](http://linux.derkeiler.com/Mailing-Lists/Fedora/2008-09/msg02187.html)

I would like to try this, but i have 17 xorg.conf.* files,

e.g:

xorg.conf.20090320173936
xorg.conf.20090320174748
.....
.....
.....
xorg.conf.deactivated
xorg.conf.dist-upgrade-200905201950
...
...
xorg.conf.failsafe

which one do i modify?

---

### Post by eggnogg on 2010-02-23
running:

sudo X -configure

didnt help either

When i do the following:

startx

Network Manager connects to my ethernet port and I have an internet connection, but no way of communicating with this connection

If I did so, perhaps dpkg  or dist-upgrade would help fix this error?

Can I connect to the ethernet connection via terminal?

---

### Post by eggnogg on 2010-02-23
ok, i ended up fixing it myself.

here's what i did:

sudo dhclient eth0, to get ethernet runnin
sudo aptitude update
sudo aptitude dist-upgrade

after the above, starting x would still result in no keyboard or mouse, so i saw the lo file:

sudo less /var/log/Xorg.log.0

and sure enough, i needed to add the following :

Section "ServerFlags"
Option "AllowEmptyInput" "off"
EndSection

into /etc/X11/xorg.conf

restarting x got everything up and smooth

---

