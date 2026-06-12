---
title: "diNovo keyboard not working anymore"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by pwlodarczak on 2011-10-15
Hi there,
I upgraded to 11.10. After reboot my diNovo Bluetooth keyboard asked to enter the PIN shown in a pup-up and everything worked fine. After the automatic log out, the keyboard stopped working. I had to use the on screen keyboard to log in. I would then be prompted to enter the PIN for the keyboard, which I can since the keyboard doesn't work anymore. Also, I was always prompted to enter the PIN shown in a pop up window, even if I could I wouldn't know what PIN to enter.
Any help greatly appreciated since my computer it totally useless.
Thank you
Peter

---

### Post by redLeopoldo on 2011-10-16
Maybe this is a workaround: [http://www.spinics.net/lists/linux-bluetooth/msg17162.html](http://www.spinics.net/lists/linux-bluetooth/msg17162.html)

In the process of trying it.

---

### Post by redLeopoldo on 2011-10-16
Logged out and then back in: works. Had to do similar change when I first tried to connect keyboard.

---

### Post by pwlodarczak on 2011-10-17
Thank you. But what exactly did you do? When I change hiddev to hidraw as suggested in the problem report, the Bluetooth stack wouldn't start any more.

---

### Post by ckazimie on 2011-10-17
I have the same problem however I got my diNovo keyboard to work in 10.10 by changing to hidraw* however today there was an update of BT packages and the keybaord stopped to work. I can see the update reverted the settings back to hiddev* and the usual workaround to change it back to hidraw* doesn't work this time. The BT stack is not loaded.

---

### Post by pwlodarczak on 2011-10-17
I just did an update and the keyboard works again with hiddev.

---

### Post by ckazimie on 2011-10-17
My keybaords doesn't work

The section from 
/lib/udev/rules.d/62-bluez-hid2hci.rules
is 
# Logitech devices

KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"


bluez package was upgraded today from 
4.96-0ubuntu3 to 4.96-0ubuntu4
along with a number of other bluetooth packages.


I regret now having updated to Ubunto 11.10 :(

---

### Post by ckazimie on 2011-10-18
I have also got it to work with the hiddev* setting. You need to discover the keyboard in the bluetooth setup as a new device and then pair it. Afterwards the keyboard works fine. You need at least one additional mouse  that is working for doing this.

---

### Post by robth on 2011-10-18
When I upgraded to 11.10 my diNovo stopped working. Thanks to this thread I could get it to work after having edited my [FONT="Courier New"]/lib/udev/rules.d/62-bluez-hid2hci.rules[/FONT] file.

After today's upgrade the keyboard stopped working. But I would like to confirm that I got it working again after simply pairing it.

Hope you all get it to work as well! Much better than a virtual keyboard :D

---

