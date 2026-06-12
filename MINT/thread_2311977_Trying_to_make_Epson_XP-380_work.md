---
title: "Trying to make Epson XP-380 work"
date: 2016-01-31
forum: MINT
---

### Post by ggk494 on 2016-01-31
I am running linux Mint with a 64bit and apu

---

### Post by howefield on 2016-01-31
Thread moved to the "*MINT*" forum.

---

### Post by yancek on 2016-01-31
That's not much to go on.  You will need to post more details such as what you tried and what happened.  How did you try to configure the printer and what were the results, error or warning messages?

---

### Post by rewyllys on 2016-02-02
First, the Epson Website does not list a printer identified as "XP-380".  Are you sure that this the actual name of the printer you have?

Second, Epson does not supply drivers for Linux for its printers.  You might find a driver that some Linux enthusiast has written for your printer, by Googling for it.

But you probably would do best by finding a way to trade your Epson printer for one from Brother, Canon, or HP, all of which provide Linux drivers for their printers.  And Brother makes it especially easy to install the pertinent Linux driver for any of its printers.

---

### Post by andreas93j on 2016-02-04
Hey ggk494,

If there are no native drivers, I got a quick workaround for you.
You could install VirtualBox on your Computer.
1.) Import a Windows Appliance ([https://dev.windows.com/en-us/microsoft-edge/tools/vms/](https://dev.windows.com/en-us/microsoft-edge/tools/vms/)), where the driver works
2.) Connect your printer on usb and forward it to the VM (you can also use a network printer, therefore you have to use a network bridge as adapter)
[IMG]http://s13.postimg.org/71k4zjeyv/vm_usb.png[/IMG]
3.) Start your VM and install the drivers

Note: You'll have to print your documents via the virtual machine. This could be quite annoying on the long run. If you are looking for a new printer  I can totally recommend HP, they have a great Linux support.

Greets andy

---

### Post by howefield on 2016-02-04
Are you sure it's not an R380 ?

If not automatically recognised by your system, the linux driver can be download from the Epson website as is the case for most (all?) their printers.

---

