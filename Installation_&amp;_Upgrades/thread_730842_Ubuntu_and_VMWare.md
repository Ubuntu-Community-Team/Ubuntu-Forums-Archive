---
title: "Ubuntu and VMWare"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by ekmon1582 on 2008-03-21
I have the Ubuntu 7.10 Gusty .iso file on my computer, how do I set that up with VMWare?

---

### Post by Touch.Code on 2008-03-21
You need to set the .iso to a virtual disc or a physical one then just run VMWare with the disc drive to boot :)

---

### Post by ekmon1582 on 2008-03-21
So like burn an image to a disc? I have a LiveCD of Ubuntu 7.10, would that work. And when you say run vmware with the disc drive to boot, what do you mean?

---

### Post by Touch.Code on 2008-03-21
Yeah burn the iso or use Daemon tools to set the .iso as a virual CD :)

Change the VMWare BIOS settings to boot from CD.

---

### Post by ekmon1582 on 2008-03-21
Alright, how do I change the vmware BIOS settings? Also keep in mind this is a school computer, so I don't want to do anything that will cause loss of windows, or screw my computer up.

---

### Post by Touch.Code on 2008-03-21
When VMWare starts to boot, press F2 or Delete :)

---

### Post by ekmon1582 on 2008-03-21
All it does is rename it. When you say when vmware starts to boot, you mean when I start vmware right?

---

### Post by mmichalik on 2008-03-21
Another way is to start the VM server and then create a new virtual machine.

in the hardware properties of the virtual machine, before you power it up, change the connection settings from the physical CD to "Use iso image" by clicking the radio button and then, put the path to the iso in the field.

Then power up the virtual machine and it will automatically boot from the iso image.

---

