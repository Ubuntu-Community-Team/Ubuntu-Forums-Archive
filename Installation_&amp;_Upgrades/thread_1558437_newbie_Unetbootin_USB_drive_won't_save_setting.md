---
title: "newbie: Unetbootin USB drive won't save setting"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by asian_xl on 2010-08-22
I downloaded the latest ubuntu 10.4 iso, then followed the steps in [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) to create a USB bootable drive.

Everything is fine, but it doesn't save my preference setting (wallpaper / theme / desktop icon) after reboot. What did I do wrong?

USB drive: 2gb Avixe


How do I create a USB bootable Ubuntu properly that will save my preference? please provide step by step method.  THANKYOU!

---

### Post by asian_xl on 2010-08-22
no body can help?

---

### Post by asian_xl on 2010-08-23
somehow I find it's something to do with persistent mode .  How do I do that?

---

### Post by C.S.Cameron on 2010-08-23
The usb installer that comes on the Live CD is probably the simplest method of making a persistent install.

If you insist on making an UNetbootin install persistent:

This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext3 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Windows, started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, booted thumbdrive.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.

---

### Post by fnyahoo on 2011-11-16
I cant egit syslinux.cfg file it says read only 

anybody can help here?

---

### Post by gakon77 on 2011-12-17
> **fnyahoo said:**
> I cant egit syslinux.cfg file it says read only

syslinux.cfg is a system file and it's readable only for a good reason. 
Although, you can write on it if are root.

Do you know how to do that?

---

### Post by Dennis N on 2011-12-17
Unetbootin creates a bootable USB that acts like the live CD and installer. Unless they have added a new feature, it does not save your changes between uses (persistence).

If you have access to a computer with Ubuntu already installed, use Ubuntu's built-in USB creator which allows persistence of settings in creating a bootable USB.

Otherwise, if you are working from a Windows machine, study this website for possible solutions:

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

