---
title: "Creating a USB boot stick from an ISO - then reformat back"
date: 2012-03-02
forum: Installation &amp; Upgrades
---

### Post by sselt on 2012-03-02
I would like to manually create a bootable usb stick if possible. And then return the usb stick to it's original format.

I am not currently running ubuntu, but want to create a bootable usb ubuntu from a current downloaded iso.

I know about other programs that can do this such as pendrivelinux, linuxliveusb, unetbootin, startup disk creator....

Can dd do this? If so, is this basically what these programs are doing?
And if so, does the usb stick need to be formatted first?

After using the stick for an install, I would like to return the usb  stick to it's original format. What would be the best way to do this and  what can be used to detect the format of the usb stick prior to  creating the boot stick?

I am not a noob, only not familiar with creating usb sticks. Please feel free to suggest any command line tools and commands.  :)

---

### Post by darkod on 2012-03-03
As far as I know, dd can't create the boot sector on the usb stick that you will need to boot with it. If you have another ubuntu machine at hand, start up disc creator is best I guess.
On windows you can take a pick between unetbootin, universal usb installer, pendrivelinux, etc.

After you are done with the stick, you can simply plug it into any linux or windows machine and just format it as FAT32 or NTFS depending what FS you were using it with before. In fact the boot usb is usually in fat32 so you will only need to do a quick format to delete all the files including the boot sector.

---

