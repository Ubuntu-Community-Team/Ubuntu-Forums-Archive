---
title: "Can't install on Winbook laptop. (via82cxxx hanging on install)"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by k4o on 2007-05-19
I don't have a CD drive in the laptop, so I am doing a network install through PXE.  It downloads everything fine, but when it gets to "Detecting disks and other hardware", it hangs on "Loading module 'via82cxxx' for 'IDE chipset support'".  I tried installing using the 'pci=nommconf' flag but no dice.  This is bothering me to no end.  This is what the console reports:

hw-detect: Detected module 'via82cxxx' for 'IDE chipset support'
hw-detect: insmod /lib/modules/2.6.20-15-generic/kernel/drivers/ide/pci/via82cxxx.ko


stops there.

Is there a way I can fit the ubuntu installer on a 512mb flash drive and just upgrade everything through the web, bypassing all of this hassle?

---

### Post by k4o on 2007-05-19
I know it's only been a few hours and I normally don't do this but any ideas?

---

### Post by Topsiho on 2007-05-19
I am sorry that I can not help you, as I am no expert, even if I sound like one if I ask you to do dmesg in a terminal. Maybe you'll find what is bothering your computer...

To give you an idea what the via82cxxx.ko is I show you what I get after a locate on my machine:

topsiho@Bromo:~$ locate via82cxxx.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/ide/pci/via82cxxx.ko
/lib/modules/2.6.17-11-generic/kernel/drivers/ide/pci/via82cxxx.ko

For both kernels that I have it's a driver, in your case for your via chip set.

As I sadly said already: I can not help you more, and I hope a real expert will jump in this matter :)

Topsiho

---

### Post by k4o on 2007-05-19
Hey, thanks for that, dmesg spits out a bunch of stuff, nothing looks out of the ordinary, but I can't scroll up through the log.

---

### Post by Topsiho on 2007-05-21
You say you can't scroll through the log, which makes me think that you did dmesg in a real ( :) ) text screen, such as tty2 which you get after ctrl-alt-F2 (you get the graphical screen again with alt-F7).

If you use the text screen within Gnome or KDE then you can easily scroll in the text and see if you find something. But probably the cause of trouble is within the last lines.

Topsiho

---

### Post by k4o on 2007-05-23
I scrolled around and couldn't find anything bad.  It just seems to stop at that part when loading the module via82cxxx.ko

I'm on Windows right now (:() but I want to put Ubuntu on ASAP.

---

### Post by Topsiho on 2007-05-24
Do you have this module, in the right place? Just check this. If it is not there I wouldn't know why it is not. But it looks like it can not be found.

Topsiho

---

### Post by k4o on 2007-05-24
How would I check?

I am doing the PXE install so I assume it is downloading everything from the internet or from whatever I have from the FTP.

Would it work if I went back a build?  Maybe back to 6 instead of 7?

---

### Post by k4o on 2007-05-24
Anyone?

---

### Post by Topsiho on 2007-05-25
Sorry for not being on line every minute a day.

One way to check is to repeat what I did in a previous post and see whether you get something like this:

topsiho@Bromo:~$ locate via82cxxx.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/ide/pci/via82cxxx.ko
/lib/modules/2.6.17-11-generic/kernel/drivers/ide/pci/via82cxxx.ko

There are more sophisticated ways, but this will do I think.

You could of course try a previous version too, and I would suggest Dapper Drake, that is Ubuntu 6.06 LTS. This is a so called Enterprise version: more stable and longer support for securities.

Topsiho

---

