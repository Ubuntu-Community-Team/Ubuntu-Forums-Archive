---
title: "Cannot boot after Win10 intentionally removed"
date: 2024-11-06
forum: Installation &amp; Upgrades
---

### Post by nevyoung2 on 2024-11-06
Hi – My son gave me his Ubuntu 22.04 desktop, with 16G RAM, SSD and nice big 4TB HD. I have tried migrating to Linux for nearly 30 years, but never became sufficiently proficient in it to escape *******. Many of the non-Ms programs I use are now available in Linux environment.

I noticed that the HD sounded unhappy. Tried various tests. The machine would often hang if left for more than a day. Looong story. I wanted to run the machine without the HD, but it would not boot without it. My son told me the machine used be dual boot with Win10. He deleted the Win, but it appears that the bootloader is chained with the HD. Have tried Boot-Repair and studied the summary carefully but don’t understand everything. Especially "Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.5 LTS entry (sda1/efi/****/shim****.efi (**** will be updated in the final message) file)"

 I have been able to boot from grub but only WITH HD connected, but could not then make the settings permanent. WITHOUT the HD connected, grub boot encounters “a start job is running for /dev/sdb1 - i.e the HD. Where is this job instruction??? 

The one time that I got it to boot via grub, I then tried to upgrade grub which must have changed something so it no longer can boot from the OS at all. So – after a week of learning without succeeding, I hope you guys can spot the problem in the summary which I uploaded to the pastebin, having booted from a Live USB. [https://paste.ubuntu.com/p/wncHZcwWvk](https://paste.ubuntu.com/p/wncHZcwWvk). I thought I had correctly uploaded the summary but don't see it at this link. Let me know it I must try another upload. Attaching txt file .......

Note – I don’t want there to be any Windows or its leftovers on this machine. 

Thanks

---

### Post by grahammechanical on 2024-11-06
Some clarification is needed. Is Ubuntu installed on the SSD or the 4TB hard disk? This message - 

> "Please do not forget to make your UEFI firmware boot on the Ubuntu  22.04.5 LTS entry (sda1/efi/****/shim****.efi (**** will be updated in  the final message) file)"

is telling you to open the UEFI (also called BIOS) settings utility and give the boot priority to sda1 partition. Assuming that Ubuntu is on sda and sda is the ssd and not the 4TB drive.

Your pastebin link is broken. And without knowing about your drives and partitions and which operating system is where and not knowing where the Grub boot files are, we cannot help you.

It seems that you cannot now boot Ubuntu at all otherwise I would have advised loading the Disks utility. That will show you the partitions on the drives.

Regards

---

### Post by yancek on 2024-11-06
Your boot repair information shows the necessary files but you need to go into the BIOS firmware on boot, before you see a Grub or any other menu and set Ubuntu to first boot priority.  The way to do this varies with manufacturer and one will often see a message on boot indicating which key to use.  If you don't see that, you will need to do an online search for how to access BIOS on "whatever manufactuer".  Or you could post that information here, HP, Dell, Lenovo and which specific brand.  The drive with Ubuntu and the bootloader on it is /dev/sda which is a 223GB drive and without that you can't boot.  Your larger drive (3.4TB) has an ext4 Linux filesystem but nothing on it.

---

### Post by oldfred on 2024-11-06
I see UEFI Secure boot is on. Line 74.
That will work, but you also have nVidia, line 67. That makes Secure boot a bit more difficult as you have to create a MOK or machine owner key to authorize the binary blob that is the nVidia driver. Ubuntu cannot say it is secure for Secure boot as it cannot review the software. 
Often nVidia then needed for system to work correctly. Or you have to go into UEFI settings and change video to internal CPU's video, if it has video. That will reduce performance in most cases particularly gaming, but normal use like browsing & file editing may not have noticeable change.

You have the mount of the HDD partition in your fstab. Line 196
Is 4TB drive an external drive? Mount in fstab would have to time out, if drive not found. But it should still work.
If external drive, there are additional settings recommended for fstab mount. Or remove entry from fstab with # to convert to comment, in case you want to add again. Also if keeping it better to use UUID or label not device like /dev/sdb1.

---

### Post by nevyoung2 on 2024-11-07
Thanks. Ubuntu on SSD. Can access BIOS without a problem but don't see an option to boot from sda1. Have used the Disks utility and can see the partitions but don't see anything that looks unusual. It appears from the next replies that the summary as accessible.

---

### Post by nevyoung2 on 2024-11-07
Thanks. Have been accessing BIOS (Del) and have seen boot priority settings but seem to have no other choice besides HD, USB or CD-ROM. Will look again carefully. Drive with Ubuntu is on sda2. 4TB HD only has some unimportant data on it. Gparted shows that sda1 seems to be a EFI boot partition. I expect that the machine should be booting from Ubuntu on sda2, but a bootloader on EFI sda1 appears to be complicating the process.

---

### Post by nevyoung2 on 2024-11-07
Thanks. I have even learned about MOK but don't really understand what can be done.
 nVidia - will try the on-board video. No gaming - video processing and astronomy image stacking are my uses. 
4TB is internal HD. OK - will see what is in fstab but don't know if I could simply comment the reference to sdb1 out. 
Another possible complication is that when attempting to reinstall grub, the installer that downloaded was grub2 which I hear from a work colleague is not entirely compatible with grub but should install nevertheless. That install process stopped when it could not find /var/lib/..../modinfo.sh. Difficult to keep track of the many things that I have tried!

---

### Post by oldfred on 2024-11-07
Grub is the default boot loader for Ubuntu and many other distributions. It is boot boot manager (menu) and boot loader.
A few, particularly those with Macs like rEFInd, but it is just a boot manager (menu) not a boot loader.
I have rEFInd on a very old flash drive that is too small for anything else. And have needed it for emergency boot once or twice with my older system that seemed to get lost when I plugged in too many drives, flash drives test SSD, all with grub.

There are two versions of grub, grub-pc for old BIOS systems and grub-efi-amd64 for UEFI systems. How you boot install media UEFI or BIOS is how it installs or repairs.

My Dell with 11th Gen Intel says "BIOS" but once in BIOS, it says it is UEFI only. You do not boot a partition, but do boot a drive whether UEFI or BIOS.
With BIOS, it knows to jump to very first sector of drive to find MBR. With UEFI, it will have long GUID, seen as partuuid that specifies the ESP - efi system partition. We use esp,boot flags to defind esp, but internally it is the long GUID.

You just need a # like the other comments to temporarily not mount of  4TB drive. Then you can manually mount to test if it has issues.

You can see UEFI boot entries if live installer or system booted in UEFI mode.
sudo efibootmgr (new versions seem to show detail, older ones needed the -v option)
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
Check partUUIDs match to ESP - efi system partition(s) you have.

---

### Post by yancek on 2024-11-07
When you access the BIOS you should see a tab for Boot or Boot options where you can look for the Ubuntu entry.  It should show as ubuntu as your boot repair entry indicates it is there.  Generally it will show something similar to:  Boot0000* ubuntu  You need to move that up to first boot in your BIOS menu.  You won't see any reference to a drive partition such as /dev/sda1 or /dev/sda2.

---

### Post by nevyoung2 on 2024-11-07
Thanks guys - I have repaired the boot process thanks to your tips, especially @oldfred for the UEFI links. It was a  lot of intense reading and learning. I am not entirely sure of the detail of everything that I eventually did, but here is the gist of it.
- the BIOS/UEFI was set to an Ubuntu boot device, not specifying though the device and partition. That has been the boot setting all along.
- this desktop is an AMD chipset. It has a disable option for a security setting called fTPM - (Trusted Platform Module). It sounds but may not be similar to Secure Boot which I have learned is not an essential component of UEFI, so I disabled it anyway. That took a lot of reading and learning.
- I commented out the fstab reference to sdb1 - that did not initially solve the problem, but was probably necessary to the final solution.
- I tried grub commands with a few various settings, but main problem was that I could not tell which was the boot device and file system root. Looked through the directories and saw what looked like boot files on sda1 and on sda2. Confusing.
- I then ran boot-repair again to generate the latest summary.
- I then took a look at the Advanced Option in Boot-Repair - like disabling Secure Boot and choosing whether to use a 'separate' boot partition location. Under Grub Location tab saw that OS to boot by default was set on sda2. Initially after de-selecting the 'separate' option, it wanted me to create a bigger boot partition >1MB on sda2 which sounded too drastic. It was happy to continue using a 'separate' (default) /boot/efi directory on sda1 which did not need resizing.
- Then I ran the Boot-Repair and it actually worked! I was astonished and amazed. I did generate a boot summary to see what had changed, but have not been through it yet. Anyway, I attach it to this post in case it makes me/us any the wiser as to what has made the machine boot again. 
- BTW - it now boots without needing the internal 4T HD connected, but boots with it connected too.
- The 4T HD is not making the unhappy noises it was making which started my attempts at repairs a week ago. The regular sounds were similar to the usual start-up click-click sounds, Who knows what might have caused that?
- also hope that the machine does not hang if left running for a day. Will see.....
Thanks for your support - perhaps Linux will eventually after many years become my predominant computer working environment!!

---

