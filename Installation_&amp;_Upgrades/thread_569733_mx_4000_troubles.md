---
title: "mx 4000 troubles"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by wolf98 on 2007-10-07
hello all,
i just installed an ubuntu breezy badger system and it says that the x-server is not working. when i went in to reconfigure x.org it always defaults to the onboard videoand it wont allow me to change to the correct pci slot. could you tell me how to solve this problem. mabe i need to install the nvidia drivers but i need to know how to do that too. all help appreciated.](*,)](*,)](*,)](*,)](*,)](*,)

---

### Post by Pumalite on 2007-10-07
If you installed a new card, make sure it's configured in BIOS

---

### Post by wolf98 on 2007-10-07
whats bios

---

### Post by Pumalite on 2007-10-07
At boot, press 'Esc' or 'Del' or 'Tab', etc. Consult your motherboard Manual. It's where the computer gets it's facts before it runs.

---

### Post by Pumalite on 2007-10-07
[http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)

---

### Post by wolf98 on 2007-10-07
my bios has no means to configure it. how do you install the nvidia drivers

---

### Post by wolf98 on 2007-10-07
please

---

### Post by Pumalite on 2007-10-07
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by Pumalite on 2007-10-07
You are better off doing this first:

sudo dpkg-reconfigure xserver-xorg, choose 'vesa' as the driver. Once in the system install from System>Administration>Restricted Drivers Manager.

---

### Post by wolf98 on 2007-10-07
okay, now i have the drivers installed but ubuntu is not recognising the nvidia card and it wont let me change the pci slot what do i do?

---

### Post by Pumalite on 2007-10-07
Did you use your BIOS to have your card recognized and configured?

---

