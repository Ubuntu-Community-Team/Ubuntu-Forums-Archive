---
title: "Bluetooth, GPS and pairing PIN"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by lotus49 on 2008-10-13
I am trying to pair my BT-Q880 bluetooth GPS receiver with my Acer Aspire One running Intrepid Ibex.

I have successfully paired my phone so I know it basically works.  When I try to pair with my GPS receiver, I am asked "Please enter the following PIN code: 8456" (the actual PIN obviously varies each time).

My GPS receiver, unsurprisingly, does not have any way of entering a PIN so how do I do this?

TIA for any suggestions.

---

### Post by outdooricon on 2008-10-13
> **lotus49 said:**
> I am trying to pair my BT-Q880 bluetooth GPS receiver with my Acer Aspire One running Intrepid Ibex.

I have successfully paired my phone so I know it basically works.  When I try to pair with my GPS receiver, I am asked "Please enter the following PIN code: 8456" (the actual PIN obviously varies each time).

My GPS receiver, unsurprisingly, does not have any way of entering a PIN so how do I do this?

TIA for any suggestions.

I am having this exact same problem with my dinovo mini keyboard using bluetooth applet (although I'm using Intrepid)...

---

### Post by lotus49 on 2008-10-14
I hope this isn't a stupid question, but if you are using a keyboard, can you not just type in the PIN on the keyboard?  My problem is that my GPS receiver has no keys so I cannot type anything.

---

### Post by JPorter on 2008-10-18
What I don't understand is why the PIN seems to automatically randomize and send every time when you try to pair a new device.

My Holux GPS puck for example, uses 0000 as its default PIN, and can't be set to other values.  I'm never given the opportunity to set the PIN when using the new Bluetooth applet to pair, and the default PIN setting in /etc/bluetooth/hcid.conf doesn't seem to have any effect on the new applet's behavior.

Is there ANY documentation whatsoever on the new Bluetooth tools?  Everything I find on the web seems to be from 6.10 and 7.04 vintage, including on the official Ubuntu wiki.  ;)

---

### Post by diafygi on 2008-10-22
I can confirm this problem. Anyone find a solution?

Edit: Found a bug report on Launchpad, [Bug #284994]("https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/284994"), with a possible workaround. Will report on if it works.

---

### Post by priegog on 2008-10-22
Yeah I can confirm this too. Seems odd that there is no way to choose to enter a pincode manually. the RC is due out tomorrow, hopefully this will be fixed by then. This problem DOES seem like the kind of mistakes they do on develpment versions, so there is hope.

---

### Post by diafygi on 2008-10-22
> **priegog said:**
> the RC is due out tomorrow, hopefully this will be fixed by then.
To ensure that adequate attention is drawn to this bug, everyone who sees the problem needs to confirm it on the bug tracker on Launchpad, [Bug #284994]("https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/284994").

---

