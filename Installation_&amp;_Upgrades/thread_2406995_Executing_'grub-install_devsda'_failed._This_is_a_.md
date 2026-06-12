---
title: "Executing 'grub-install /dev/sda' failed. This is a fatal error"
date: 2018-11-28
forum: Installation &amp; Upgrades
---

### Post by jonty16117 on 2018-11-28
Please help...i installed windows 10 on uefi/gpt system.Then i tried to dual boot with xubuntu...but it fails every time with this error. Then when i try to boot, my windows 10 is also gone and unable to boot. Then i have to again install windows after cleaning my whole hdd and again when i try to reinstall xubunt, i shows the same error. I have done this f***$-@ process a lot and it is getting frustrating. Please help as i m unable to use my laptop....:confused:

---

### Post by ubfan1 on 2018-11-28
The EFI menu (some function key at power-up like F12) will offer you the choice of boot device/OS.  Choose Windows, and it should boot, bypassing grub completely.  How big is the EFI partition? Maybe there's not enough space to install the grub/shim bootloaders.

---

### Post by oldfred on 2018-11-28
Post this from live installer:
sudo parted -l

What brand/model system?

---

### Post by jonty16117 on 2018-11-29
Installed using this method.. but still no luck. Anyhow will mark solved when any solution is found...

I checked using gparted from live usb...and efi partition size is 100 mb out of which 27mb is used (i guess by the windows boot loader).

---

### Post by baiteh on 2018-11-29
I had this on a dell xps 15 - in the end I booted off a live usb and used gParted to delete the partitions.  Then installed Ubuntu and it worked ok.

---

### Post by yancek on 2018-11-29
You haven't answered the questions asked above so we're just going to be guessing.  Have you mounted whichever partition is your EFI partition from the Xubuntu installer to check to see if you have an ubuntu directory with the necessary boot files?  You should have been able to boot windows from the BIOS as suggested above after your failed Xubuntu install.

---

### Post by jonty16117 on 2018-11-29
Ok...

All the partition information..

All the partition information...[https://m.imgur.com/1MZSJtq](https://m.imgur.com/1MZSJtq)

I want to install windows 10 btw with xubuntu...both on gpt/uefi mode...for an update

---

### Post by oldfred on 2018-11-29
Normally the ESP - efi system partition is first or second.
And Windows requires its unformatted system reserved partition to be before any NTFS partitions.
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)

Ubuntu only requires the ESP & /. And only one ESP per drive, so Windows & Ubuntu will share the one ESP. But most suggest smaller / of 25 GB or so and large /home and/or data partition(s).

---

### Post by jonty16117 on 2018-11-29
Can you suggest me an easy way to do this ...

---

### Post by oldfred on 2018-11-29
Not really easy unless you are willing to start over. That requires good backups of everything you might want to save.
You are not showing a lot of data in each partition, so is this a new install?

Since Windows likes extra partitions, often easier to install Windows first. Then shrink the NTFS partition with Windows tools & reboot so it can run chkdsk.
For Windows to install, you would have to erase all partitions.
Then create / (root) of 25GB and large /home or other data partitions.
You do not need swap anymore as new versions use swap file.

Be sure to always boot in UEFI boot mode.

---

### Post by jonty16117 on 2018-11-29
Quick update...backed up everything...i have a 1tb hdd...i'm planning to use 100gb for windows, 200gb for local disk(ntfs), and the rest of it as linux or ext4....so any additional advice beforehand would be appreciated...

---

