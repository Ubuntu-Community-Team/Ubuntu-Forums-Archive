---
title: "Installing Windows 8.1 after Ubuntu"
date: 2014-08-30
forum: Installation &amp; Upgrades
---

### Post by ibn5100 on 2014-08-30
I'm trying to install Windows 8.1. Ubuntu was not able to detect my windows so it cleared my entire hard drive to install itself. I'm trying to get windows back, but every attempt of making a bootable USB with the windows ISO file leads to it being undetected in the boot menu. I can see the USB in Ubuntu's file manager though. Can someone help? Is there a specific method I have to use when burning the window's image file or something?

---

### Post by Mark Phelps on 2014-08-30
I've heard about something called RUFUS -- but I've never used it.  You should check that out and see if it will work for you.

---

### Post by fantab on 2014-08-30
Is there a NTFS partition on that HDD?
Post the output of:
```
sudo parted -l
sudo fdisk -l
```

Try [Microsoft Windows 7 DVD/USB download tool]("http://www.microsoftstore.com/store/msusa/html/pbPage.Help_Win7_usbdvd_dwnTool"), it is [compatible with Windows 8]("http://www.microsoft.com/en-us/windows/compatibility/CompatCenter/ProductDetailsViewer?Name=Microsoft%20Windows%207%20USB%2FDVD%20Download%20Tool&vendor=Microsoft&ModelOrVersion=1&Type=Software&tempOsid=Windows+8.1"). It will only work from Windows machine.

---

