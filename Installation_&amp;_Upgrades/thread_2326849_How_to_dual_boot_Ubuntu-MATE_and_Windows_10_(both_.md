---
title: "How to dual boot Ubuntu-MATE and Windows 10 (both UEFI)"
date: 2016-06-05
forum: Installation &amp; Upgrades
---

### Post by khanhoct on 2016-06-05
My laptop already installed Windows 10 UEFI and I want to dual boot with Ubuntu-MATE but: [COLOR=#ff0000]**I want to keep Windows Boot Loader**[/COLOR], it show like:

[http://i.stack.imgur.com/ga0a6.png](http://i.stack.imgur.com/ga0a6.png)

I refer to some tutorial but they do not have UEFI and use EasyBCD ([COLOR=#ff0000]**EasyBCD does't support UEFI Boot**[/COLOR]).
Please help me, thanks :P

---

### Post by oldfred on 2016-06-05
Please attach screen shots, not post in line. Not everyone has high speed Internet.
Easy to attach with Forum's advanced editor and paper clip icon.

If UEFI, best not to use EasyBCD. It not really required.

Use Windows to shrink the NTFS partition to make unallocated space for Ubuntu. Reboot immediately so it can run chkdsk and update to its new size.
Make sure fast start or the always on hibernation is off.
So not choose any of the full drive or full drive encrypted options as that will erase Windows. And if fast start not off, the install side by side option may not be shown. If familiar with partitions you can manually partition, either before hand or during install. 

Many more details if interested in link in my signature below.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
Also shows Windows 8 screens or similar to Windows 10
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

---

### Post by khanhoct on 2016-06-05
> **oldfred said:**
> Please attach screen shots, not post in line. Not everyone has high speed Internet.
Easy to attach with Forum's advanced editor and paper clip icon.

If UEFI, best not to use EasyBCD. It not really required.

Use Windows to shrink the NTFS partition to make unallocated space for Ubuntu. Reboot immediately so it can run chkdsk and update to its new size.
Make sure fast start or the always on hibernation is off.
So not choose any of the full drive or full drive encrypted options as that will erase Windows. And if fast start not off, the install side by side option may not be shown. If familiar with partitions you can manually partition, either before hand or during install. 

Many more details if interested in link in my signature below.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
Also shows Windows 8 screens or similar to Windows 10
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

I installed Ubuntu and can dual boot with Windows 10, but system always use Ubuntu Boot (It has Windows Boot option). But I want to [COLOR=#ff0000]add Ubuntu Boot into Windows Boot[/COLOR] (look like the attached photo), Can I do it like that?
All links in your signature use Ubuntu Boot.

---

### Post by oldfred on 2016-06-05
I do not know Windows, this may help?
[http://askubuntu.com/questions/744697/i-need-to-see-the-bcdedit-for-a-windows10-ubuntu-install-both-by-wubi-and-by-sep](http://askubuntu.com/questions/744697/i-need-to-see-the-bcdedit-for-a-windows10-ubuntu-install-both-by-wubi-and-by-sep)

Many like rEFInd which is a gui based UEFI boot manager:
       [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

---

