---
title: "Installation on Macbook using Hard drive"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by alexmorph on 2012-10-22
I am trying to install the latest Ubuntu desktop on my old Macbook. The Macbook can not be booted from anything other than the internal hard drive (Broken CD drive, no USB boot).

I have another Mac and have followed the installation instructions to create a boot USB directly onto the hard drive.

If I then put this hard drive into the old MacBook and boot it from that drive it boots into Ubuntu Live mode. So I now have the option to try or install.

Now here comes the issue. I am trying to install Ubuntu onto the same drive its trying to install from and it doesn't seem to want to do it. I have tried various options with the partitions (which I have to create from the live mode). I believe that the install files are being deleted while its installing.

The only other option I could think of was installing Ubuntu from an external drive while in the trail mode. But I can not see to work out how to do this as all the images are boot images.

Any help would be appreciated.

---

### Post by darkod on 2012-10-22
Strange situation.

Have you tried:
1. Create the partitions on the disk while it's still connected to the other Mac, when you are preparing it as live hdd. Make only a small partition at the beginning to serve for the live files, you can partition the rest with the sizes you want for the partitions you plan to use for ubuntu. That way you will not need to repartition anything while running from the hdd.

2. Have you considered to start the install by PXE boot if the old mac network card supports that? That is one option if you can't boot from anything else. Install the hdd inside and use PXE to run the installer.

---

