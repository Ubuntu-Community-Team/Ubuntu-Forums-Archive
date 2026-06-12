---
title: "PXE Boot Tale"
date: 2015-11-01
forum: Installation &amp; Upgrades
---

### Post by James_Lucid on 2015-11-01
Just wanted to share some interesting tips on what it took for me to install a PXE boot server, on a desktop machine that was unstable due to memory issues (crashing), in order to perform a network install for a HP Elitebook (no cd-drive).
First, I have to mention that it pays off having a pile of hardware scrounge laying around. I discovered that my HP Elitebook's HDD was bad (failed HDD test), so I found a HDD from a MacBook Pro that was busted, but I knew the drive was good. So I removed and replaced the drive and the old drive from the Macbook passed without a hitch. Moving onto my desktop to install the packages that needed to run PXE server failed multiple times, corruption I/O errors, all kinds of issues. I decided to reinstall Ubuntu, this time using 15.10, but the installer kept crashing with a warning saying I should go to the electronics store and buy a dvd cleaner, or to try replacing my HDD if it's "old", whatever.  My suspicion rested with the fact that I only have one dimm in the machine, and that it's probably bad. I drove over to Walmart thinking they had dimms somehow, of course they didn't, but I did pick up a DVD cleaner/brush. Got home and tried the dvd cleaner and repeat the same process, still crashing with the same error (err 5 I/O).  Frustrated, and for whatever reason, I decided to take out the dimm and placed it in a storage freezer bag and into the freezer for approx 10 minutes. After that, I installed it back in the machine and started the install process again, and it worked! It went through the install process and I was able to install ubuntu and all the other packages for the PXE server!  I followed this guide:
[http://www.unixmen.com/install-and-configure-pxe-server-on-ubuntu-15-04/](http://www.unixmen.com/install-and-configure-pxe-server-on-ubuntu-15-04/) but ran into an issue after discovering that udp only listens to ipv6. I found this [https://bugs.launchpad.net/ubuntu/+source/tftp-hpa/+bug/1448500](https://bugs.launchpad.net/ubuntu/+source/tftp-hpa/+bug/1448500) and used the solution found at the bottom with deleting the [::] out of the tftpd-hpa file. Restarted services and ensured apache was working, and then performed the network boot on my EliteBook. All went great after that.
Has anyone ever heard of fixing bad dimms by putting them in the freezer for 10 min? I still can't believe that worked.

---

