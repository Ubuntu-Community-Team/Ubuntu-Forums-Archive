---
title: "Intel ESRT2, Matrix RAID or Ubuntu Software Raid?"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by dalitso on 2010-10-04
I am trying to install Ubuntu 10.04 on a RAID 1 configuration on an Intel server board S3420GP. The server is for a certain company, so I don't have it with me as I write. I left it on site.

In BIOS setup > advanced>Mass storage controller configuration> SATA MODE there are these options: Enhanced, compatibility, AHCI, Intel ESRT2 and Matrix Raid.

When I choose intel ESRT2 and save the setting then use the intel cd to setup a raid 1 array on the two 500GB SATA drives,I get stuck on ubuntu installation when doing partitions. Its says "configure iscsi volume and asks for ip address and port.

When I select Matric Raid, I cannot even setup up an array using the Intel boot cd or get some key combination to press to enter the raid setup when server is booting.

Which of these technologies can I use for ubuntu, intel ESRT2, Matrix Raid or should I just use the ubuntu software raid?

If I can use either ESRT2 or matrix raid, please point me to where I can get instructions to install ubuntu on the raid 1.

---

### Post by ian dobson on 2010-10-04
Hi,

I would go with software raid (mdadm). If the motherboard/RAID controller dies for any reason and your using the hardware raid then your screwed unless you can find exactly the same hardware.

With linux software raid just replace the motherboard and mdadm will use the normal sata ports and your data is available.

So use AHCI mode in bios and mdadm software raid.

Regards
Ian Dobson

---

### Post by ronparent on 2010-10-04
Unless you want to dual boot with windows and share data on the raid with both systems, you are probable better off using software raid. If you decide to use software raid, even though you have not yet created any raid partitions, be sure to erase the raid meta data from your raid drives before uninstalling dmraid (the fakeraid software). You could then install mdadm (software raid manager) and setup your software raid.

---

### Post by dalitso on 2010-10-04
No dual boot is needed on the server, just Ubuntu. So onboard RAID be it on a desktop motherboard or server motherboard is still unreliable? I thought that since this is a server board then it would be better. In that case then, I will just definitely use mdadm.

Thank you guys

---

