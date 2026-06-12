---
title: "Install 2nd Linux O/S after Ubuntu 6.06.1"
date: 2006-09-22
forum: Installation &amp; Upgrades
---

### Post by scottrob12 on 2006-09-22
I would like to install a second Linux O/S on my hard drive after Ubuntu.Once installed, I would like the option to select at boot stage which system to use. I have read a lot of info about installing linux after Windows Xp but need a simple explanation regarding setting up grub in the above scenario.Ubuntu is in a 60GB root partition and I have created a 20 GB partition (ext3 ) for the 2nd O/S which is the new version of LinuxXP which I would like to test out.Any guidance from greater minds than mine would be greatly appreciated.

Regards

Scottrob12

---

### Post by pradeepadapa on 2006-09-22
hi,

ya u can install 2nd linix OS in the 20GB partition which u hav created, its actually very easy, u can install the other LINUX just as u hav installed UBUNTU but take care about the GRUB which gets installed on the MBR or the root of the UBUNTU partition, there is no need to panic bec the OS itself will install the GRUB nd when the installation is complete it shows u a GRUB prompt frm where u can select either of the OS either LINUXXP or UBUNTU , usually the latest distros which r being shipped with 2.6.x kernel automatically r detectinf many distros(major),so no need special guidance nd u can install the second linux OS.

ALL THE BEST MAN, hav any problms nd u can ask.

bye.

---

### Post by ajgreeny on 2006-09-22
No major difficulty with this except that many linux installs do not pick up existing ones in the new grub menu.

One easy way out is to make sure you have a copy of the various entries for OS's in your current grub menu, and then just add them to the new one when you have the new system installed.  This does mean that any changes to the ubuntu kernel will not be picked up automatically as you will not be using the grub.menu.lst from ubuntu, but the new OS instead, so you will have to edit the grub menu list manually, not a difficult activity, but something to consider.

You could also, of course, not install grub from the new OS but keep ubuntu's and then edit that to include the new OS, but what you add to that will depend on the newsystem.  Once you have installed it you should mount it (there is plenty of info about mounting other linux partitions in ubuntu on this forum), copy its menu.lst file and add the OS entries from that to your  ubuntu menu.lst file.  It is not too difficult; I have done it several times when adding Suse, Mepis and Fedora to my system.  The only problem I ever had was with Fedora, which by default does not put itself on to a logical partition, and it took me a while to figure out how to mount it in ubuntu.

Good luck!  I haven't found anything to touch ubuntu yet (it's this forum that makes all the difference, the community help here is second to none).

---

