---
title: "Can't access Windows 8.1 after dual-boot install Ubuntu 14.04"
date: 2014-11-24
forum: Installation &amp; Upgrades
---

### Post by Jan_De_Clercq on 2014-11-24
Dear anyone

I have a Lenovo Thinkpad e11 with Windows 8.1 pre-installed on it. But I want the options of a dual-boot. So I followed a guide how to install Ubuntu 14.04 next to Windows ([http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)). I've followed the steps, but now I'm stuck. I've been reading and trying for 3 days now and am getting frustrated.

From what I understand, Windows is still on my hard drive (on a different partitition than Ubuntu), I just have no clue how to access it.

What do I want to know:
* how to access Windows 8 again
* how to have a Windows option in Grub

BACKGROUND INFORMATION
In Grub, Windows doesn't show as an option. I disabled Secure boot in BIOS before, so that I could install Ubuntu, but I've tried re-enabling it but Windows seems to be gone. (I've tried many other things in BIOS as well, like changing the boot border, disabling quick boot etc.) On this forum and others, people suggest many things, from installing programs to using code in Terminal or Grub. But as I'm fairly new to Ubuntu, I don't understand what my problem really is and fear ruining my new laptop. I only have a WindowsImageBackup directory for back-up, but that doesn't appear to work as a boot drive.

->If anyone wants to have a look at my specific problem, I'd be much obliged.
Ubuntu installation log: [http://paste.ubuntu.com/9149205/](http://paste.ubuntu.com/9149205/) (the installation guide I followed says an error is normal, therefore I had to use Boot-Repair)
Boot-repair log: [http://paste.ubuntu.com/9233281/](http://paste.ubuntu.com/9233281/)

---

### Post by oldfred on 2014-11-24
Is this yours?
[http://paste.ubuntu.com/9195866/](http://paste.ubuntu.com/9195866/)

If so I hope you made full backups of your Windows & efi partitions before install.
(step 1 of instructions, you said you used).

That link shows just an efi partition, Ubuntu install and swap. If you did the Something Else install, you would not have erased Windows. It is the auto install option on a re-install that may  say it is erasing all of Ubuntu when it erases all of drive.

       Reinstall says overwrite Ubuntu but it also erases existing Windows or any other partitions.
Sept 2014 Fix being released for one drive installs, but mulitiple drive installs must use Something Else. And fix is not in current versions.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by Jan_De_Clercq on 2014-11-25
Thanks Oldfred

The link I pasted was wrong (sorry). This is the correct one [http://paste.ubuntu.com/9149205/](http://paste.ubuntu.com/9149205/) (which now shows Windows on the sdb1 partition)

I'll also edit my original post.

---

### Post by yancek on 2014-11-25
Your boot repair output shows the FAT32 EFI partition (sda1) and the Ubuntu system partition (sda2) and the swap partition (sda3).  You have a windows partition on sdb1 which is an 8GB flash drive.  I'm guessing you didn't have your windows 8 on a flash drive so I hope you made a backup!   The flash drive does not show the standard windows boot files.

---

### Post by oldfred on 2014-11-25
The sda1 is the efi partition which is just for UEFI boot files.
The sdb1 is the FAT32 formatted live installer.

You do not show any Windows.

Did you make backups?
Vendors do not provide restore DVD set but have partition on drive that you can use to make reinstall DVD set, but you also erased that. Did you make restore set as soon as you received computer as vendors suggest.

---

### Post by Jan_De_Clercq on 2014-11-25
Thanks for your answers. 

I didn't make a boot disc. I only have a SystemImageBackup file on an external hard drive. This does not appear to work as a boot drive.

My plan is to contact Tech support and check if they can send me a copy of Windows.

---

### Post by oldfred on 2014-11-25
Some vendors are pretty good about offering a restore image for  a system. It would be the same as you would make from recovery partition. But some others refuse to support a user at all.
One user had just purchased from a local retailer and the store's tech found an identical model on display and made the recovery set of DVDs. Some stores would charge so much that buying a new copy of Windows would be less expensive. 

You can only use your vendor's version to restore or have to purchase full new copy with new product key.

 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

---

### Post by Jan_De_Clercq on 2014-11-26
So I followed your advice and obtained a recovery disc. (Lenovo helpdesk was not helpful; I borrowed the thing from a very friendly computer store)

When I reinstalled, I did see there still was a recovery partitition on the drive, but I just cleaned everything. I'll catch my breath and then give dual-booting another go.

Thanks for the assistance guys!

---

