---
title: "problem installing (raid prob?)"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by gloth on 2008-10-15
Hi, I am new to ubuntu.
I have tried to install ubuntu without success =\
Here is what I have:
1 sata hdd with 1 primary partition that I have installed windows on and the rest is unallocated space at the moment.
2 sata hdd raid-0
1 external hdd with 2 hdd inside raid-0

edit: my mb is Gigabyte N680-DQ6, it uses the nForce 680i SLI chipset

I made a clean install of windows at the 1st primary partition and made a 2nd primary partition with the windows installer.
After installing windows I moved on to install ubuntu.
With the ubuntu installer I deleted the 2nd partition and created a /, a /home (ext3) and a swap.
The installer saw the external disks as raid, but did not see the 2 internal disks as raid - I thought it wasn't going to be a problem, I could search for drivers after I log on to ubuntu.
I choose the boot loader to be installed in the 1st partition (it recognized the vista loader there as well)
Installation ended...

Problems are:
1) after restarting the raid software found the 2 hd but could not see them as raid. If I shut down the power and restart my pc the software finds the 2 drives and successfully makes them a raid.

2) the ubuntu boot loader didn't start. After restarting windows loaded =\

I am thinking that it has something to do with the installer not recognizing the raid and messing up the drives (???), but as I stated I am new to this and I would like a little help.

Thanks

---

### Post by gloth on 2008-10-15
anyone? =(

---

