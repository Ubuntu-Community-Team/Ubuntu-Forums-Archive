---
title: "install Ubuntu from USB Key to HDD"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by Antal on 2008-09-30
Hi Guys,

Hope you can assist me with this, I am trying to install Ubuntu onto my hdd from a usb key but the installation seems to run as a livecd only. 

What I mean is, that when I use the info from this link ([https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick))
 the machine boots fine using the Unetbootin app, starts to install and I get to the part where I get to choose the partitions. The only partition/hdd it recognises though is the USB stick itself. Cancel out of the installation brings me into a Ubuntu LiveCD enviroment. Unfortunately it doenst recognise my nic outta the box, using a new Intel Mini itx mobo, the DG45FC. 
([http://www.intel.com/Products/Desktop/Motherboards/DG45FC/DG45FC-overview.htm](http://www.intel.com/Products/Desktop/Motherboards/DG45FC/DG45FC-overview.htm)).

Any ideas how I can install from USB key to HDD ?

Thanks!

---

### Post by arkticcool on 2008-09-30
Trust me, it would be best if everyone tried to uncomplicate everything they did. Download an .iso of Hardy Heron, or use the one you already have and create and use a LiveCD.

I've never installed through a usb so I don't quite understand what the problem is. However I do have a link that can help you dual-boot with XP and Ubuntu (XP installed first):

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm")

NOTE: This is with a LiveCD.

---

### Post by Antal on 2008-09-30
Thanks for your repsonse, unfortunately my mobo doesnt allow for an ide cd-rom drive to be used and I dont have access to a USB cd-rom drive.

I therefore tried the USB key thingie.

On your link my install will stop on 'page 3' ( [http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=3](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=3) ) as the only drive recognised is the USB key.

It doesnt show any of the hdd installed on the machine.

Like I stated, I want to install from USB key to HDD.

---

### Post by webaake on 2008-09-30
I've recently installed from a 2 GB USB stick successfully, formatted a drive on Shuttle KPC 45.

I used the isotostick.sh script, which worked fine with Ubunut and Xubuntu 8.04 Live CD's. It did NOT work with server or alternate install CD's due to a bug in them.

Borrowd from Indrawan:

Here we go…

1. Download file isotostick.sh:

wget [http://www.startx.ro/sugar/isotostick.sh](http://www.startx.ro/sugar/isotostick.sh)

2. Change the permission:

chmod u+x isotostick.sh

3. Before running the isotostick file, we have to make our usb stick bootable or the script will generate error “The partition isn’t bootable” (or something like that):

sudo parted /dev/sdb set 1 boot on

(BE CAREFULL :”/dev/sdb” is my usbstick location, change it when necessary)

4. And the final step is execute the script:

sudo ./isotostick.sh ubuntu-7.10-desktop-i386.iso /dev/sdb1

(i have the iso in my current location, and again “/dev/sdb1&#8243; is our destination, our usb stick location)

5. Umount our usb stick, plug it when power off, and then power on. Violla….our usb stick is now working as Live CD..

Hope it works..

Greetings from Indonesia

Indrawan

---

### Post by unni on 2008-09-30
I followed the steps given [here]("http://www.teamteabag.com/2008/03/07/install-ubuntu-804-hardy-heron-from-usb/") for installing Kubuntu 8.04 (using Kubuntu 8.04 DVD iso). It worked perfectly.

---

### Post by caljohnsmith on 2008-09-30
From what you descibe I think you might be misunderstanding the purpose of UNetbootin; UNetbootin is used to create a bootable USB drive that will boot and work the same as the Live CD. In other words, it is like putting your Live CD on a USB drive. Once you do that, you can boot from the USB drive, and then use that to install Ubuntu to your HDD. Is this maybe what you are looking for?

---

### Post by Antal on 2008-09-30
> **caljohnsmith said:**
> From what you descibe I think you might be misunderstanding the purpose of UNetbootin; UNetbootin is used to create a bootable USB drive that will boot and work the same as the Live CD. In other words, it is like putting your Live CD on a USB drive. Once you do that, you can boot from the USB drive, and then use that to install Ubuntu to your HDD. Is this maybe what you are looking for?

Thanks guys!

You correctly state that I want to install from usb drive to a hdd.

I will try the above mentioned versions too!

Cheers!

---

### Post by Antal on 2008-09-30
Will guys, i gut it sorted, usual fault...my bad... changed from IDE to AHCI and now it shows the disks...

Sorry! *blush* blushh*

---

