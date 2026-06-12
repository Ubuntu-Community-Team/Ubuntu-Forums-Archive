---
title: "No network interfaces detected"
date: 2005-02-25
forum: Installation &amp; Upgrades
---

### Post by W. Irving on 2005-02-25
Yup, that's the error I get when the installation program is attempting to proceed with the "Configure the network" step. The dialog box furher informs me that
"You may need to load a specific module for your network card, if you have one. For this, go back to the network hardware detection step."
When I choose to do so, the installation program automatically searches for NICs, seems to be finding one ("Starting PC card services.." can be seen briefly), and proceeds to 'Configure the network', and there we are again. :P
I installed Debian shortly before finally deciding on Ubuntu, and during the installation phase I was able to choose a driver for the NIC. I cannot remember which one I chose (I think it was the Tulip one..), but I was given a number of drivers to choose from, and it worked. Which is not what is happening in the Ubuntu installation program, contrary to what it says.
What do I do?

The NIC is a Wlinx Cardbus device in an IBM 600 Thinkpad.

Very grateful for all the help I can get! :)

---

### Post by W. Irving on 2005-02-26
No ideas?
I find it strange how the setup refers to a dialog that doesn't exist..

---

### Post by wolfchri on 2005-03-15
Try the bootparameter

 pci=noacpi 

in boot/grub/menu.lst, that helped me.

---

