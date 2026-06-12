---
title: "USB automounting problem?"
date: 2006-02-20
forum: Installation &amp; Upgrades
---

### Post by erakepio on 2006-02-20
Been trying to get Ubuntu 5.10 on my Seagate 40GB USB Hard Drive.  I followed one of the guides posted here on the forum and it installed the OS with no problems at all.  Yet when i attempted to boot it up it said it couldnt find the disk.

i checkd partition menu at for some reason it changed it from "/ " and set it to /media/sda1 which it shouldnt have.  

I then booted up in rescue mode and attempted to edit the boot.lst in the grub folder using vim.  i tried changing the locations each time and then reloading the kernal...rebooting but run into the same problem.."disk doesnt exist".

any help would be much appreciated, cheers

---

### Post by bernardfrancois on 2006-02-20
I think you'll have to edit **/etc/fstab**
You can do that as well in rescue mode I think.

The mount point for your partition should be changed from /media/sda1 to / (unless there already is a root-partition).
Maybe you can first try to do a **ls /media/sda1** and **ls /** to see what's there

---

### Post by erakepio on 2006-02-20
yeh i got a friend of mine to go through that and he says everything looks fine.  He said the problem is that the drive is Auto-mounting itself and that i need to turn it off somehow.

any ideas?

its a seagate 40GB USB drive

---

### Post by bernardfrancois on 2006-02-21
Maybe you can look in your BIOS setup utlilty... Probably you can force your computer there to boot from your USB device (or to have your USB device highest in your boot priority).

---

### Post by erakepio on 2006-02-21
it is set to that in the menu as its top of thelist in boot priority followed by the add-in cards.  it was also the only storage device connected at the time.

i need actually physciall disable, or in worst case scenario kill the automount feature of the USB device..as it automatically changes from "/" to /media/sda1 upon reboot

---

### Post by bernardfrancois on 2006-02-22
If you want to disable automounting I think the solution is to simply mount it manually by adding a correct mount line in /etc/fstab.

The mount line I have for my root partition is the following:
```

/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1

```

The first parameter is the device name of your usb drive (maybe something like /dev/sda or /dev/sda1, I dunno exactly, this is just a guess). The other parameters should be the same as mine. If you want more information, check **man 5 fstab**.

---