### Post by oldfred on 2018-11-29
Just the general instructions.
 Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 10 screens or similar to Windows 8
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)  & 
[https://askubuntu.com/questions/221835/how-do-i-install-ubuntu-alongside-a-pre-installed-windows-with-uefi](https://askubuntu.com/questions/221835/how-do-i-install-ubuntu-alongside-a-pre-installed-windows-with-uefi) 

I prefer to use gparted to create partitions in advance, but that is not required.
Make sure Windows fast start up is off.

More details in link in my signature.
Scan the steps to install, and if any questions better to ask before install.

---

### Post by jonty16117 on 2018-12-01
OK...now tbh, this is getting really frustrating. I formatted the whole disk using gparted from live installer using gpt scheme. Created a efi partion of 600mb, flagged it with boot and efi. Created second partion ext4 of 25 gb at /. Created swap of 4gb. Created another ext4 at /home and the rest is as it is( out of 1tb).
UEFI settings:
OS selected to "others" (there was second option "windows 8").
UEFI BBS Priorities selected to windows boot manager.
Secure boot is off.
And no other option is available on uefi settings related to boot...
Then installed xubuntu at that ext4 of 25gb at /, bootloader installation at dev/sda only to give the error (once again my friends) 'grub-efi-amd64-signed at target/' something...now wtf is this

---

### Post by C.S.Cameron on 2018-12-01
I recall a similar error message trying to put the boot loader on a partition rather than on the disk, ie sdxn rather than sdx.

---

### Post by jonty16117 on 2018-12-01
OK...i understand you but...i already specified that i installed bootloader at sda and not sdax ... anything else?

Respond plz...

---

### Post by oldfred on 2018-12-01
If installing in UEFI mode, it really does not matter what you specify in the combo box on the partitioning screen. Grub just installs to first drive's ESP, normally sda, but if NVMe first NVMe.

I just installed 19.04 to sdb, told it not to use ESP on sda, to use ESP on sdb and selected sdb in combo box. I of course overwrite my default boot in sda's ESP.

Sometimes there is no rhyme or reason. And users have used Boot-Repair (in UEFI boot mode from Ubuntu live installer) to totally reinstall grub using advanced options & then it works.

---

### Post by jonty16117 on 2018-12-01
So are you suggesting to run boot repair from live installer...?

---

### Post by oldfred on 2018-12-01
Try that, and if not working post new link to latest report from Boot-Repair.

Dell just works, but you have to have latest update to UEFI and if SSD update its firmware.
And you have to have RAID off , change to AHCI unless RAID 0 as drive setting in UEFI.

       Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)
Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)
Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
[https://wiki.archlinux.org/index.php/Dell_XPS_15_9560](https://wiki.archlinux.org/index.php/Dell_XPS_15_9560)
[https://askubuntu.com/questions/1043842/running-ubuntu-via-live-usb-error-on-dell-xps-15-9560](https://askubuntu.com/questions/1043842/running-ubuntu-via-live-usb-error-on-dell-xps-15-9560)

---

### Post by jonty16117 on 2018-12-01
I have wipro e.go laptop btw

---

### Post by oldfred on 2018-12-02
Missed that post saying Dell was not you.

Did you try Boot-Repair?

---

### Post by jonty16117 on 2018-12-02
i tried boot repair. Here are the results...[https://jmp.sh/b/QkM7h5MzMaYjWEevKsYs](https://jmp.sh/b/QkM7h5MzMaYjWEevKsYs)

btw i had created an efi partition of 600mb at the start of this installation before...

---

### Post by oldfred on 2018-12-02
Link not working.
Normally Boot-Repair uses a paste bin site.

You can rerun report and get new link, if you did not save link it creates.

---

### Post by jonty16117 on 2018-12-02
[https://drive.google.com/open?id=18uAVB7bR6uRDxly7Wl2jenMY84dyTszk](https://drive.google.com/open?id=18uAVB7bR6uRDxly7Wl2jenMY84dyTszk)
[https://drive.google.com/open?id=1mouWZQnvymwvQ9t7Zn6k59QOj-4DFy8s](https://drive.google.com/open?id=1mouWZQnvymwvQ9t7Zn6k59QOj-4DFy8s)
check both links...

pls report if the link is not working again...

---

### Post by oldfred on 2018-12-02
This seems to be one issue.
      >  Locked-ESP detected. 



Boot-Repair tried to do a fix, but it must not have worked.
Try this from live installer:
       [http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872](http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872)
dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

Install otherwise looks correct. And you do have UEFI entries for ubuntu, both grub & shim. Shimx64.efi works whether UEFI Secure boot is on or off. Grubx64.efi is only for UEFI secure boot off. But corruption on ESP may prevent UEFI from reading ESP.

Some UEFI also have locked settings for secuity, check you do not have a lock on the ESP partition.

---

### Post by jonty16117 on 2018-12-02
ok i tried dosfsck and the output is:
fsck.fat 4.1 (2017-01-24)
/dev/sda1: 13 files, 1479/153296 clusters
and regarding that ESP partition lock...how to check if my esp partition is locked...

---

### Post by jonty16117 on 2018-12-02
if its not too much to ask.. do you have any experience in bios-mods:roll:

---

### Post by oldfred on 2018-12-02
Know nothing about UEFI/BIOS other than installing an update.

Can you read/write into your ESP.
The normal mount with fstab to /boot/efi/EFI/ubuntu is normally umask=0077, I think for security reasons. Back with 14.04 it use defaults and you could easily write into it. Boot-Repair changes it to defaults so it can update settings. I normally change mine, so I can backup the ubuntu folder, but may start changing back to 0077 after changes.

If you can read/write into your ESP then it is not locked. Or Boot-Repair includes that message if issues in writing into the ESP.
Some with FAT32 issues had to backup ESP, erase it, and recreate a new FAT32 with boot/esp flag partition. And restore backup. But new UEFI entry & full grub update requires as then it gets new UUID & GUID(used by UEFI).

---

