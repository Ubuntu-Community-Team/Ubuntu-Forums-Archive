---
title: "Grub menu disappears when running Windows 8 &amp; Linux Multi-Boot"
date: 2013-01-16
forum: Installation &amp; Upgrades
---

### Post by anttepoika on 2013-01-16
I have similar problem. Except that I ran boot repair chekcing the box to rename and backup and I still can get in only once, after that the option disappears from the boot menu. I dont have to open windows at all, just turn off the computer. The url: **paste.ubuntu.com/1537511**

---

### Post by oldfred on 2013-01-16
Welcome to the forums.

Moved to your own thread.
While your boot issue may seem similar, you have a different configuration since you have several other installs. For reference this was old solved thread. Also users that may be able to help do not look at solved threads, since they are solved.
[http://ubuntuforums.org/showthread.php?t=2103778](http://ubuntuforums.org/showthread.php?t=2103778)

Clickable link to your pastebin.
[http://paste.ubuntu.com/1382319/](http://paste.ubuntu.com/1382319/)

Are all your installs in UEFI mode now? You can only boot in UEFI mode or BIOS mode, unless you want to go into UEFI and turn off UEFI and turn on BIOS/legacy boot and vice-versa each time you change.

Have you turned off secure boot and fast boot? Are you booting the ubuntu entry in UEFI menu and using grub menu to chain load to other efi entries?

Do not know about other Linux and how well they work with the new secure boot:
       Multiple installs - Ubuntu, Fedora, Arch based Manjaro, Mint 14
[http://ubuntuforums.org/showthread.php?t=2086602](http://ubuntuforums.org/showthread.php?t=2086602)
[http://paste.ubuntu.com/1382319/](http://paste.ubuntu.com/1382319/)

    This says not every distribution supports secure boot, so Windows 8 may cause issues.
        The State Of Linux Distributions Handling Secure Boot
[http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI](http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI)

I do not think any of the os-prober entries from grub2 will work, you need to add efi chain entries. See bug report which was Windows but applies to all efi boot stanzas.
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by anttepoika on 2013-01-16
I now have it working. Very ugly though... All this trial and error made opening my computer a bit messy with menus, but it works and with that I am satisfied.

I studied little and checked the things you mentioned. Learned a lot and found something to try on in the process. The trick was to choose the partition where my EFI is for the start up files to be placed when installing. Havent found this mentioned before. Well this helped to get me up and running with Ubuntu, but it still did not load any grub menu so I was stuck with Ubuntu and no Windows. Searched a bit more and found some mention about mcafee(among other programs) writing in the hard drive where it should not and messing up the grub. So I deleted it and the problems gone. 

Only thing now is that Ubuntu is all tangled up and not working at all after a short periode of usage. Maybe this might be due to the release being so new? Or propably just broken install or something. I am going to install it one more time(or meny more, if necessary....) and hope that will help. 

Still happy with the results this far and thank you for your help!

---

### Post by oldfred on 2013-01-16
If you are installing in UEFI mode, it does not matter where you say to install grub, it should just install to the efi partition. The UEFI version uses grub-efi not the BIOS version grub-pc.

The issue with a lot of Windows 7 software was the area just after the MBR where grub writes core.img and Windows writes DRM serial numbers and other data. Now Windows has the MSR which looks like an unformatted partition and grub is in efi and install partitions, so there should not be any conflicts with UEFI.

---

