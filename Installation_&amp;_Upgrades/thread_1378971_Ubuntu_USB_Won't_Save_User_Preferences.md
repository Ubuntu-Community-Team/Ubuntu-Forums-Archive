---
title: "Ubuntu USB Won't Save User Preferences"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by Dynamata on 2010-01-12
I installed Ubuntu 9.10 on a USB stick using UNetbootin but my user preferences aren't saved from session to sesssion. :roll:

---

### Post by Vignesh S on 2010-01-12
As far as I know, UnetBootin doesn't allocate space to save one's settings. If you want to boot Ubuntu via USB, then going to System ----> Administration ----> USB startup disk creator is what you are after. It is more tailored to getting Ubuntu onto your USB, with storage space to save all of your personal preferences. Be careful that you chose the right USB, or to be on the safe side, only put 1 USB flash drive into your computer while this is happening, because it doesn't give any warning that using it might potentially corrupt the USB :-O

---

### Post by Dynamata on 2010-01-12
I pre-partitioned & formatted a Patriot Xporter 8GB USB stick:
1GB(boot-FAT32 label=casper-rw)/500M(swap-FAT32)/5.9GB(home-ext4).

I tried installing from Ubuntu Live CD but USB stick wouldn't boot. :roll:

---

### Post by PRC09 on 2010-01-12
I dont think you can install Ubuntu that way as it doesnt identify it as a hard drive(I think).You can however use the built in usb disk creator as stated in a previous post above.The following link shows how.Yes it is for 8.10 but the instructions are the same.....



[http://www.howtoforge.com/installing-ubuntu-8.10-on-your-usb-flash-drive](http://www.howtoforge.com/installing-ubuntu-8.10-on-your-usb-flash-drive)

---

### Post by C.S.Cameron on 2010-01-12
This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext3 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, removed CD, rebooted.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Changed desktop background, connected to wireless and installed FontForge.
Rebooted, changes were persistent.

Yes, most modern computers do see a flash drive as just another HDD and a full install using the install option from the Live CD or Live USB will work just fine but may take a bit more roo than the above method.

---

### Post by Herman on 2010-01-12
A full install is the best, and simple to do as well.

Either GRUB2 or PLOP Boot Manager can boot USB drives in some computers and can't normally boot a USB.

---

### Post by Dynamata on 2010-01-12
The USB Startup Disk Creator install booted but didn't save settings. Will try UNetbootin again, although I had hoped to avoid the horror of editing scripts.

I will install to HD eventually but I don't have a spare one right now.

---

### Post by C.S.Cameron on 2010-01-12
With usb-creator you need to check "stored in reserved extra space" to get persistence from a simple install. 
Space should be less than 4GB as this is the file size limit in FAT32.
The method I mentioned above also works with usb-creator to make a persistent install of over 4 Gig.

---

### Post by Dynamata on 2010-01-12
Followed the UNetbootin instructions but could not find syslinux.cfg (used search & whereis). Cannot also find USB partition sdb1 in file system, must be hidden.

---

### Post by Dynamata on 2010-01-12
Found it! when I tried to mount sdb1 I got:

mount: according to mtab, /dev/sdb1 is already mounted on /cdrom

I didn't realize cdrom referred to the USB drive, however syslinux.cfg is read only & I can't change permissions because I am not owner. Have to do some more reading. :P

---

### Post by Dynamata on 2010-01-13
I have been trying for hours but I cannot make syslinux.cfg writable. It is owned by root but "gksudo gedit syslinux.cfg" does not work.

---

### Post by Dynamata on 2010-01-13
Seems like I have a Read-only file system so I am not going to waste any more time on this. I'll install Ubuntu on a Hard Drive & see how that goes.

---

### Post by Dynamata on 2010-01-14
Found this:

It is important to mention that Live Linux USB flash drives created with this tool (UNetbootin), do not currently utilize a persistence feature. The resulting USB Linux install will function just as it does from a CD. By default you will not be able to save and restore your changes.

[http://www.pendrivelinux.com/using-unetbootin-to-create-a-live-usb-linux/](http://www.pendrivelinux.com/using-unetbootin-to-create-a-live-usb-linux/)

---

### Post by Dynamata on 2010-01-15
Here is a solution using Linux Live USB Creator:

[http://www.pendrivelinux.com/linux-live-usb-creator/](http://www.pendrivelinux.com/linux-live-usb-creator/) 

[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) :cool:

---

