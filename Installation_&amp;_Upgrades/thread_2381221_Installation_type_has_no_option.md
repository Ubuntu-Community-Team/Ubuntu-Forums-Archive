---
title: "Installation type has no option"
date: 2017-12-28
forum: Installation &amp; Upgrades
---

### Post by tezarin on 2017-12-28
Hi all,

I downloaded an Ubuntu 16 iso file and created a bootable image using Rufu on my Windows machine. Now booted from my USB and trying to install Ubuntu as a dual boot with my Windows. Got to the "Install (as superuser)" section, but under the Installation type there is nothing listed.
When I click the +  - or change  it just hangs. The drop down only has /dev/sda

The only thing that may work if I click a hundred times, is the x at the left corner, then a message pops up: Matacity: Install as superuser is not responding and I have the option to Force Quit or Wait. Then I clicked on the Force Quit and it takes me to the Ubuntu desktop which I don't think it has been installed - It's fully functional but maybe it's just the live try Ubuntu. Then I click on the disk icon (Install Ubuntu 16.04.3 LTS) and this time it gives me the installation types:
/dev/sdd
/dev/sdd1 fat32 ---> size 3867 MB Used 1595MB

Device for boot loader installation:

/dev/sdd1
/dev/sdd ---> My USB drive

Whichever combinations I pick, it keeps giving me an error. Please let me know what to do, I never had installed Ubuntu from a USB before. This new laptop doesn't come with a DVD player and I really want to get this to work.


Thanks

---

### Post by yancek on 2017-12-28
If you are attempting to dual boot with windows, which version of windows do you have?  Do you have 8 or 10?  If so, can you verify that your windows installation is using UEFI/GPT?  Also, if you have windows 8 or 10, you need to turn off fast boot and anything related to hibernation in windows.  Have you used the Disk Management tool in windows to shrink the largest windows partition so that you have unallocated space on which to install Ubuntu?  The output you show is just your flash drive which you are booting from.

---

### Post by tezarin on 2017-12-28
Thanks for your reply. I have Windows 10, turned on the legacy option, disabled the boot security. I now can see a lot of devices, but when I pick the one which is the larges I get the same error as this post: [https://askubuntu.com/questions/610873/ubuntu-error-the-partition-table-format-in-use-on-your-disks-normally-require/610888](https://askubuntu.com/questions/610873/ubuntu-error-the-partition-table-format-in-use-on-your-disks-normally-require/610888)

---

### Post by oldos2er on 2017-12-28
So, you're installing Ubuntu in UEFI mode as suggested in the thread you linked to?

---

### Post by roner2 on 2017-12-28
I just fixed this issue myself, though I do not know if we may be having the same root problem.  Basically there were little remnants leftover on the hard drive, specifically a fat32 partition that made no sense and when we cleared the drive and I ran installation afterwards I was given the proper options on the installation type page.  Hope it helps.

---

### Post by yancek on 2017-12-28
The FAT32 partition was most likely an EFI partition.  The message in the link you posted above in post 3 is telling the user that they need to create a BIOS boot partition in order to use GPT and NOT UEFI which apparently doesn't work with windows but does with Linux.

---

