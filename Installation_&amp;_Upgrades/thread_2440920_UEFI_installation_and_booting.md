---
title: "UEFI installation and booting"
date: 2020-04-16
forum: Installation &amp; Upgrades
---

### Post by winecurmudgeon2 on 2020-04-16
I have Xubuntu 18.04 installed on a Dell Latitude E7440. The machine was refurbished and came with Windows 10, and I wiped the SSD and installed Xubuntu. I have done that many times, in fact, with nary a problem. Sometimes the machine boots (maybe one-third of the time) and the rest of the time I get the "No bootable devices found" with the F1, F2 and F5 options. Currently, the settings are UEFI with secure boot disabled and legacy options enabled. No other combination gets me anywhere close to booting.

I have tried many of the Google-sourced suggestions, including setting up the partition manually, using GPT (which came close to borking the SSD drive), switching from RAID to AHCI (which is the current setting), and trying to turn off Intel fast boot (could never quite figure out how to do that). I have also tried rEFInd, which sometimes allows me to boot into Xubuntu by using the live disk. However, when I installed rEFInd, the bootup list recognized it, but has given a variety of error messages and doesn't boot into Xubuntu. 

I am resigned to rebooting until the machine boots or using rEFInd as a live disk, unless someone has a few thoughts about what can be done. Thanks, as always, for your help.

---

### Post by oldfred on 2020-04-16
Once you get UEFI settings correct, Dell usually is one of the better systems.

You do need to update UEFI, update SSD firmware, have UEFI fast boot off, have AHCI on.
If using Windows you need AHCI drivers & fast start up off.

General UEFI info in link in my signature below.

Other Dell 7000 series, but Dell issues are very similar for all models of same generation of Intel or AMD chips. Essentially same UEFI has been used with just options for specific models enabled.
Dell 7791 UEFI update & some settings
[https://ubuntuforums.org/showthread.php?t=2431450&page=3](https://ubuntuforums.org/showthread.php?t=2431450&page=3)
Ubuntu 19.10 Provides Good Out-Of-The-Box Support For The Dell XPS 7390 Icelake Laptop
[https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1](https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1)
DELL Inspiron 15 7577 18.04 needed boot parameters
[https://ubuntuforums.org/showthread.php?t=2386049](https://ubuntuforums.org/showthread.php?t=2386049)
Post installation issues Ubuntu 18.04-Dell inspiron 7559
[https://askubuntu.com/questions/1072382/post-installation-issues-ubuntu-18-04-dell-inspiron-7559](https://askubuntu.com/questions/1072382/post-installation-issues-ubuntu-18-04-dell-inspiron-7559)

---

### Post by winecurmudgeon2 on 2020-04-17
Thanks for this. I'm not quite sure how to turn off UEFI fast boot or update the SSD firmware (I have updated the bios), but will give this a run and report back.

---

### Post by oldfred on 2020-04-17
I recently updated my Samsung NVMe SSD. 
It has Magican for Windows, I do not have Windows.
But my newer NVMe drive also had a specific bootable ISO for the update version.
It looked more like an old DOS screen, just checked version & updated SSD.

Some are now starting to update directly from Linux.
[https://www.phoronix.com/scan.php?page=news_item&px=Fwupd-NVMe-SSD-Support-Start](https://www.phoronix.com/scan.php?page=news_item&px=Fwupd-NVMe-SSD-Support-Start)
[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist) & 
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

---

### Post by winecurmudgeon2 on 2020-04-17
I mostly have it booting, using the instructions at "Post installation issues Ubuntu 18.04-Dell inspiron 7559." I can F12 to the boot menu and get the UEFI Xubuntu about half the time, and then use the less current kernel (5.3.0-28-generic). The most current is 5.3.0.46-generic, but that gets the F1/F2/F5 menu. 

Also, do I need to do the bit with grub and the NVDIA drivers as detailed in that post?

The most current SSD firmware update is 2016, and the revision ID in hwinfo is the same as the 2016 firware update. So it looks like that is OK.

Thanks again for your help.

---

### Post by oldfred on 2020-04-17
Only if you have a nVidia card or chip would you need nVidia drivers.
On my 2014 desktop I found that the Haswell's internal video was better than the old nVidia card I was using. 
So removed nVidia card & drivers. 
I do not game, so normal desktop uses seemed the same or could not really tell difference.

---

### Post by winecurmudgeon2 on 2020-04-17
Thanks again. Is there anything I can do about having to use the older kernel or the need to boot into F12, or should I mark this solved (mostly)?

---

### Post by oldfred on 2020-04-17
I might try recovery mode boot of both of your kernels.

Since you only have one install, you normally would not get grub menu unless you press Escape if UEFI or hold shift key if BIOS. So system may be starting to boot, but then has some issue. May need boot parameter or some other update.

Recovery mode uses nomodeset but also then does not include the quiet splash parameters so you see boot process. Often when it does not then boot, you may see error or warning several lines above where it stops. Or if you can boot next time, you can check log files to see errors on boot process or if something takes a long time to load and you are not giving it enough time.

You also can check boot times.
 systemd-analyze
Then to see processes.
systemd-analyze blame

For example with my system & fast SSD & fast internet, I often see several attempts to connect to internet. Eventually it does. I changed some settings that may have helped that also.

---

### Post by &amp;wP*!) on 2020-05-06
> **winecurmudgeon2 said:**
> Thanks again. Is there anything I can do about having to use the older kernel or the need to boot into F12, or should I mark this solved (mostly)?

Your observation let me think that this might be a hardware problem. Because no matter which booter you take you have a boot issue. I have the same model E7440  as you have. This moodel is from 2013-2014 timeframe. If you have not changed the drive, which was possibly used massively before, then your drive might start stumbling. If this is the case SSD firmware update won't help here. You can check this easily (you might have to install smartctl first if you don't have it):
```
smartctl -a /dev/sda
```
there you will see a Wear_Leveling_Count parameter. This number shows the health. If it is close to 10 (before death) I recommend you to replace it. Afterwards it might be better.

---

