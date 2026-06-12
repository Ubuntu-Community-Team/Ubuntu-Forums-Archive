---
title: "2TB Bootable USB 3.0 Stick Problems"
date: 2020-05-28
forum: Installation &amp; Upgrades
---

### Post by khidden on 2020-05-28
Hi folks, 

I need some help. I built a bootable USB stick that worked, but was only a 20mb stick and it's only USB 2.0 and was extremely slow. I decided to purchase a USB 3.0 USB stick to help make it faster and decided to get a very large one, so I chose a 2Tb. I cannot seem to get Ubuntu installed on it. I was thinking that there may be a size limitation, because using Rufus, or balenaEtcher it fails just about 1/2 way through. I thought I had a stroke of genius and decided to rebuild my original Bootable USB stick and clone it to the new stick. It still doesn't work and I'm not sure why. Does anyone have some advice for me? I would really appreciate any help I can get from here!

Thanks,

Karl

---

### Post by oldfred on 2020-05-28
Did you really pay over $1000 for a flash drive?
[https://www.digitaltrends.com/computing/largest-flash-drives/](https://www.digitaltrends.com/computing/largest-flash-drives/)

If you paid a lot less, it may be one of the fake drives where they take a much smaller drive, and internally get it to say it is large, but really is not.

For that price you have have a nice sized external SSD. And flash drives are slow and have limited life.

When I built my system 4 years ago M.2 NVMe drives were expensive, so I installed a M.2 SSD. I just upgraded to a new NVMe drive internally and purchased an inexpensive M.2 USB3 case. Almost as fast as as when SSD was an internal drive. My flash drives are are a lot slower. A full install to flash drive is 40Min+, install to USB SSD 10 Min+, internal SSD is bit less than 10 min.

---

### Post by C.S.Cameron on 2020-05-28
Why put a persistent install on a drive that size?
You can do a Full install to the drive and still have almost 2TB left over as a NTFS data partition.
See: [https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step)

Edit:

balenaEtcher will use 3GB for the OS and leave no space for anything else.

Rufus can provide a persistence partition but you will not be able to use it for data on a Windows machine.

If you really want a persistent drive, install mkusb on your 20mb stick and use that to create your 2TB drive,
Mkusb will make a persistence partition and a NTFS data partition.
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

