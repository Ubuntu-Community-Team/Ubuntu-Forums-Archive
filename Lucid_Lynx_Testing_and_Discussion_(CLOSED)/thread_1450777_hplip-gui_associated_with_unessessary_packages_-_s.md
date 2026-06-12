---
title: "hplip-gui associated with unessessary packages - synaptic"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by BrokeMahPC on 2010-04-09
When choosing to install the hplip-gui in synaptic, it also requires the installation of gimp and xsane. As we already have simple scan installed by default why is this necessary?

edit - add to that cups-pdf - also requires gimp and xsane

Ubuntu 10.04 Beta 2 - downloaded 9th April

Just to let you know - no other problems with Beta 2 so far but not fully tested.
Boots well and fast - don't get plymouth splash on startup but it boots so fast, hard to tell if it's there or not.
ATI proprietary driver seems to be working well
ATI Radeon HD 4670
It requires: sudo aticonfig --initial -f after reboot when installing with the hardware drivers app.

I am using 2 hard drives - it did not detect the Linux Mint install on the other hard drive so had to run: sudo update-grub. It found it after that.

---

### Post by cariboo on 2010-04-09
It looks like after all the complaints about removing gimp from the default installation, they've made it much easier to install gimp. :)

---

### Post by emarkay on 2010-04-09
Interesting - don't recall addig GIMP. but it';s installed - and yes I did add Xsane - I have a scanner/printer.

Maybe GIMP has added data needed that is easier than making a stand alone package?

---

### Post by BrokeMahPC on 2010-04-09
Well it does make you wonder! hplip and cups are already installed and working without gimp and xsane. I am simply adding a gui for hplip and an additional feature of cups - why does it need gimp and xsane? Not that I mind - I love gimp but would prefer not to install it during testing. :confused:

---

### Post by n6yga on 2010-04-09
It's been that way since 9.10.


Mark.

---

### Post by kansasnoob on 2010-04-09
And the problem is?

You disagree with the dependencies?

Does anything NOT work properly?

---

### Post by BrokeMahPC on 2010-04-09
Well I guess it's not a problem - just wondered if it was.

I found it odd that ubuntu decided to remove Gimp from the default install and that installing two piffling little printing application add-ons requires an entire graphics package!

I also found it odd that ubuntu decided to remove Xsane from the default install and go with simple scan - then installing the above requires Xsane back again.

It didn't make sense, so thought I had better check if it was all OK. OK?

---

