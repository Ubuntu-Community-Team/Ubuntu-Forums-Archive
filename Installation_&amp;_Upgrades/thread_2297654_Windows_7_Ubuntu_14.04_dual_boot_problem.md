---
title: "Windows 7 Ubuntu 14.04 dual boot problem"
date: 2015-10-05
forum: Installation &amp; Upgrades
---

### Post by crusader8 on 2015-10-05
Hi!

I've an ssd (sda) which contains windows 7 and a hdd (sdb) which contains ubuntu 14.04. (ubuntu was installed after windows 7)
After the installation of ubuntu is successfully finished I had a nice grub 2 menu upon restart. From this menu ubuntu was loaded successfully, but when I've selected windows entry, the result was only black screen so I could not boot windows.

I was able to make windows to run by booting windows 7 installer and fixed the mbr on sda. But after that grub 2 was erased from the mbr, so I cannot boot ubuntu.
After multiple unsuccessful trial, I've tried to install grub 2 to the mbr of sdb so it would not interfere with the mbr of sda. On restart I could choose to boot from sda or sdb from bios so I could boot each os without a problem.
Unsucessfuly this attempt was a also a failure. Currently windows boot from sda without a problem, but when I try to boot from sdb only black screen is visible (so no grub 2 menu) and ubuntu is not boot.

I've a boot-repair report about the current situartion 

[http://paste.ubuntu.com/12691743/](http://paste.ubuntu.com/12691743/)

Can anyone help me the configure the dualboot?

Thanks!

---

### Post by oldfred on 2015-10-05
Drive you boot from is always hd0 in grub, but grub boot stanza shows hd1 still.
Did you have to add nomodeset for nVidia or AMD video?

Do not run auto fix in Boot-Repair as that will overwrite your Windows boot loader on sda. 
But you can run the advanced mode, and do the full uninstall/reinstall of grub.

---

### Post by crusader8 on 2015-10-06
I've run purged/reinstalled grub to sdb by using Boot-Repair. After I've tried to boot using sdb, the result is the same as previously: blank screen. (Booting windows from sda works as expected.)
Boot-Repair status:
[http://paste.ubuntu.com/12695213/](http://paste.ubuntu.com/12695213/)

I do not really understand why booting from sdb results only a blank screen when grub 2 is installed into the mbr of the drive.

(The backstory:
Previously I had only a hdd which dual booted win/ubuntu as expected. At that time mentioned nvidia driver was installed and everything worked fine.
After I've installed my new ssd I was not able to boot my linux from the hdd. Since I wanted to repartition the hdd anyway, I did the partitioning and reinstalled ubuntu to the hdd. This was the ubuntu installation I've mentioned in my previous post.)

---

### Post by oldfred on 2015-10-06
If you had nVidia driver before then you  need nomodeset boot parameter until you install a nVidia driver.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Then install nVidia driver from system settings, unless new Maxwell model card and then you may need to add a ppa to get very newest driver.


 Ubuntu Launches Its "Fresh" Proprietary Driver PPA
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
sudo apt-add-repository ppa:graphics-drivers/ppa

---

### Post by crusader8 on 2015-10-06
Sorry, I've not described the problem properly. The blank screen I've mentioned in my previous comment is appearing when I boot by using sdb. It's NOT appearing after selecting a menu entry from grub 2 menu. There is no grub 2 menu appearing at all. Just the blank screen.

So the problem is that grub is installed to the mbr of sdb but no grub menu appearing after booting from sdb just blank screen.

(However I've installed nvidia driver to ubuntu by overwriting sda boot record so I was able to boot to ubuntu. After the installation finished I've restored the boot record of sda by using windows installer. When I've tried to boot from sdb not grub 2 menu appeared just blank screen)

---

### Post by oldfred on 2015-10-06
Perhaps the grub in sdb has not found Windows yet, or needs a sudo update-grub to find it.

But if only booting Ubuntu, you do not get the grub menu. It just continues to boot and then you get black screen? If so hold shift key from BIOS until grub menu appears. Then add nomodeset to linux line.

---

### Post by crusader8 on 2015-10-06
There are three cases)
1) I put grub to sda mbr, and boot from sda: Grub menu appears. Windows and ubuntu entries are available. By pressing windows entry, windows does not boot. By pressing ubuntu entry, ubuntu boots.
2) I put grub to sdb mbr, and boot from sda: Since sda mbr is re-written by bootrec /fixmbr there is not grub in sda mbr. Windows successfully boots. There is no way to start ubuntu.
3) I put grub to sdb mbr, and boot from sdb: Grub menu does not appears, just black screen. In case I press shift key during boot I get "GRUB loading." text, and boot process stuck.

---

### Post by oldfred on 2015-10-06
How are you putting grub into sdb?

       sudo parted -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

Or something else?
Either way I would expect grub in sdb to work if the install to sda works.

---

