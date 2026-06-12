---
title: "Help install Ubuntu Along side of Debian 7 wheezy !"
date: 2013-10-22
forum: Installation &amp; Upgrades
---

### Post by frank18 on 2013-10-22
I have Debian Wheezy 7 PPC on IMAC G5 and it runs Farely good, but i  would like to try other Distro like Ubuntu PPC but just for testing and  see which runs the best on my pc 
but i don't want to erase the  existent OS,in case i can't install ubuntu PPC, i want to be able to go  back to Debian Wheezy 7 and erase the other distro.Thanks

---

### Post by fantab on 2013-10-22
If you have a spare partition to spare then Yes you can.
Just remember to install the grub from ubuntu to its own partition. Otherwise it will replace the grub from Debian and install its own grub. Then if and when you remove Ubuntu you will have to re-install debian grub.

---

### Post by frank18 on 2013-10-22
> **fantab said:**
> If you have a spare partition to spare then Yes you can.
Just remember to install the grub from ubuntu to its own partition. Otherwise it will replace the grub from Debian and install its own grub. Then if and when you remove Ubuntu you will have to re-install debian grub.

Thanks fantab; can send me to where i have detail info how to go about it,thanks

---

### Post by fantab on 2013-10-23
Its simple. When you are installing Ubuntu use 'Something Else' option to manually control your install and partitioning. On doing so you will be presented with a dialog where you will select the partition you want to install ubuntu to. At the bottom of the dialog you can choose where you want to install your grub to, just select the partition you are installing ubuntu on from the drop-down menu. Thats it.

Remember, after installation when you reboot you will NOT see Ubuntu in the Grub. You will have to boot into Debian and update-grub, because Debian-Grub is in control and it needs to update to show Ubuntu. I don't know if 'os-prober' is installed by default in Debian. If it isn't then install it.

---

### Post by su:bhatta on 2013-10-23
Debian 7 has a os-prober in built. I am using the 2 togather and Debian7 cd came with os-prober. So that will not be a problem.

Once Ubuntu is installed and grub is installed in Ubuntu partition, restart and boot into debian and run update-grub as a superuser.

Here is the Ubuntu 13.10 installation guide: [http://www.ubuntu.com/download/desktop/install-desktop-latest](http://www.ubuntu.com/download/desktop/install-desktop-latest)

Also, have a look at this installation guide: [http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/](http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/)

**Step7-C** in that guide is the screenshot where you can choose where the grub is installed from a dropdown menu at the bottom of the **Installation Type** window. Ensure you choose your partition where you are installing Ubuntu as the drive where Grub is installed.

---

### Post by frank18 on 2013-10-23
> **bhattabhishek said:**
> Debian 7 has a os-prober in built. I am using the 2 togather and Debian7 cd came with os-prober. So that will not be a problem.

Once Ubuntu is installed and grub is installed in Ubuntu partition, restart and boot into debian and run update-grub as a superuser.

Here is the Ubuntu 13.10 installation guide: [http://www.ubuntu.com/download/desktop/install-desktop-latest](http://www.ubuntu.com/download/desktop/install-desktop-latest)

Also, have a look at this installation guide: [http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/](http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/)

**Step7-C** in that guide is the screenshot where you can choose where the grub is installed from a dropdown menu at the bottom of the **Installation Type** window. Ensure you choose your partition where you are installing Ubuntu as the drive where Grub is installed.

Thanks,i apreciate, The installation of ubuntu or Debian on Imac  ppc G5 is diferente from those links given obove although the effect is the same,
here some pics of the way debian ppc was installed,,,on Lubuntu,Ubuntu  ppc it's almost the same exept the first screen pic and the pic # 12 where i have the option of Desktop invironment and printer server,and others on ubuntu or lubuntu i'm not given the  offer of desktop environment option, and i install all the software just like in the screen pics, it hangs at the end with terminal and requesting Name and pasword  log in ,i just don't know how to get to the desktop, if you guys know what commands do i need please post,thanks 

[http://www.tecmint.com/debian-gnulinux-7-0-code-name-wheezy-server-installation-guide/](http://www.tecmint.com/debian-gnulinux-7-0-code-name-wheezy-server-installation-guide/)

---

