---
title: "Lexmark X1110 stops working after distro upgrade"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by matteo.cacciola on 2011-04-30
Dear friends of the forum, after upgrading my ubuntu station to Natty, scanner of my multifunctions Lexmark X1110 stopped working. I mean that the device still operates correctly as printer, but the scanner is not found. Before upgrading, under Maverick, all functions of X1110 worked correctly

Here is the result of scanimage -L command
```

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```But if I type sudo lsusb, here is the reply of the terminal
```

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 004: ID 046d:08af Logitech, Inc. QuickCam Easy/Cool
Bus 006 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 010: ID 043d:007b Lexmark International, Inc. InkJet Color Printer
Bus 005 Device 009: ID 043d:007c Lexmark International, Inc. Lexmark X1110/X1130/X1140/X1150/X1170/X1180/X1185
Bus 005 Device 008: ID 043d:007a Lexmark International, Inc. Generic Hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```It means that the device is found: that's why the printer works correctly, after installing the right drivers. Thus, I run on terminal sudo sane-find-scanner -p. Here is the result
```

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x046d, product=0x08af) at libusb:006:004
found USB scanner (vendor=0x043d, product=0x007c, chip=rts8858c) at libusb:005:009
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # No Mustek parallel port scanners found. If you expected something
  # different, make sure the scanner is correctly connected to your computer
  # and you have apropriate access rights.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```Please, note that sane-utils and xsane are installed, saned user is present and enabled within /etc/default/saned, and the demon is started by the command
```

sane-port    stream    tcp    nowait    saned:saned    /usr/sbin/saned saned

```included within the file /etc/inetd.conf.

After all these attempts, I completely uninstalled xsane and sane-utils, trying to make a scan by using simple-scan package, unsuccessfully. I installed again xsane and sane-utils, applying the configuration they had under maverick, but still unsuccessfully. 

I verified that the driver lexmark in /etc/sane.d/dll.conf was uncommented. Any idea on how to solve this issue, please?

---

### Post by mörgæs on 2011-05-01
I would begin with a fresh install of 11.04.

---

### Post by matteo.cacciola on 2011-05-01
Mörgæs, I really thank you, but I cannot, since the PC has root and /home within the same partition, unfortunately. Please, give me a help

---

### Post by mörgæs on 2011-05-01
The fraction of the Ubuntu users who have this printer/scanner at home is close to zero. Hence you must be more than lucky to get an exact answer.

What I and a lot of other users can offer is systematic and analytic troubleshooting, eliminating sources of error as we go along.

---

### Post by wellzel on 2011-05-03
I got Lexmark as well and yes they are not the best printer for Linux dists You dont have an old version of ur conf file. I used the old one and it worked after upgrade

---

### Post by matteo.cacciola on 2011-05-03
wellzel, the conf file of the printer? the cups demon? please let me know, thanks

---

### Post by rasmus_olsen on 2011-05-05
I have the same problem with my Lexmark X1130. Scanner worked before upgrade now its nor working.

---

### Post by wbar2 on 2011-06-09
I have the same issue with Lexmark X4650. After the upgrade, sane-find-scanner finds it, but scanimage -L does not. I looked through /etc/sane.d/ and found that the configuration file was still there. I also looked at /etc/sane.d/dll.conf and saw that it was listed in the file.

---

### Post by wbar2 on 2011-06-11
I was able to get mine going again by redownloading the driver from the Lexmark support site. I went into Synaptic and uninstalled the old driver. I closed Synaptic and ran the new driver installation. After that mine worked again.

Give this a shot and let us know how it goes.

---

### Post by killerisation on 2011-07-14
wbar2, would u mind giving us a more thorough howto to do that?
I have a x1180 that has the same problem.

---

### Post by wbar2 on 2011-07-15
I don't know what the procedure for x1110 is, but for my x4650 the following worked.

The easiest thing to do would be to uninstall with the following command in the Terminal:

```
sudo dpkg -r lexmark-08z-series-driver
```

Then I went to support.lexmark.com and found my printer's linux driver and installed it. They have a driver for x4650, but I don't see one for x1110.

---

### Post by omunozsj on 2011-07-26
I also have an X1185 and stop working after upgrade. I did uninstall sane, xsane, simple-scan and reinstall all of them. Didn't work yet.

---

### Post by ddastoor on 2011-07-26
would this be a pointer, but it's just for the printer part.. 
maybe it will work for the scanner as well ?

[http://ubuntuforums.org/showthread.php?t=49714]("http://ubuntuforums.org/showthread.php?t=49714")

[http://ubuntu-art.org/content/show.php/Lexmark+driver+pack+for+ubuntu?content=98648]("http://ubuntu-art.org/content/show.php/Lexmark+driver+pack+for+ubuntu?content=98648")


this may work, and if the existing printer also stops working, do u have to then re-run the update manager to get back to t he earlier state ? anyone ?

---

### Post by killerisation on 2011-09-12
bump
(scanner still not responding to scanimage -L)

---

### Post by Scoobin on 2011-09-12
There is a relatively painless fix for Ubuntu Natty users on the following Launchpad ticket, by using the libsane and libsane-extras packages from Debian Squeeze.

Mixing packages from different distros is generally not advisable, but in this case there is little chance of complications (sane is not a core system library).

[https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/774475?comments=all](https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/774475?comments=all)

---

### Post by killerisation on 2011-09-12
Works! Thanks very much :)

---

### Post by itagomo on 2011-09-28
nice this link worked ! BIG THANKS to Scoobin !

guys please mark this thread as SOLVED !

---

### Post by TedinOz on 2011-10-01
Thanks to everyone here! I did have to uninstall later versions of libsane via Synaptic before installing the older versions but after they were installed and confirmed, my Lexmark X1195 was detected and I can now open and run Xsane. These forums are bl***dy marvellous!

Thank You!

---

