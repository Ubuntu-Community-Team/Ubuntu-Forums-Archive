---
title: "Unattended Install Using WDS and a Shared Folder"
date: 2012-05-17
forum: Installation &amp; Upgrades
---

### Post by glangBESC on 2012-05-17
I am attempting to build an unattended installer using a Microsoft Windows Distribution Server. Using information I found online I have been able to get it setup and running with only one problem, the CD needs to be in the drive for it to work. I would like to know if there is a way to get the installer to access the files from a share so the CD is not necessary.

For example, I have an NFS share called "/nas/softare/ubuntu/12.04LTS" that contains the extracted Ubuntu 12.04 LTS Alternate Installer CD. When I perform a PXEboot, and am prompted to select an option, I want the installer to automatically connect to the NFS share mentioned above to get the files it needs rather than it going to the CDROM. I have searched the Internet for days but the only thing I can find is how to do it using TFTP which is something I would prefer not to do.

In case anyone is wondering, I do have network connectivity during the install because I am pulling the preseed file from a URL and it works as it is supposed to.

This is the content of my menu file and I have attached my preseed file:

LABEL Ubuntu12.04LTS-Install
    MENU label ^Ubuntu 12.04 LTS 64-bit install:
    KERNEL /Linux/Ubuntu/12.04/vmlinuz boot=precise auto=true ramdisk_size=1048576 rw
    APPEND vga=791 initrd=Linux/Ubuntu/12.04/initrd.gz -- preseed/url=http://192.168.65.196/preseed.txt locale=en_US keyboard-configuration/layoutcode=us console-keymaps-at/keymap=us debian/priority=critical netcfg/choose_interface=eth1 netcfg/dhcp_timeout=60 hostname=install domain=bnesystems.com

---

### Post by glangBESC on 2012-06-05
Bump

---

