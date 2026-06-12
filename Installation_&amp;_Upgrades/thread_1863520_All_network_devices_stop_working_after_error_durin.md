---
title: "All network devices stop working after error during upgrade"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by zahonin on 2011-10-17
Hello,

During the upgrade process my wireless network connection inexplicably stopped working.  Then, several steps of the installation failed due to no network connection while trying to install elements with dropbox support.  The installation could not complete and Kernel version 3.0 will not boot.

I managed to boot into 2.6.35 but both wireless and wired connections do not work.  The interfaces exist but do not appear to be able to connect.  

i.e: The wireless network SSID is visible but cannot connect.  I cannot set even a static IP and ping the router.  DHCP fails on both wireless and wired connections.

Looks like something went awry with the network stack.  Perhaps a mess with the version of the kernel.

Any suggestions on how I can temporarily bring up the network in this configuration to see if I can complete the upgrade with:

apt-get clean
apt-get update

Thanks in advance.

---

### Post by 23dornot23d on 2011-10-17
Check in my links below ... there may already be a solution to this ......

---

### Post by zahonin on 2011-10-18
It doesn't look like it's one of the listed problems.  My wireless card is an Intel 2200b/g.  I did manage to make some progress though...

Kernel 3.0 won't boot.  I managed to bring back the wireless and wired network up with an old 2.6.38 kernel but still get an error of cannot read file, press any key... before it boots.  

Managed to clean up the upgrade with apt-get clean, apt-get upgrade, apt-get update.  

Kernel 3.0 still wouldn't boot.  Says that it cannot find kernel header.  Tried uninstall and re-install of the kernel to no avail.  

Boot Info log is here: [http://paste.ubuntu.com/711600/](http://paste.ubuntu.com/711600/)

If this doesn't work I may just fall back on 2.6.38 if I can figure out how to get rid of that Cannot read file error.

Thanks again.

---

### Post by Serious_Python on 2011-10-18
My upgrade also failed because the network connectivity went down. After a really slow reboot the machine came up and I plugged in the LAN cable. I then did a do-release-upgrade and the upgrade completed successfully.

---

