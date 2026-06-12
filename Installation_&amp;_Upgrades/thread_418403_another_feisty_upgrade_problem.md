---
title: "another feisty upgrade problem"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by merlin666 on 2007-04-22
After selecting the upgrade to feisty option from update manager, the following happened (leaving the system unattended while files were downloading overnight due to slow connection):

* I was logged out without dialogue

* after rebooting there were several new kernel options (2.17) related to feisty, but none of them amd64

* I booted to the highest amd64 kernel available (2.15) and when I checked update manager it still said ubuntu 6.10, with an error that the distribution was broken

* I tried to run the distribution fix program but it did not connect to servers

* when checking the package managers I noticed that repositories were changed to feisty

* after changing repositories back to edgy I was able to run the distribution fix

* I have done this four times and the same thing always happens

* the list or feisty kernels are still showing up in the grub list, and I cannot edit menu.lst anymore (please help)

Is this specific to upgrading to 64-bit feisty. It seems there are many other problems related to the upgrade process posted here.

---

