---
title: "Logitech Dinovo Edge (usb keyboard) fail on 10.04 upgrade"
date: 2010-08-07
forum: Installation &amp; Upgrades
---

### Post by buybuydandavis on 2010-08-07
Hi. I had a hell of a time getting 10.04 to work, because I only have a Logitech Dinovo Edge keyboard, and it stopped working after I upgraded. After grub, I'd get to the login screen, and the keyboard wouldn't do anything.

[LIST]
[*]First, I dug up a mouse that did work.
[*]Then I logged in by clicking the Human Accessibility icon on the login screen.
[*]Somewhere in there, I was able to bring up an on screen keyboard.
[*]With the on screen keyboard, I could now login.
[*]Under system>preferences>bluetooth, I was able to, after some fiddling and plugging and unplugging, get the keyboard paired to the bluetooth dongle.
[/LIST]
Anyway, it seems pretty obvious now that my original bluetooth pairing was lost with the 10.04 upgrade, and I just needed to re-pair. I don't remember having such problems on previous upgrades, though.

I've seen a few other folks having problems with keyboards going dead on the upgrade, so I thought I might be able to save someone some aggravation.

---

### Post by efflandt on 2010-08-07
The problem is that due to a different bug report for 9.10 (where it worked) they changed something in 10.04 to make it not work, which is strange because it normally works right from boot for BIOS password or CMOS setup with no drivers at all required.

There are either of 2 quick solutions by editing /lib/udev/rules.d/70-hid2hci.rules if you have access to a regular keyboard.  Use **sudo nano** or **gksu gedit** to either change "hiddev*" back to "hidraw*", or commenting out the two lines after Logitech devices works just as well for me as follows:

```
# Logitech devices
#KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \
#  RUN+="hid2hci --method=logitech-hid --devpath=%p"
```

After that the Bluetooth applet is not even required and should not even show up unless you are using some other Bluetooth for something else.

---

