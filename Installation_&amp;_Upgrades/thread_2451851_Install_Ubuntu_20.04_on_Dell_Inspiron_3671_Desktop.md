---
title: "Install Ubuntu 20.04 on Dell Inspiron 3671 Desktop"
date: 2020-10-12
forum: Installation &amp; Upgrades
---

### Post by myjr522 on 2020-10-12
Hi,

I just want to share my experience to install the Ubuntu 20.04 in Dell Inspiron 3671 Desktop. I haven't been installed the Ubuntu by myself for several years and I struggled to cope with the Intel Rapid Storage Technology (RST) and the Security Setting in the BIOS.

Here is what I did and hopefully this would be helpful for someone:

0) the computer is coming with a pre-installation of windows 10 on the SSD driver with RST setting

1) I follow the steps in the link to edit the registers:

[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)

Once finished the register edit, do not reboot the computer at this stage but go to Step 2) below. 

2) In the windows, follow Choice #2 in the following link:

[https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems](https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems)

3) Now, reboot the computer, press F12 when Dell logo shows to access the bios, and change RST to AHCI in the bios

4) Also, turn off the secure boot option in the bios. 

If the secure boot option is active, this would give problems with nvidia graphic setting; in fact, I didn't turn off and installed the ubuntu; later during the ubuntu booting the normal boot failed and had to use the recovery mode ubuntu. I thought it might be the graphic card setting problems and digging into nvidia card settings; but it was the secure boot option in the bios.

5) now, you could hopefully install the ubuntu 20.04 followed the usual procedures.

---

