---
title: "Trouble installing Ubuntu 10.10 Desktop or Server on Shuttle XS35"
date: 2011-02-09
forum: Installation &amp; Upgrades
---

### Post by bevel on 2011-02-09
I recently picked up a Shuttle XS35 from NewEgg to act as a central file and print server.

Using the download and install instructions over at the Ubuntu site, I've made myself both a 10.10 Desktop and 10.10 Server bootable USB drives, but both flavors seem to hang for me when trying to install on the hard drive in the Shuttle.

10.10 Desktop gets to the UI screen where it asks you to make sure you have enough room, are plugged in, and have access to the internet. When I click "Forward", an error message appears in the top status bar, stating that there was a "problem in ubiquity" and that it "crashed on an assertion failure".

10.10 Server seems to get a little further along, but stalls when (I think) its scanning the hardware for a final time before installing. At the "Starting up partitioner" dialog, it hangs at 45% of the process, where it states its "scanning disks".

I've searched around for answers, but just keep going in circles and I feel like I'm the only person to ever run into these issues trying to install Ubuntu 10.10.

Yes, booting from the USB works, and the BIOS is configured to USB boot over HDD boot. I have no trouble using the LiveCD version of Ubuntu from the USB, but run into similar issues when trying to install from the 10.10 Desktop installation utility.

I've formatted the HDD from the LiveCD, and mounted it prior to trying the installation, and still get no joy.

Any help would be greatly appreciated :confused:

---

### Post by konnari on 2011-03-06
Exactly the same problem here. I have a Shuttle XS35GT and the Ubuntu 10.10 Alternate installation always hangs at the "Starting up partitioner" dialog, on 37%.

The problem is USB. If I remove the USB from the shuttle just before "Starting up partitioner" phase, the partitioner starts ok. It's possible to make partitions, but the installation fails when it tries to install rest of packages. It can't find the installation media anymore.

Workaround:
- Create the ubuntu installation usb using example Unetbootin or Ubuntu tool.
- Copy original .iso-file to root directory on usb. In my case ubuntu-10.10-alternate-i386.iso
- Reboot from the usb.
- Start the installation.
- Stop the installation before the disk detection and the partitioning phase. Example when prompted a network name. Select "Go Back" and then "Execute a shell" from the main menu.
- Execute shell and copy iso image from usb to memory. Mount iso to cdrom.

```

mkdir /iso
cp -a /cdrom/ubuntu-10.10-alternate-i386.iso /iso/
umount /cdrom/
mount /iso/ubuntu-10.10-alternate-i386.iso -t iso9660 -o loop /cdrom/
exit

```- Remove usb.
- Continue installation.

Hope it works for you also.

---

