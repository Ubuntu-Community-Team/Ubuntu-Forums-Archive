---
title: "USB drive became corrupted while setting up live USB"
date: 2022-10-06
forum: Installation &amp; Upgrades
---

### Post by JustSomeCanuck on 2022-10-06
Hello everyone!

This is an unusual one. I decided to upgrade an old laptop with an SSD and start with a fresh install of Ubuntu 22.04. The first time I tried to set up the USB with the startup disk creator, an error message appeared saying this particular USB drive couldn't work. I didn't keep a record of the exact message. I was able to complete the installation with a different USB drive (set up using Rufus on a Windows PC), but I've tried to restore the original one and the drive seems to have become corrupted somehow. I've tried all of the usual format methods on Ubuntu and Windows to try and restore it.

I think the USB still works, because when i connect it to a computer (Ubuntu or Windows) it is recognized. Using Disks it shows as having a partition and I can eject it normally, but I can't move files to it. In Windows, a message appears saying I need to format it.

This all happened with a spare USB that wasn't being used for anything, but it would be nice to recover it if at all possible. Anyone know what might be going wrong with it? I'm mostly worried that this could happen the next time I try to make a live USB.

---

### Post by ian-weisser on 2022-10-07
Seems like classic symptoms of a faulty USB drive.

They do go bad as their components age and wear, and it sometimes looks a lot like that.

---

### Post by yancek on 2022-10-07
What filesystem type do you have on the usb?  If windows is suggesting you format it, I would think it has a Linux filesystem.  When you say 'recover', does that mean recover it to be used again because as I read your post, there is no data on it.  Have you tried using GParted or similar software to create a new partition table on the device?

---

### Post by JustSomeCanuck on 2022-10-07
@ian-weisser: It was a fairly new USB stick, and it hadn't been used a whole lot. Unless it was defective from the beginning, which is why it never worked in the first place ¯\_(&#12484;)_/¯

@yancek: I was trying to format it back with the FAT32 filesystem just to use it as a basic USB stick. Yes, there is no data on it. I tried Ubuntu's Disks utility, so maybe I will try GParted next.

---

### Post by ajgreeny on 2022-10-07
You could also try [mkusb]("https://help.ubuntu.com/community/mkusb") which has a facility to return a USB to use as mass storage following its use as an install disk.

It is a very long time since I used startup disk creator, having moved to **mkusb** when it first appeared so I can't recall if its use makes the USBs unusable without first creating a complete new partition table which you could also try in gparted.

---

### Post by sudodus on 2022-10-07
I agree with the advice in the previous replies, and would like to add, that you can **analyze the problem according to [this link](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)** and if you are lucky, find a solution.

---

### Post by JustSomeCanuck on 2022-10-10
Thanks for all of the help. I tried fixing it with mkusb, and it seems to be working again, but I'll be keeping an eye on it. If it's still not 100% healthy, at least I discovered that now before anyone used it for anything permanent!

---

### Post by ajgreeny on 2022-10-10
Beware!
I don't think USB thumb drives are a good way to save anything permanently; they can unfortunately be a lot less reliable than most other storage devices.

---

