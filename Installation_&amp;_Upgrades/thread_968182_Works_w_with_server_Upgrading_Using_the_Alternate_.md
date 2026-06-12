---
title: "Works w with server?: Upgrading Using the Alternate CD/DVD"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by jeffk on 2008-11-02
I am upgrading several Ubuntu 8.04.1 servers to 8.10, and would like to use the downloaded ISOs to minimize bandwidth usage.

Is the following section's instructions going to display a dialog for a text-mode upgrade that will continue unabated without dropping the network connection?

> **_[Upgrading Using the Alternate CD/DVD](http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD)_**

Use this method if the system being upgraded is not connected to the Internet.

   1. Download the alternate installation CD

   2. Burn the ISO to a CD and insert it into the CD-ROM drive of the computer to be upgraded.

          * If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by mounting the ISO as a drive with a command like:

            ```
sudo mount -o loop ~/Desktop/ubuntu-8.10-alternate-i386.iso /media/cdrom0
```

   3. A dialog will be displayed offering you the opportunity to upgrade using that CD.

   4. Follow the on-screen instructions.

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

```
gksu "sh /cdrom/cdromupgrade"
```
I also would like to run a final aptitude update/full-upgrade before reboot to catch any late kernel and assorted releases before rebooting these remote machines.

---

