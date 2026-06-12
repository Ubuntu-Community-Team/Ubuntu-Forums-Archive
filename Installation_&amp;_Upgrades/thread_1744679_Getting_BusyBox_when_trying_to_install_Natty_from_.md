---
title: "Getting BusyBox when trying to install Natty from USB"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by eks on 2011-04-30
I've tried both the DVD and CD, the CD with both usb-creator-kde and unetbootin. The results are the same always, the USB boots, into the splash screen, I select Start Kubuntu, it goes to the loading screen. After some seconds it starts scrolling a wall of text, gives some error about not being able to write or read /root/var/* because they don't exists and end up on a BusyBox with (initramfs) prompt.

What gives?

I need to install the system on a new disk (2tb) instead of upgrading because I have to send the current one (1tb) to replacement. Could the large 2tb disk be a problem? I tried unplugging all disks and leaving just the disk I want to install to, but no deal... (both are SATA).

(Checked the md5sum and they both match for DVD and CD...)

---

### Post by Quackers on 2011-04-30
Wehn booting, at the first purple screen (with the little man icon at the bottom) press any key. Choose your language and on the next screen select the cjeck for defects option. It doesn't matter whether you are using a cd or a usb, the process is the same. Any error found is bad.

---

### Post by eks on 2011-04-30
Tried pressing a key, esc worked, but the result was exactly the same. The wall of text begins to scroll and ends up at the attached "photo"shot.

What could generate this errors?

---

### Post by Quackers on 2011-04-30
Are you trying to boot from a live cd/usb or trying to boot an installed version from the hard drive? It looks like the latter from those messages, but I could be wrong.

---

### Post by eks on 2011-04-30
From a 8gb USB. I've used it to install Ubuntu and Kubuntu everywhere, but it was last formatted to NTFS so I could get some files from work (larger than 4gb). I just formatted it today with gparted back to fat32, could try formatting it again. Or to ext2/3...

---

### Post by Quackers on 2011-04-30
I would try formatting it again and burning the iso image again. It doesn't look too good from here.

---

### Post by eks on 2011-04-30
Thanks for the support Quackers, but... bad news...

I've tried formatting in ext2 and Kubuntu 11.04. Exactly the same problem and the same result as on the screenshot. Then formatted back to fat32 and tried Ubuntu 10.10 to test to see if the problem might be the USB stick, since I had used that configuration to install it already, and it worked... So it's not the USB or the file system.

Any ideas of what the problem might be? I see it's only me with this problem, have googled this a while and couldn't find anyone getting into BusyBox during the installation, I really thought it could be the USB stick...

I will try to install Kubuntu 10.10 and then upgrade it then.

---

### Post by Quackers on 2011-04-30
Sorry, I don't know. I haven't seen a Busybox when booting from a live cd/usb before :-(

---

### Post by wm_brant on 2011-05-01
Are you using a SanDisk USB drive with U3 software on it? I fought a very similar problem this weekend until I read:

"11.04 Natty Narwhal installation does not work with [SanDisk]("https://help.ubuntu.com/community/SanDisk")'s USB drives with U3 Launchpad present, you need to remove it either with u3-tool from Ubuntu Repositories or [SanDisk's tool]("http://u3.sandisk.com/launchpadremoval.htm") to be able to use it. All other brands of USB drives work."

From: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by omns on 2011-05-02
Same problem here with USB. I also get it from a boot cd. Perhaps a bad download.

---

### Post by Kangarooo on 2011-05-22
If flash made bootable it doesnt matter what else is there.
and heres the bug [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/773304](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/773304)

---

