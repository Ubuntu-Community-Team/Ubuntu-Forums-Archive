---
title: "[SOLVED] Install via USB Stick fails, tries to mount CDROM"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by ubuser_7 on 2008-12-01
Hi Everyone

I have been trying to install Ubuntu Server (8.04) on an AMD machine via a 1GB USB Stick. 

I made the installer USB using UNetBootin (listed here: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)). 

Now when I boot from the USB stick, everything goes fine till it reaches the step where it detect and mount a CDROM. It gives me the following message: 

```
Your installation CDROM couldnt be mounted. This probably means that the CDROM was not in the drive. If so you can insert it and try again.

Try again to mount the CDROM?
```

Now, when I say no, it says that the Detect and mount step failed. It shows me a list of installation steps. 

I tried choosing 'Load debconf preconfiguration file' step, but it says that it could not retrieve the file from file:///cdrom/preseed/ubuntu-server.seed

Basically I think I am stuck with that the installer is still trying to find everything from the CDROM and not from the USB after the initial boot from USB. 

Am I missing something? Do i need to some additional steps to make it look for the files from the USB stick instead?

I renamed isolinux, isolinux.cfg to syslinux and syslinux.cfg.

I also tried to mount the USB to /cdrom however was unable to do so. 

Any help will be greatly appreciated!

---

### Post by ubuser_7 on 2008-12-01
Problem solved :).

The things I did (and somehow it worked):

I chose cdrom instead of Install from the initial menu shown by the USB.
When the mount fails i manually mounted my USB to /cdrom (It worked this time around, maybe because i skipped the -t vfat?) 

This was enough to make it find all the files from USB.

---

### Post by solo23 on 2008-12-02
Can you post excatly what it was u typed in, I'm trying to follow the wiki but it doesn't work and ur instructions are not descriptive enough.

# mkdir /cdrom /dev/cdroms
# cd /dev/cdroms
# ln -s ../sda1 cdrom0 (where sda1 is your USB stick)
# mount -t vfat /dev/cdroms/cdrom0 /cdrom


I'm using ubuntu server 8.10

---

### Post by ubuser_7 on 2008-12-02
I just did:

```

mount /dev/<your USB> /cdrom

```

My system showed that my USB was FAT16 (??) and hence I skipped the -t vfat option. Also it was giving me an error with -t vfat (I dont remember the exact error).

I think you will also want to verify what your USB stick is (like sda1 etc.) .

The wiki had mentioned that the mounting is needed only for older versions, but I guess we still need to do it even with the newer versions.

---

