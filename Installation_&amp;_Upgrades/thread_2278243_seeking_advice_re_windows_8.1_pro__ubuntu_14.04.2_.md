---
title: "seeking advice re windows 8.1 pro / ubuntu 14.04.2 dual boot on custom PC"
date: 2015-05-14
forum: Installation &amp; Upgrades
---

### Post by Hodor on 2015-05-14
I currently have windows 8.1 pro 64 installed on a custom PC (Intel Core i7-4790K, ASRock Z97 EXTREME6, System / boot drive: Samsung SM951 512GB M.2-2280 SSD,
Data drive: Samsung 850 Pro Series 512GB SSD (currently blank), LG Optical Drive ).
One point to clarify up front - when windows 8.1 was installed on the sm951, the Pro drive was disconnected (so all the windows system files are on the sm951).
I would like some advice on installing ubuntu 14.04.2 as a dual boot - would the following work?
- save current uefi/bios to drive as 'windows_boot.bin' (boot from pro drive is disabled, done);
- go into uefi -> boot menu -> disable all boot options apart from optical drive: boot from optical, install ubuntu to Samsung Pro drive -> reboot;
- go into uefi -> boot menu -> disable all boot options apart from optical drive and Samsung Pro drive -> save uefi/bios to drive as 'ubuntu_boot.bin'-> boot from Pro drive;
- subsequently: to boot from windows or ubuntu: just go into uefi and load appropriate saved uefi and boot.


What I really want advice on:
a. if I install ubuntu as per above, can I do the installation so as to leave my existing windows installation on the SM951 drive intact?
b. if so, when I susequently boot into this ubuntu installation, will my windows installation on the SM951 drive survive unmolested (or will grub or something else mess up my windows installation)?
c. if yes to the above, if I then subsequently boot into the windows installation (with windows_boot.bin loaded to uefi), will windows leave the ubuntu installation on my Pro drive alone, or will it get molested / messed up?

Also, I will need to briefly remove the sm951 to complete a small task soon, so if it would help, I could modify the above procedure to install ubuntu on the Pro drive while the sm951 is disconnected.

Incidentally, I have considered installing ubuntu on a virtual machine using hyper V, but I also want to consider the above option if it might work.

Thanks very much for any help.

---

### Post by ubfan1 on 2015-05-15
Certainly backup your Windows and EFI partition (the bootloaders are just files in some directories -- copy them somewhere like a USB). Installation of Ubuntu should just add another directory to the EFI boot partition's filesystem (/EFI/ubuntu/) and copy in the bootloaders, so that wont interfere with Windows in any way. Also, an nvram entry should be added pointing to the new bootloader, and this new entry put first in boot order.  Now you can still invoke the EFI menu, and select the Windows bootloader directly if you don't want to go through grub (because maybe grub still cannot boot Windows when secure boot is enabled).  Really, removing the Windows disk will prevent any possible mix-up of you specifying the wrong disk, but if the directories or sizes or something makes telling the disks apart easy, you might just consider leaving the disks in the run configuration.  grub has enough trouble with changing configurations as is (when USB is considered a disk, gets enumerated before the hard disk, and then gets removed after installation).
  You can also put an EFI partition on the second disk, and if you can boot from it, you can maybe not even write anything on the Windows' EFI partition. The installation should be easy, but of course, every machine is different, so a quick search of the forum/askubuntu for your specific model might turn up some specific tips.

---

### Post by Hodor on 2015-05-15
Thanks ubfan1.  I'll see how I go.  Found some tips for my PC here: [http://ubuntuforums.org/showthread.php?t=2252873](http://ubuntuforums.org/showthread.php?t=2252873)

---

### Post by oldfred on 2015-05-15
I did a second install of Ubuntu to sdb. I specifically told it to install grub to sdb, and it mentioned that it was installing to sdb. But it overwrote the ubuntu folder on sda. I had to reset that.

And UEFI seems to lose NVRAM settings when a drive is disconnected. So when you reconnect you may have to reboot a couple of times or use efibootmgr to create a new entry.

When Ubuntu installs to sdb, and puts efi files on the sda efi partition it writes only to a new ubuntu folder. It will not modify the Windows efi folder. From UEFI boot menu you should always be able to boot Windows directly. But always back up efi partition separately, it is not large.

But if motherboard is like my Asus, you may need to turn off fast boot (not the Windows fast startup which also must be off). Fast boot means UEFI does not recheck what hardware you have., Since hardware rarely changes, it does speed boot, but then you do not have time to press any key to get into UEFI to make changes. I set mine to normal boot on total reboot or cold boot. And my fast boot has a delay setting so I set that to 3 sec just so I have a chance to get into UEFI if needed on a warm reboot.

Also be sure to install in UEFI mode. Many links to useful sources in link in my signature.

---

### Post by Hodor on 2015-05-16
Hi oldfred,
Thanks for excellent advice as always.
The PC now seems to work as I had hoped (but I'm still learning).
Extreme6 UEFI has some handy tools - surprises me as I thought it was going to be trouble.

Kind regards.

---

