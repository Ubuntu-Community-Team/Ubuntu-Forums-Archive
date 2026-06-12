---
title: "Keyboard problem after 10.04 upgrade"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by etwietmeyer on 2010-05-04
Hello,
 
I just upgraded my 9.10 x64 Server to 10.04 using the standard Update Manager (I have the GNOME desktop installed). The installation went very smoothly, no errors or problems that I noticed.
 
However, after reboot I get the main log in screen, but I can't enter my password because the keyboard seems to be ignored. The mouse is fine, no problems there. I looked at the various keyboard possibilities, and it has choosen the basic "USA" keyboard. It doesn't matter which keyboard type I choose though, it still fails to respond to any keyboard keypress.
 
To be clear, there were no issues with the keyboard before the upgrade.
 
I don't know where to start. Any pointers would be very helpful. Thanks.
 
-Eric

---

### Post by etwietmeyer on 2010-05-04
As an addendum to the first post: They keyboard is recognized in the grub menu thing, i.e. I can successfully hit "ESC" during startup and am presented with the boot selection screen and I can use the keyboard to interact with this.
 
It is just when it gets to the main, normal, log in screen that the system has problems getting keyboard input.

---

### Post by etwietmeyer on 2010-05-04
And further: The keyboard works if I boot to the basic root command line interface and don't bring up GNOME.

---

### Post by etwietmeyer on 2010-05-05
Ok, here is a work around:
 
[[COLOR=#444444]http://communities.vmware.com/message/1515622#1515622[/COLOR]]("http://communities.vmware.com/message/1515622#1515622")
 
I don't know why it should be necesary to modify this console-setup default, as the original version works on my 9.10 installs.
 
-Eric

---

