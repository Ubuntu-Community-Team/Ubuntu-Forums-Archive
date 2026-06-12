---
title: "ubuntu 12.04.4 installation problems in VMware workstation 10"
date: 2014-03-06
forum: Installation &amp; Upgrades
---

### Post by jasjohnson on 2014-03-06
Hello, I am new to Linux and I am trying to teach myself how to use it. I am trying to install the ubuntu 12.04.4 desktop-i386.iso on a vmware workstation 10. My host machine is a Windows 7 64bit hp laptop. All seems to go good until I power up the vmware virtual machine. When I first power up the machine I get the following popup window message is displayed. 

"Could not prepare the instal disc at C:\location. Make sure that you are using a valid Linux install disc. If this error persist, you may need to reinstall VMware Workstation"

When I restart the virtual machine I get the purple background for a little bit and then the following message.

"EDD: Error 0400 reading sector 361815

Invalid or corrupt kernel image.
boot: _"

Any help appreciated.

---

### Post by ajgreeny on 2014-03-06
Did you check the .iso file you used for the VM installation against the hashsums at [https://help.ubuntu.com/community/UbuntuHashes?](https://help.ubuntu.com/community/UbuntuHashes?)

---

### Post by jasjohnson on 2014-03-06
I just checked the hashsums and they did not compare. So now what do I do? Keep downloading the iso file from ubunta until the hashsum compare is good?

---

### Post by ajgreeny on 2014-03-06
Download using a torrent client which will ensure that the downloaded file is a good copy.

---

### Post by jasjohnson on 2014-03-06
I just download the file and the MD5 Sum did match and the ubunta installed on the vm. Thanks for the help. I didn't want to believe the file was corrupted.

---

### Post by ajgreeny on 2014-03-07
> **jasjohnson said:**
> I just download the file and the MD5 Sum did match and the ubunta installed on the vm. Thanks for the help. I didn't want to believe the file was corrupted.

It happens too often when using a standard http download if your ISP web quality is not as good as it ought to be.  A torrent checks the file packets as it is downloaded and if any of those do notmatch gets just that part again, saving time and bandwidth.

---

