---
title: "Ubuntu Server 15.10 hangs on fresh install"
date: 2015-12-08
forum: Installation &amp; Upgrades
---

### Post by joshua63 on 2015-12-08
Greetings,

I've just put together a new system for managing home media content. I burned the latest server installation ISO to a USB drive and was able to run through the installation process with no indicated errors. I am using a Samsung 120GB SSD for the operating system and when prompted allowed Ubuntu to "use the entire disk" for installation. It's worth noting that prior to this the SSD had Windows 7 installed on it.

When the system rebooted, I pulled the USB stick and allowed it to boot into the SSD (keep in mind this is the ONLY drive connected to the motherboard). However, after POST'ing, I'm met with a flashing cursor with no ability to provide any input (no keystrokes or combinations produced anything). 

The motherboard is a Gigabyte GA-H97 and I've attempted to mess around in the bios a few times to force all boot options to use Legacy mode to see if that was the issue, however, I've had no luck. Any recommendations on how to proceed forward here?

---

### Post by joshua63 on 2015-12-08
I resolved this issue using Boot-Repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)). Here was the log if it helps anyone: [http://paste.ubuntu.com/13834733/](http://paste.ubuntu.com/13834733/)

---

