---
title: "Problems with software Raid"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by waltervalderrama on 2009-11-26
Hello everybody.

I have a serious problem with software RAID. I installed Ubuntu 9.04 AMD64 with 2 HD of 250 GB each, configured software RAID 1. When I used my PC normally I have some warnings when booting. Nothing happens if I use PC with internet, music and some gaming. The problem is when I use a VMWare virtual machine. At next reboot (after VMWare), there are problems, boot errors and one of the HD makes a strange sound (tic tac). 

I tried to unplug the fail disk, start PC again, but an error appears and booting process stops. I think that when you boot a RAID 1 array with 1 disc only, PC should boot. 

After that I plug the fail disk again, and booting process completed successfully

I want to replace the fail disk, but I am not sure if my PC would boot normally after that.

---

### Post by punkybouy on 2009-11-26
Well, technically if you disconnect one drive in the mirrored array then from the array's perspective you have "failed" the drive so when you reconnect it a rebuild should start to occur and depending on how much data you have on the drive the rebuild could take hours.
Both drives should be equivalent so you should be able to take either one out and replace it with a new drive and yes it should reboot but I can't speak for your RAID hardware vendor or software driver.  I am going to assume the adapter came as part of the motherboard and you enabled it in the bios and installed a second drive.  If so then did you also install a driver?  Pretty rare to have a Linux driver for that.
Normally the RAID driver would have to be slipstreamed into the installation as the OS is installed and not installed AFTER the OS install is done.

---

### Post by falconindy on 2009-11-26
You'll need to manually fail the device in order to remove it safely. Something similar to:
```
mdadm /dev/md4 --fail /dev/sda6
```
Obviously you'll need to replace the first /dev with your array device and the second with the faulty hard drive device.

---

