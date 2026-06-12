---
title: "Bluetooth pairings not persisting over reboot"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by JPorter on 2009-03-28
I'm having an odd issue with the Bluetooth functionality provided by the Gnome Bluetooth Applet 1.8 (bluez).  This is on 9.04 32bit, with the latest updates.

I have a Logitech MX5500 Revolution wireless keyboard and mouse, which connect as standard Bluetooth devices.  The usb dongle for these units is not a "slave", it is a normal Bluetooth hub.

Everything works swimmingly, pairing is normal via the Bluetooth control panel with pairing-key transmission to the keyboard, etc.  Function is very good.


The problem is that the pairings do not persist correctly over reboot.  The devices still appear in the Bluetooth panel but aren't being reconnected properly.  I have to delete the devices from the list and then re-pair them to get them to function properly.


Also, even when paired and functioning, I am still able to "discover" the devices via [FONT="Courier New"]hcitool scan[/FONT].  If they're paired, I thought they shouldn't show up?


Any help that anyone can provide would be greatly appreciated.

Thanks!

---

### Post by Teracis on 2009-03-29
Hey man, I just set up my new box with ubuntu a week ago and have the mx5500, I'm only running Intrepid Ibex but the fix for that is this

[http://ubuntuforums.org/showpost.php?p=6549339&postcount=3](http://ubuntuforums.org/showpost.php?p=6549339&postcount=3)

worked for me, turns out its not hard to do either, even for someone brand new to ubuntu (like me):)

---

### Post by JPorter on 2009-03-29
That did the trick, thanks Teracis!

---

