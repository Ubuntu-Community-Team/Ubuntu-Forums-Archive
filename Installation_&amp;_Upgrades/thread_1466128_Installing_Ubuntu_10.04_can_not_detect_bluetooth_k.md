---
title: "Installing Ubuntu 10.04 can not detect bluetooth keyboard and mouse"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by nocknock on 2010-04-30
Hello friends.

I tried to do a clean install of Ubuntu 10.04, but when I get to the screen if I want to test or install Ubuntu, the keyboard and mouse (bluetooth) don't work.

I tried to resync the peripherals, I disconnected usb connector base of the tower and putting it back but nothing works for me.

I have a Logitech Desktop MX 5000 (Bluetooth).

Does anyone have an idea?

Thank you very much.

---

### Post by TariBuntu on 2010-04-30
Well, this is no idea - rather to let you know you're not alone out there.

Guess we're stuck with the same problem...

[http://ubuntuforums.org/showthread.php?t=1465899&highlight=bluetooth+keyboard]("http://ubuntuforums.org/showthread.php?t=1465899&highlight=bluetooth+keyboard")

---

### Post by Peter09 on 2010-04-30
Is it this
 
> [https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/553964](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/553964)

---

### Post by P4man on 2010-04-30
can you connect an usb mouse and see once the session has started if the bluetooth works then or not?

---

### Post by nocknock on 2010-04-30
i'm started with a keyboard and mouse usb. But i have the same bluetooth problem, in my user session.

---

### Post by P4man on 2010-04-30
Peter09 provided a good link with (a duplicate of) the bug that is biting both of you:

[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288)

It provides a workaround, and I would suggest subscribing to that bug and clicking the "it affects me" pending  a fix.

---

### Post by IzeHouze on 2010-04-30
I am currently running upgrade, and there is a screen that pops up stating what packages are no longer supported.  First item on the list is 'bluetooth'

Does this mean there is a replacement package or have they dropped support completely?

---

### Post by P4man on 2010-04-30
its replaced (by bluez).

---

### Post by martin.christensen on 2010-05-01
I have a diNovo Logitech bluetooth keayboard and MX bluetooth mouse.

In order to get them working I have to disable the bluetooth restart section in /etc/init.d/bluetooth.

 
```
   restart|force-reload)
    echo "Bluetooth restart disabled"
    # $0 stop
    # $0 start
    ;;
```

After restarting my machine I can setup the bluetooth pairing for the mouse and keyboard through the Bluetooth Applet / Bluetooth Preferences dialog using a cabled mouse.

Long time ago I read somewhere that the logitech devices couldn't handle the usb hidd restart. It might not be true, but it gave me the idea to try this out.  I have been doing something similar in ubuntu 8.x and 9.x. The bluetooth script just looked a bit different and I didn't have to create the bluetooth pairing in the Bluetooth Applet.

---

### Post by malrost on 2010-05-01
I'm also using a Logitech Edge keyboard, and it was not functioning after upgrading. 

[This fix]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288/comments/10") worked for me after installation. 

I had an USB mouse handy and was able to make the changes using the onscreen keyboard.

---

### Post by VMZ on 2010-11-02
Sorry for digging up graves, but this problem occured again just after recent updates (two days ago). Didn't notice any bluetooth-related stuff going, but I'm not sure.

However, the link posted by malrost is still current, and works for Logitech DiNovo Media Desktop.'

In case it disappears from launchpad, here's a snip from the comment:

***

Kent Wilkinson wrote on 2010-04-24

/lib/udev/rules.d/70-hid2hci.rules

from

# Logitech devices
KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"

to

KERNEL=="hidraw*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"

***

---

