---
title: "Ubuntu VM missing grub, on repair-boot network mirrors are unavailable"
date: 2012-08-24
forum: Installation &amp; Upgrades
---

### Post by essefbx on 2012-08-24
Hello,

So I duplicated a Ubuntu server 12.04 vm with Vmware Converter. The conversion fails at 99% due to this error:

FAILED: An error occurred during the conversion: 'GrubInstaller::InstallGrub: /usr/lib/vmware-converter/installGrub.sh failed with return code: 1, and message: FATAL:
kernel too old Error running vmware-updateGrub.sh through chroot into /mnt/p2v-src-root '

when booting the vm it says no operating system found.

So I booted the vm using an image of Ubuntu Server to do a repair boot.
when accessing the root shell sudo apt-get update receives a bunch of failed to fetch errors and temporary failure resolving "whatever mirror".

switched the network adapter from E1000 to VMXNET 3 and still can't resolve the mirrors.

The machine has a statically assigned IP and dns, Which resolves the host name on set-up. I can also ping the server from my local, but can't ping anything from the server.

Any ideas?

edited /etc/hosts and etc/hostname to contain new host name but still getting failed to resolve errors.

---

### Post by darkod on 2012-08-24
When you say you can't ping anything, does that include public IPs or only domain names?

Try:
ping 8.8.8.8
ping yahoo.com

If pinging the IP works, you have internet access. If despite that pinging the domain doesn't work, the DNS servers are not set up properly on your server so there is nothing to resolve yahoo.com for it.

Take a look in /etc/network/interfaces and in case you are using static IP make sure you have a line specifying the DNSs like:
dns-nameservers x.x.x.x y.y.y.y

---

