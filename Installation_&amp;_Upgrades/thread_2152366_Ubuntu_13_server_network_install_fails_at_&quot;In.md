---
title: "Ubuntu 13 server network install fails at &quot;Install the system&quot;--"
date: 2013-06-07
forum: Installation &amp; Upgrades
---

### Post by mikepeon on 2013-06-07
Hi!

I'm doing an install from ubuntu-13.04-server-amd64.iso with PXE boot and http mirror. However, it fails at the "Install the system step". I've tried this from VMWare (both server and client) and in real machines (again, both real machines in a LAN), so it's not likely to be a HW issue. Any suggestions?

Setup:
* DHCP, TFTP with dnsmasq. Serves the netinstall ISO for Ubuntu 13
* Apache2 servs the contents of ubuntu-13.04-server-amd64.iso thru the network
* Expert install
* Client machine boots up from network, detects the mirror, downloads installation packets perfectly, and then, at the "Install the system", fails with this message:
"An installation step failed. You can try to run the failing item again from the menu, or skip it and choose something else. The failing step is: Install the system"
* Going to the virtual console 4, I get:
INFO: Menu item 'live-installer' selected    --> Notice I selected "normal", not "live"
error: Could not find any live images
WARNING **: Configuring 'live-installer' failed with error code 1
WARNING **: Menu item 'live-installer' failed.
kernel: [140.294528] sda6: WRITE SAME failed. Manually zeroing.


In the same setup, the Debain 7 install works.
Thank you a lot!

---

### Post by gordintoronto on 2013-06-07
Must you use PXE?

---

### Post by mikepeon on 2013-06-08
> **gordintoronto said:**
> Must you use PXE?

Yes, because the machines are in a different building, quite far apart. I control the installation thru a virtual KVMs. (Any other option?)

The point is that PXE seemed to work perfectly. The error arises at a later point, reading the files from the mirror. At the beginning, the installer is able to access the installer components, but it somehow fails to identify the files for the base install.

I've copied the whole Ubuntu 13 server ISO into the apache directory, at /var/www/ubuntu. I've checked that I can access any files thru http manually.

Any ideas.

(Thanks a lot!)

---

### Post by mikepeon on 2013-06-10
Just in case it can help anybody on assisting me, I've tried with Ubuntu 12.04.2 LTS Server and the same procedure works perfectly (PXE-TFTP boot plus HTTP for the mirror).

Thanks again!

---

