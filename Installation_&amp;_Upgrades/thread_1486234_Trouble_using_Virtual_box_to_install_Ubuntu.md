---
title: "Trouble using Virtual box to install Ubuntu"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by aquaticann on 2010-05-17
Hello Everyone!

I'm attempting to try out Linux for the first time. I downloaded VirtualBox so that I can keep Windows Vista intact. I have everything set up until I try to run Ubuntu. Then I receive a fatal error:No bootable medium found! System Halted. 

Sorry you have to deal with an amateur! I have become really interested in Linux since I starting listening to This Week In Tech.

Thanks everyone for your help!

---

### Post by davidmohammed on 2010-05-17
The reason that VirtualBox can't find the OS - remember when you create a VM  there is no OS.

In order to boot a virtual machine to an OS, you have to install an OS first by mounting an ISO or physical CD with a bootable OS install.

Edit the virtual machine properties and attach the CD ROM drive containing the lucid live CD you have burned.  Alternatively - instead of attaching a CD ROM drive - point the CD ROM drive directly to the lucid iso file.

After you have done that, start the virtual machine - the VM will then install lucid.

---

### Post by aquaticann on 2010-05-17
Thank you so much! I'll be trying that tonight!

---

### Post by adamsiddhi on 2010-05-20
I had a different problem getting Ubuntu 10.04 to work in Virtualbox with in Vista & I video documented it over here:

[COLOR="Red"][http://www.youtube.com/watch?v=XMbbm5E_0Xw]("http://www.youtube.com/watch?v=XMbbm5E_0Xw")[/COLOR]

Help is welcome!

---

