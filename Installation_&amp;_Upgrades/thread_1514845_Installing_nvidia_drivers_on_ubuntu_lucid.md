---
title: "Installing nvidia drivers on ubuntu lucid"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by Zireth ZH on 2010-06-21
Hello there.. i just replaced my ati card for a nvidia ... ati drivers arent good enough for me... 

could you guys guide me on the installation of the drivers downloaded from the site?

ive tried this guide: [http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

but when i reach to this step :

''sudo apt-get –purge remove nvidia-*''

an error shows.. and i cant go on... currently im running ubuntu with the drivers found in ''hardware drivers''


please help me out THANKS IN ADVANCE

---

### Post by cascade9 on 2010-06-21
> **Zireth ZH said:**
> an error shows.. and i cant go on... currently im running ubuntu with the drivers found in ''hardware drivers''

please help me out THANKS IN ADVANCE

The drivers from "hardware drivers" are nVidia drivers, and unless you've got some good reason to try to install the nVidia drivers manually (like your hardware isn't supported by the version in hardware drivers) you are much better off using the version you are running already.

---

### Post by Zireth ZH on 2010-06-21
> **cascade9 said:**
> The drivers from "hardware drivers" are nVidia drivers, and unless you've got some good reason to try to install the nVidia drivers manually (like your hardware isn't supported by the version in hardware drivers) you are much better off using the version you are running already.

why is that? is it more stable or something? i thought i would gain considerably more performance if i install the latest drivers from them ... or im wrong? i wanna play some games..

---

### Post by cascade9 on 2010-06-21
The current driver in nvidia-current (10.04)- 195.36.15

[http://packages.ubuntu.com/lucid/nvidia-current](http://packages.ubuntu.com/lucid/nvidia-current)

The newest driver from nVidia- 195.36.31. 

I doubt that you would see even 1% increase in framerates from updating to the newest driver. Major revisions (say, 190.XX.XX to 195.XX.XX) is when you tend to see the most increase in perfromance, but minor updates (eg 195.24.XX to 195.36.XX) it much less noticable. With very minor revisions, like from nvidia-current to the newest version, there will be very very little difference. 

BTW, if you manually install the nVidia drivers and you get a kernel update, it can bork your system.

---

### Post by Zireth ZH on 2010-06-21
> **cascade9 said:**
> The current driver in nvidia-current (10.04)- 195.36.15

[http://packages.ubuntu.com/lucid/nvidia-current](http://packages.ubuntu.com/lucid/nvidia-current)

The newest driver from nVidia- 195.36.31. 

I doubt that you would see even 1% increase in framerates from updating to the newest driver. Major revisions (say, 190.XX.XX to 195.XX.XX) is when you tend to see the most increase in perfromance, but minor updates (eg 195.24.XX to 195.36.XX) it much less noticable. With very minor revisions, like from nvidia-current to the newest version, there will be very very little difference. 

BTW, if you manually install the nVidia drivers and you get a kernel update, it can bork your system.

ok so i guess ill stay with my current drivers then .. thanks alot for ur help man ):P

---

### Post by cascade9 on 2010-06-21
No problem, enjoy your games ;)

---

