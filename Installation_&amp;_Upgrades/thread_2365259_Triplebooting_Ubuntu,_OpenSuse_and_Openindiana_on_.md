---
title: "Triplebooting Ubuntu, OpenSuse and Openindiana on Dell XPS 17 2x 500gb HDD"
date: 2017-07-04
forum: Installation &amp; Upgrades
---

### Post by peterrp81 on 2017-07-04
Hi everybody!

I would like as detailed as possible description on how to use grub for installing all these OS´s on my laptop. And also how I may add Windows 10 to those partioning schemes. Is it possible?

Thanks alot:-)

---

### Post by oldfred on 2017-07-04
UEFI or BIOS?
But whichever you need to be sure to install all systems in same boot mode, either all UEFI or all BIOS.
Some of the other Linux default to LVM, but one of LVM's advantages is when it manages the entire hard drive. And Windows cannot be inside an LVM, so only manual LVM install would be possible on part of drive. Some have posted to just use manual install for those that default to LVM to use a standard partition similar to Ubuntu's default install. But Ubuntu can install in LVM if desired.

I know Debian based installs create a link in / to newest kernel, so grub can boot using Link and not need updating from main install (to find a newer kernel in other installs) and still boot newest kernel. Not sure if other distributions have link or not.

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

### Post by johndough2 on 2017-07-04
Hi 

In addition to the helpful info given by oldfred I would like to add that multi-booting with opensuse is not really problematic, Grub being the exception.

I triple boot this lappy with W10, opensuse and Debian 9 and it all runs nicely.

The number of partitions you create can be over 10 and care and naming are vital.

 for windows 3  boot, efi and C:
for opensuse 3 /, home and swap

at this point I have had problems with too many swap files, sometimes suse will write setings out to swap and reload from there, if ubuntu uses the same swap then opensuse can take a long time to re-boot, so the choice is to give a clean area for suse to write to.

A common area NTFS where all OS's can have letters and piccies.

Add in the other OS needs and you can see potential confusion.

Where practicable an A4 sized piece of paper, legal probably in the US of A, and write out the table and names of partitions and try to find the option to mount by name, SuseRoot SuseHome and SuseSwap means I get to understand rather than a long string of hex.

I would add/allow a small area for a Grub Boot partition.

I hope you are successful in 4 OS's and tell us about the experience.

---

