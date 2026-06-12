---
title: "Re-installing Windows 10 after Ubuntu 18.10"
date: 2019-03-08
forum: Installation &amp; Upgrades
---

### Post by yajirobe on 2019-03-08
Hello everybodies, I need your help.
I have Ubuntu 18.10 in my Hp notebook. I need to return to windows 10, without dual boot for the moment.
I downloaded windows installer and woeusb, I tried to do as in some tutorials that I saw, but there is en error message from woeusb that it can't burn the iso into the usb.
I tried to make a bootable usb from a macbook but my system can't see it like boot option in BIOS setup.

How can I solve this situation?
Thank very much

---

### Post by logix2 on 2019-03-08
What's the error you're getting using WoeUSB? The one I used to run into can be solved by this: after you plug-in the USB stick, click on the unmount icon in Nautilus / Nemo or whatever file manager you're using, and then use WoeUSB to write the Windows ISO to the USB.

You can also try to create the Windows bootable USB using [bootiso]("https://www.linuxuprising.com/2018/07/bootiso-easy-iso-to-bootable-usb-drive.html"), a command line tool that can create a bootable USB from Windows or Linux ISOs .That's what I've used the latest time I had to install Windows on some computer, and it worked perfectly.

---

### Post by jdeca57 on 2019-03-08
Actually there is a tutorial on creating bootable usb disks in this forum under tutorials and another link is [https://fossbytes.com/create-bootable-usb-media-from-iso-ubuntu/]("https://fossbytes.com/create-bootable-usb-media-from-iso-ubuntu/") Personally I don't know WoeUSB but there are many alternatives.

---

### Post by anderbuntu on 2019-03-10
I got error from gui woeusb about some 4gb limit > then I fixed this via cmd line woe

[https://askubuntu.com/questions/1097560/woeusb-error-code-256-with-ntfs-formatted-usbsudo](https://askubuntu.com/questions/1097560/woeusb-error-code-256-with-ntfs-formatted-usbsudo) woeusb --target-filesystem NTFS --device /media/lubuntu/usbdata/images/windows.iso /dev/sdx

---

