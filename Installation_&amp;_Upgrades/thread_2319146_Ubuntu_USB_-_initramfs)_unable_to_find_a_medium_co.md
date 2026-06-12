---
title: "Ubuntu USB - initramfs) unable to find a medium containing a live file system"
date: 2016-04-01
forum: Installation &amp; Upgrades
---

### Post by robartist on 2016-04-01
OK as mentioned i uninstalled lubuntu.

I have now put ubuntu on an external usb 'pen' drive. Created with pendrivelinux yumi.

But now it won't start at all.

I get error:
[h=2]initramfs) unable to find a medium containing a live file system.[/h]

---

### Post by robartist on 2016-04-01
NOT Lubuntu. Ubuntu.

---

### Post by robartist on 2016-04-01
AHA. Ok I have now installed another linux distro - ubuntu mate - onto my external usb pendrive under yumi.

Again it will not boot. Again I get the same message: 
[h=2]initramfs) unable to find a medium containing a live file system[/h]Can anyone please help solve this problem? Thanks

---

### Post by robartist on 2016-04-01
ok. i moved the usb memory stick from usb2 to usb3 and it worked!

I now how ubuntu desktop.

needless to say the wifi isn't working!

right click on trackpad also not working.

any suggestions on how to get them running?

---

### Post by sudodus on 2016-04-01
0. Please tell us about your computer (it makes it easier to help)

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

- Which version of Windows are your running?
- Which version of Ubuntu/Lubuntu are you trying (14.04.4 LTS or another version)?
- Are you running in UEFI mode or the old BIOS mode?

1. Please check that the iso file was downloaded correctly. Check with md5sum according to this link: [UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

2. Try to flash the iso file to the pendrive with another tool. I think cloning is the most reliable method. In linux you can use ***mkusb***, but it seems you are starting from Windows (with ***yumi***). And you can use Win32 Disk Imager to clone from Windows. See the following link

[Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

Good luck :-)

-o-

See the following links (and links from them), if you need more details about booting from USB.

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[Howto help USB boot drives](http://ubuntuforums.org/showthread.php?t=2196858)

---

### Post by sudodus on 2016-04-01
It seems you solved the problem with booting while I was writing my first post (#5 in your thread). Congratulations :KS

Please create a new thread with a good title to address the wifi issue. This thread will probably not get the attention of our wifi experts. [COLOR="#696969"]I'm no wifi expert, I use wired internet.[/COLOR]

And I think you should create another thread for the trackpad issue. :-)

---

### Post by robartist on 2016-04-01
Thank you sudodus. Good suggestion!

---

