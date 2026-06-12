---
title: "Set Ubuntu as default OS? + Lots of confusion"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by sli121 on 2010-06-22
Hi all,

Please excuse me, like lots of people I don't have much experience with this, but I can understand if explained clearly. Thanks in advance to everyone reading!

My problem is that while I had the Win7 RC, I installed Ubuntu 9.04 as a Windows application using Wubi and I allocated the minimum amount of hard drive space to it, which is like 10 GB. Now, I can't remember exactly what happened, but through uninstallations and installations, now I have Win7 Pro and Ubuntu, though Ubuntu is not in the Add/Remove Programs list in Windows.

All I really want is for Ubuntu to be the default OS (first on the list at startup so I don't have to select it every boot). I can select Ubuntu fine, but I can't set it as default, whether it's in the .lst file (set default to 0, which it already is set to) as I've found on some forums, or in Windows msconfig.

Running everything is fine, I just want it to be selected first. I don't know if it's an app in Windows or dual booted.

If it matters, I am in Ubuntu now (10.04) and it says disk space is the entire disk space, not just a partition. I don't even have separate partitions, as I've found through gparted. I'm very confused, but I'm sure it's much simpler for all you out there. I appreciate any help, and I'll try to answer any questions! Thanks!

---

### Post by oldfred on 2010-06-22
It sounds like you still have wubi, which uses the windows boot loader and exists as a file inside the windows NTFS partiton.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

If you are using Ubuntu a lot you may have reached the point where you should think about a full install to separate partitions.

---

### Post by darkod on 2010-06-22
You probably have only wubi 10.04 installed inside win7. You can clearly see if you boot your ubuntu/wubi and in terminal check the partitions with:

sudo fdisk -l (small L)

If that shows only NTFS partitions, it's definitely wubi. If you also have a Linux and Linux Swap type partitions, it might be full ubuntu dual boot.

For wubi, you have to tell windows which OS you want as default. For win7 you should be able to set it like this:

Right-click on desktop the Computer icon and select Properties.
On the left side menu select Advanced System Settings.
Select the Advanced tab and in the third section called Startup and Recovery click on Settings.
There should be drop down menu for default OS. Select ubuntu and close all windows with OK or similar, DO NOT hit the X mark because it doesn't save changes.

That should be it.

---

### Post by darkod on 2010-06-22
> **oldfred said:**
>  Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

If you are using Ubuntu a lot you may have reached the point where you should think about a full install to separate partitions.

Yes, I forgot to mention that. If you have decided you like ubuntu enough, I would consider making proper install even without waiting for the next version.

Besides, 10.04 is LTS (Long Term Supported) so you don't really need to upgrade/install 10.10 when it comes out. Only move to newer versions if necessary. Otherwise from one LTS to the next is enough, they come out every 2yrs.

---

### Post by sli121 on 2010-06-22
Wow, thanks a lot to both of you! Lots of good info. I'm jumping on a real install now, but this USB method isn't working too well for me now. Gonna try it again, and if it fails again, I'll try the settings change to make Ubuntu default for now. Thanks a lot! And I'll come back if I have more questions

---

### Post by sli121 on 2010-06-22
OK so I can't get the USB drive to get accessed on startup for some reason, but for now I'm having Ubuntu be the default OS through what one of you said (sorry I forgot to remember your name before starting this). I was looking for that and thought it was in msconfig, lol my bad...

Is there any way to fully install Ubuntu without a CD or USB drive? Like through Ubuntu maybe? If not, all I can think of is uninstalling what I have and reinstalling using CD. However, I can't find it in A/R Programs...so idk how to do it unless I find out (online) how to manually remove it. I'd like to just make it official and get it over with so I can have it working properly! Thanks

---

### Post by oldfred on 2010-06-22
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)

If you have a lot of stuff you have done in wubi, you should backup /home first. It has all your user settings and data. If you have installed a lot of programs you can export a list to make it easy to reinstall.

Old conversion LVPM, see Alternative Instructions 
[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)
1. Create 3 new partitions with the Partition Manager : a 10-20 GB (ext3 format) partition to use as root (/), a ~2 GB (equal to RAM size) (swap format) partition to use as swap, and make the rest a (ext3 format) partition to use as /home.
2. Boot back into the Wubi-generated Ubuntu install, mount the new partition that will be used as /home in the dedicated-partition install to /media/disk, and copy the contents of the current /home recursively over to the new partition:
rsync -avx /home/ /media/disk
Additionally, if you want to avoid the hassle of manually reinstalling all the packages you currently have installed, run:
dpkg --get-selections > selections.dpkg
That'll generate a list of packages you have installed (back up that list to somewhere safe); after reinstalling the system, just open Synaptic, go file > read markings, select that file that was generated (selections.dpkg), press apply, and it'll reinstall all the software you have on your current system ).
Repair LVPM conversion:
[http://ubuntuforums.org/showthread.php?t=1501751](http://ubuntuforums.org/showthread.php?t=1501751)

---

### Post by sli121 on 2010-06-23
Thanks a lot for all the info, gonna start it all now! Thanks to everyone!

---

