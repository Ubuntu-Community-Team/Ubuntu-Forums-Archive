---
title: "Save files on USB Live"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by baylors on 2010-07-23
I've been searching for a while to no avail. Just looking for a point in the right direction... I've used UNetBootin to install a live version to an 8 GB jump drive. I'm going to use it to remove viruses from WinBlows machines. It installs, boots, and runs great but I have to install ClamAV each time because it's a live install. How can I turn my USB from live version to one where I can DL and install software once?

---

### Post by C.S.Cameron on 2010-07-24
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

Or you could just use usb-creator booting from the Live CD, it will do a persistent install to flash drive.

---

### Post by nerdtron on 2010-07-24
There's anothe exellent utility for creating persistent USB Live install. I use Linux Live USB creator.
[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)
In just a few clicks and a few minutes you'll have a Live USB of most popular linux distros.

---

### Post by sgosnell on 2010-07-24
My preference is for an actual install to the USB drive, not a LiveUSB version.  With an actual installation, you have a complete OS on the drive, and whatever you change stays that way, just as it would on an internal HDD.  You need two USB drives to do this, or a CD drive in addition to the USB drive.  Install the liveCD/USB to a 1GB drive or CD, then use that to install Ubuntu to the 8GB flash drive.  You can still install Ubuntu from that drive if you want, but it's a good way to just run the OS on any computer.

---

### Post by varunendra on 2010-07-24
Why not just create a Live USB Startup Disk (persistant) from within Ubuntu live session. I do it all the time without any hassle and can't imagine of any quicker and more promising way around!

If you don't already know, here's how to do it:
If you have Karmic or Lucid installed, goto System>Administration>USB Startup Disk Creator. Select your karmic or lucid iso image as source and your usb drive as destination. If it is not already formatted as FAT32, click on 'Format'. Drag the 'Storage space' slider to its maximum limit (if you want more than default storage space) and go!

If you don't have them installed, you can do it through their live CDs (you won't even have to select 'source' this way).

It'll take only as much time as copying the whole iso contents onto the usb disk and will be ready as a persistant live disk! You can install clamav or whatever you want on it and it will stay there.

What C.S.Cameron suggested, creating a separate casper-rw partition (& deleting the casper-rw 'file') is only required if you need more than 4GB (FAT32's filesize limit) of storage space.

---

### Post by baylors on 2010-07-24
Thank you very much! Solved!

---

### Post by baylors on 2010-07-27
> **nerdtron said:**
> There's anothe exellent utility for creating persistent USB Live install. I use Linux Live USB creator.
[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)
In just a few clicks and a few minutes you'll have a Live USB of most popular linux distros.

Did this and worked fine! But now I have another problem... Now on my WinBlows machine I can't just browse the CD\DVD drive anymore. 

Any ideas on how to fix this? Sorry... I know this is a linux forum and I'm asking questions about a different OS, but this is really irritating.

Thanks for any and all help.

---

### Post by baylors on 2010-07-27
Solved myself... linuxlive usb did some registry editing. It changed the association with autorun. If anyone has the same probs... search the registry for linuxlive usb and remove entries that deal with autorun.

---

