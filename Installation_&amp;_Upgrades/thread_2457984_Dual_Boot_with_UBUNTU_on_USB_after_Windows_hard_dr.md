---
title: "Dual Boot with UBUNTU on USB after Windows hard drive crash"
date: 2021-02-13
forum: Installation &amp; Upgrades
---

### Post by bigrbubba on 2021-02-13
I have a 2020 HP laptop.  Windows 10 UEFI   I installed some apps and my personal stuff and then cloned the drive .
I decided to check out Ubuntu, But being i didn't have enough room on the hard drive, I burned the install onto a USB stick and installed 18.04 to another USB stick.   All is well and with an F9 at boot up I could boot from the Ubuntu USB install... got it personalized and added a few apps ect.  One recovery app that was a one time only install that I paid money for.  R-Studio for Lunux.

Next my Windows hard drive gets corrupted.   I can still boot Ubuntu UEFI but not windows.  Only the windows partition got corrupted.   I used r-Studio for lunux and it recovered some of the stuff and windows still won't boot.
So rather than corrupt that drive as there is still stuff in there, I cloned the orginal drive with JUST WINDOWS 10 ON IT and installed the clone.  The boot manager now knows nothIng about Ubuntu.  How can I get the UEFI boot menu to see the ubuntu USB pen drive?  It will boot if I turn off secure boot and turn on legacy support, but I really would like it back the way it was.  It will also boot to Ubuntu using the Dead windows drive that at one time had Ubuntu UEFI on it.

My thoughts... Install ubuntu 18.04 (can I use 20.04 install instead) on another USB stick.  That should add the UEFI UBUNTU to the boot manager menu and then just go back to using the old stick of the same size and brand.  Will that work

Is it possible to manually edit the windows UEFI boot manager to add Ubuntu to boot the stick manually?

Cronologically
1. Bought new laptop January of 2020  HP Pavilion 15 500gb NVME
2. Installed 'MY STUFF' on it
3. Cloned the Drive to make a backup in March
4. Decided to Install ubuntu 18.04 on USB stick from another USB stick  All working OK.. can F9 on boot and can see in boot options UEFI windows and UEFI Ubuntu.  Both boot fine, Ubuntu runs off of a 64gb usb stick
5. Windows partition crashes/gets corrupted won't boot.  Ubuntu stick will still boot fine using F9 and selecting Ubuntu
6. I purchase R-Studio for Lunux a one time install app, and recover as much as I can, not all.. windows still wont boot, about 25% is unrecoverable with R-Studio
7. I purchase an NVME external usb drive case and install the 'dead' drive to play with it later.
8. I have a 2 TB NVME drive and cloned the backup to it, and now am back to where I was in march .. missing apps, pix ect AND THE UEFI ENTRY FOR UBUNTU
9. If I plug in the Crashed drive, the UEFI menus come up for Windows and Ubuntu.  If I select ubuntu .. it boots up and I can remove that drive.
10.  I had to turn off secure boot to boot just off of the ubuntu USB stick, but it works.
11.  Windows works, Ubuntu boots up and am trying to recover all the stuff that accumulated in the last year.  Partly successful
12.  If I turn the secure boot back on, I cannot boot Ubuntu from the stick.  That's what I want back  Can this be manually edited somehow?  

My plan
with another 64gb USB stick of the same brand, install Ubuntu 18.04 to that, and have it update the windows UEFI boot manager.  Shut down and put in the other stick, but will it boot up?  If there is a way to manually update the boot mgr or even copy files from the 'dead' windows boot partition, which is intact.

anybody else have 'A PLAN' of action

---

### Post by oldfred on 2021-02-13
Your install to USB drive probably installed grub to Windows drive's ESP.
Better to have ESP and grub installed to ESP on flash drive.
Do you have an ESP on flash drive now, or do you have to make one?
Then you can reinstall grub.

External drives boot directly from UEFI using /EFI/Boot/bootx64.efi whether full install or the installer. The bootx64.efi is somewhat different depending on install.
Your full install probably had create an Ubuntu UEFI boot entry using the ESP on the Windows drive.
You can see UEFI entries:
sudo efibootmgr -v
You will see the GUID or partUUID of the ESP that your installs are booting from.
To see partUUIDs:
lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"

If you have ESP on external you can manually install grub to it, or use Boot-Repair from live installer.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive.

---

