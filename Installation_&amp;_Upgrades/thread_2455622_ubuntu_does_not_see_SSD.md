---
title: "ubuntu does not see SSD"
date: 2020-12-23
forum: Installation &amp; Upgrades
---

### Post by stephenbbb on 2020-12-23
trying to install ubuntu 20.04 on a new lenovo Ideapad 1 with SSD. ubuntu does not see the SSD. I tried with the nvme parameter after the quiet splash and it still does not see the SSD.
I can get into BIOS. Gparted does not see the SSD either.
pls help.
thanks

Correction: the title should be eMMC, not SSD
can't edit the title

---

### Post by CatKiller on 2020-12-23
Is it a new laptop with Windows on, which hasn't been shut down properly because you left Fast Startup on?

Have you got the access method setting in your UEFI set to RAID rather than the AHCI that it should be?

---

### Post by stephenbbb on 2020-12-23
it is a new laptop and after switching the driver from Devices to Microsoft Storage it cannot boot windows any more. There is no RAID vs, AHCI setting visible in the BIOS. there is one option called 
Reset to Setup Mode
which I have not attempted. the SSD is eMMC Card: Ramaxel 64gb
Bios is:FQCN12WW
EC: FQEC05WW
the boot-repair dump is here:
[https://paste.ubuntu.com/p/wdQb5tfB9J/](https://paste.ubuntu.com/p/wdQb5tfB9J/)

---

### Post by stephenbbb on 2020-12-23
Sadly this seems to be Ubuntu lagging behind on new technology. there  are several posts about Linux and eMMC with no solution even though some  people claim to have solved it. I installed mmc-utils, but there is no  command to detect mmc devices. there should be mmcblkxx under /dev , but  it is not there. 
this was a good boxing day sale and the processor  is much better than i5 and better than many i7 and with the eMMC it is  quite speedy. but Linux is not ready for that technology yet.

---

### Post by QIII on 2020-12-23
Did you disable secure boot, fast boot and legacy boot?

eMMC is not a particularly new technology.  There are any number of SBCs that use eMMC for storage and most of those will run Linux distros.

---

### Post by P-I H on 2020-12-24
Have you tried to run **sudo update-grub**

---

### Post by CelticWarrior on 2020-12-24
Update UEFI would be the first thing to do if such update has been released.
Then check for any drive or SATA mode. RAID or Intel RST aren't supported. Select AHCI.
Disable TPM.
Disable Secure Boot and Fast Boot.

---

### Post by leprotic on 2021-02-02
Hi. I also got a 11ADA05 yesterday. It was an emergency and I thought the price was quite good for this configuration, just like thousands of others (apparently it's selling pretty well).

So I have the same problem. In case you've been wondering if this is an Ubuntu issue, I've tried quite a few distros (Ubuntu 20.04 / 20.10, Pop OS, Mint) to no avail. I've tried pretty much all the combinations of bios options (UEFI, legacy support, secure boot,..)

I can't believe there are so many unresolved cases escalated online, yet no viable solution. I've been using Linux at home for more than 20 years now. I'm far from a power user or an expert but it never took me more than a few hours to fix any problem with the help of the community (and I'm talking about dozens of problems), even 20 years ago when there were significantly fewer users you could get help from.

I'll keep trying of course and keep you posted if I can fix it.

Are we really stuck with windows in the year 2021? It feels weird.

---

### Post by leprotic on 2021-02-02
A few additional remarks:

----------
"[I]Update UEFI would be the first thing to do if such update has been released.
Then check for any drive or SATA mode. RAID or Intel RST aren't supported. Select AHCI.
Disable TPM.
Disable Secure Boot and Fast Boot. [/I]"

Thanks CelticWarrior but there's no option for SATA mode in the bios. All it says is HDD not installed. according to the forums, a few other brands / models seem to be working OK on AHCI (Dell, Acer) but there's no such option for Lenovo 11ADA05.

---------
"[I]Did you disable secure boot, fast boot and legacy boot?
eMMC is not a particularly new technology. There are any number of SBCs that use eMMC for storage and most of those will run Linux distros.[/I]"

Thanks QIII. I've tried secure boot and legacy boot with different distros, no joy. There's no fast boot option in the bios.

---

### Post by oldfred on 2021-02-02
Multiple places where it says that specific model eMMC not seen.

One user installed to another flash drive which worked, but eMMC still not seen.

One post indicated it may have a M.2 slot? If so that would be good as M.2 SSD would be a lot faster than eMMC device.

I did my desktop build in 2016 when NVMe devices were very expensive. My motherboard had M.2 slot that supported both SATA or NVMe. So put in SATA M.2 drive. Wanted to see if newer NVMe was faster, plus wanted larger drive. So put M.2 SSD into external USB enclosure. It is almost as fast as external drive as it was as an internal drive.

---

### Post by leprotic on 2021-02-04
Update : I've added Manjaro to the list of distros tried and failed. In case anybody is willing to help, here's the lsbk output.

[manjaro@manjaro ~]$ lsblk -f
NAME FSTYPE FSVER LABEL UUID * * * * * * * * * * * * * * * * FSAVAIL FSUSE% MOUNTPOINT
loop0
* * *squash 4.0 * * * * * * * * * * * * * * * * * * * * * * * * * *0 * 100% /run/miso/
loop1
* * *squash 4.0 * * * * * * * * * * * * * * * * * * * * * * * * * *0 * 100% /run/miso/
loop2
* * *squash 4.0 * * * * * * * * * * * * * * * * * * * * * * * * * *0 * 100% /run/miso/
loop3
* * *squash 4.0 * * * * * * * * * * * * * * * * * * * * * * * * * *0 * 100% /run/miso/
sda *iso966 Jolie MANJARO_XFCE_2021
&#9474; * * * * * * * * * * * 2021-01-03-08-16-14-00 * * * * * * * * * * 0 * 100% /run/miso/
&#9500;&#9472;sda1
&#9474; * *iso966 Jolie MANJARO_XFCE_2021
&#9474; * * * * * * * * * * * 2021-01-03-08-16-14-00 * * * * * * * * * * * * * * *
&#9492;&#9472;sda2
* * *vfat * FAT12 MISO_EFI
* * * * * * * * * * * * C274-6DF3 

--
There are a few posts in different forums where people claim they fixed this problem (working around UEFI, installing additional eMMC drivers before the main installation, etc.) but I'm not convinced. Based on my 20 years of (noob) experience on Linux issues and forum support, I'd say if there was any realistic solution (no matter how complex it is), it would spread quite quickly. But there are still hundreds of unresolved cases. After countless attempts with different distros and bios configurations, I think I'm about to accept the harsh truth that there's no solution for this for the time being. I hope it draws enough attention that somebody addresses it soon.

---

