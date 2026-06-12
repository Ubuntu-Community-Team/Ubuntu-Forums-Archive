---
title: "Automated install of Ubuntu Desktop 16.04 via live CD"
date: 2016-05-28
forum: Installation &amp; Upgrades
---

### Post by tylerecouture on 2016-05-28
I am trying to setup my High School classroom as a Linux lab.

  I have a working PXE boot, and can successfully install the 16.04 Desktop via PXE and NFS.

  Now I'm trying to automate the install, and I can't get past the installation's "Welcome" screen that asks for my language, although I can get that screen to automatically pop-up (instead of having to double click the install icon)

  I've read through: [https://wiki.ubuntu.com/UbiquityAutomation](https://wiki.ubuntu.com/UbiquityAutomation) and [https://help.ubuntu.com/16.04/installation-guide/amd64/apbs01.html](https://help.ubuntu.com/16.04/installation-guide/amd64/apbs01.html)

  This is my pxe boot command:
  ```
LABEL Ubuntu 16.04 64-bit -- PRESEED
        KERNEL Ubuntu/16.04/amd64/vmlinuz.efi
        APPEND automatic-ubiquity file=/srv/install/ubuntu/16.04/amd64/preseed/custom.seed boot=boot=casper netboot=nfs nfsroot=myip:/srv/install/ubuntu/16.04/amd64 initrd=Ubuntu/16.04/am64/initrd.lz
```
  And here is the top of custom.seed
  ```
ubiquity languagechooser/language-name select English
ubiquity localechooser/supported-locales multiselect en_US.UTF8
d-i debian-installer/locale string en_GB.utf8
```
  But these does seem to be enough to get past the installer's first question.

  How can I get past the first Welcome/language screen?

I understand it is possible to do this with the netboot image rather than the live cd, but I would like to know why I can't get this to work, because it seems like it should!

---

### Post by sudodus on 2016-05-29
Welcome to the Ubuntu Forums :-)

Nice that the PXE boot works for you. Maybe I don't really understand what you want. Do you want to carry the live CD to each computer and run the setup (but without having to select options and press the Enter key)? Or do you want to do it via the network somehow?

One way to set up a classroom is to first install a master OEM system, that does what you want it to do, and then clone it. If there are no proprietary drivers, an installed system will work in various computers. The system is portable. The hardware will be identified by the linux kernel and built in drivers will be selected. In some cases you may have to install proprietary drivers.

It is even possible to create installed systems, that boot both in BIOS mode and in UEFI mode.

See these links,

[Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

[OBI, look for the tarballs Lubuntu_16.04_oem-intel.tar.xz and Lubuntu_16.04_oem-intl_amd64.tar.xz](https://help.ubuntu.com/community/OBI)

-o-

Instead of using compressed image files or tarballs, you can also make a compressed image of your OEM installed system with Clonezilla, and make cloned copies from the Clonezilla image. (Such an image is a directory with a number of files.)

[http://www.clonezilla.org/](http://www.clonezilla.org/)

Clonezilla can be run locally from a live CD or USB drive, but also via the network in a more advanced way, 'Multicast'. (I have only used Clonezilla locally from live CD and USB drives, but I have used it for several years.)

---

### Post by tylerecouture on 2016-05-29
Hi and thanks for the reply!

I am using the livecd image (standard ubuntu desktop download) to pxe boot over the network with tftp.  I'll look at the Multicast.  My goal is the unattended install of 30-60 computers.  I just got the netboot image working (unattended install via preseed), because it doesn't have the Ubiquity installer and the seed file works fine.  It's Ubiquity that's causing me the problem.

---

