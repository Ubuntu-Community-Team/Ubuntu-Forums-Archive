---
title: "Installing Kubuntu from a flash drive"
date: 2012-08-09
forum: Installation &amp; Upgrades
---

### Post by Kalantir on 2012-08-09
I currently have a persistent Kubuntu 12.04 flash drive that I plan on using to install Kubuntu on my hard drive. However, I am curious whether I can modify the installation by installing and uninstalling software on the flash drive.

For example, if I download applications using apt-get in the live boot usb, will those applications be installed as well?

---

### Post by C.S.Cameron on 2012-08-09
With a persistent thumb drive things are stored in a file named casper-rw.
When installing from the drive, items in casper-rw are not transferred to the install.
You can make a custom install iso using remastersys.

---

### Post by Kalantir on 2012-08-10
Thank you! Can the custom iso created with remastersys be used for a live boot as well or is it just a custom alternate install disc?

---

### Post by mastablasta on 2012-08-10
it's can be a live boot disk (that's how many Ubuntu based distributions came to be)

---

