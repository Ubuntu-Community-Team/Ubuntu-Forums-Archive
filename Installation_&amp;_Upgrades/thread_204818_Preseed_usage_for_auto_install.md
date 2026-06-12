---
title: "Preseed usage for auto install"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by RaBiT on 2006-06-27
I'm having trouble getting the autoinstall to work using a preseed file and the Ubuntu installer.

I have the preseed file on a floppy and added "preseed/file=/floppy/preseed.cfg to my isolinux.cfg file but the system doesn't seem to read the floppy to use the preseed file. Even in a working system I have trouble reading the floppy from Ubuntu 6.06.

I would ideally like to have the preseed file on the network but haven't managed to find out how to config the NIC in isolinux.cfg t have networking function to get the preseed file from NFS.

Would also like to have the install come from NFS but, again, info on the correct way to setup the preseed file for second stage installation (supposed to work from filesystem but no detail on how to configure) is rather scarce.

Any help or suggestions on where to find info for automated boot would be appreciated.

Have used RedHat KickStart and also setup SUSE for NFS install but Ubuntu is proving to be a challenge.

Thanks in advance.

---

### Post by RaBiT on 2006-07-26
Apparently, with Dapper Drake, you must use the Alternate CD in order to use preseed auto installs.

---

