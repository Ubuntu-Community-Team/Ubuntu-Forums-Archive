---
title: "grub2 win8 entry won't boot windows after Ubu. 13.10 64bit install"
date: 2014-02-14
forum: Installation &amp; Upgrades
---

### Post by lestoilnr on 2014-02-14
Gateway DX4831-01e running win 8. PC has fastboot off and doesn't have UEFI. Originally pc had win7.
Installed Ubu. grub boots into Ubu but win8 entries go to Repair windows-fixing Win8 cycle that won't work.  I have Win8 startup,Recover flash drive and full systek backup on ext. usbHD.  Trying recovery or restore give "disk is locked" and tell me to unlockit.
Grub2 has one win8 entry on sda1 and other on sda2.  Installing and running boot-repair with default setting gave me same grub menu as in 1st install.
Even tried "bootrec /fixmbr and fixboot' from win8 startup disk.  Still get "repair-fix cycle" and no Win8 startup.
On Ubu install I chose / on primary partition as before(which worked) and swap and /home on extended parts. Windows only had 3 primary parts.  I shrunk C:\ drive from w/in Win8 for Ubu install.  No error messages showed in Win8.
On other Gateway Ubu and win8 entries worked fine.
Win8 disk shows on live -dvd but not Ubu. desktop.
Any suggestions please.
Added: gparted shows sda1 ntfs PQSERVICE 12GiB sda2 ntfs SystemReserved 100MiB No big win8 partition. sda3 ext4/home 719GiB(was win8 size) sda4 extended 43.87 giB sda5 ext4 / 28.61  sda6  swap  Unallocated space 156GiB. Thx.

---

### Post by lestoilnr on 2014-02-15
Good thing I had win8 backup image and win8 install disks.  Fixed grub problem by recreating  800GiB ntfs partition that had disappeared and reinstalling system.  Still in the process. But can boot into win8 again thru grub. Thx.

---

