---
title: "Dual Boot(Windows 8.1 and Ubuntu 14.10 64bit) Menu isn't displaying."
date: 2015-01-08
forum: Installation &amp; Upgrades
---

### Post by PJhari on 2015-01-08
[COLOR=#141823][FONT=Helvetica][ASK] [HELP]

hi i installed ubuntu 14.10 on my win 8.1 64bit. Successfully installed through "SOMEWHERE ELSE" option by watching this video.[/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica][https://www.youtube.com/watch?v=hOz66FC0pWU](https://www.youtube.com/watch?v=hOz66FC0pWU)[/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]But after reboot.. i was unable to see any dual boot option while booting and only win 8.1 is directly loading.
Help?
FASTBOOT IS DISABLED AND BOOT REPAIR IS DONE.
[http://paste.ubuntu.com/9693494/](http://paste.ubuntu.com/9693494/)
[/FONT][/COLOR]

---

### Post by PJhari on 2015-01-08
[B][COLOR=#141823][FONT=Helvetica][ASK] [HELP]

[/FONT][/COLOR][/B][COLOR=#141823][FONT=Helvetica]**hi i installed ubuntu 14.10 on my win 8.1 64bit. Successfully installing through "SOMEWHERE ELSE" option by watching this video.**[/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]**[https://www.youtube.com/watch?v=hOz66FC0pWU](https://www.youtube.com/watch?v=hOz66FC0pWU)**[/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica][B]But after reboot.. i was unable to see any dual boot option while booting and only win 8.1 is directly loading.
Help?[/B]
**FASTBOOT IS DISABLED AND BOOT REPAIR IS DONE.**
[B][http://paste.ubuntu.com/9693494/](http://paste.ubuntu.com/9693494/)


[/B]
[/FONT][/COLOR]

---

### Post by phidia on 2015-01-08
With UEFI comes more complications in dual booting. You could take a look at [this how-to]("http://www.instructables.com/id/Dual-Boot-Ubuntu-and-Windows-8-UEFI/"). Hope that helps.

---

### Post by oldfred on 2015-01-08
What brand/model computer?
What video card/chip?

Install looks normal. 
Can you go inot UEFI menu can choose the ubuntu entry, and/or from one time boot key often f10 or f12 but varies by vendor?

Some vendors modify UEFI to only boot the "Windows" description, so we have work arounds. One is to rename bootx64.efi and copy grub or shim into /EFI/Boot and rename grub to boox64.efi. Then hard drive entry should be allowed to set as default and you boot into grub menu.

Various work arounds.
       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Rename bootx64.efi
      
 HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

 Packard Bell Easynote manually renamed bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
      
 [SOLVED] Trouble installing Xubuntu 14.04 on Toshiba Satellite P55-A (UEFI) - file rename
    [http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)

      
 From live installer mount the efi partition on hard drive, lines with # are comments only:
#Mount efi partition:
mount /dev/sda2 /mnt
#only if not already existing, You already have this folder. But others may not:
mkdir /mnt/EFI/Boot
cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
# If new folder created, the bootx64.efi will not exist, skip this command
mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
# make grub be hard drive boot entry in UEFI. If not existing, may have to update UEFI also with efi bootmgr.
mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi

---

### Post by oldfred on 2015-01-08
Threads merged. Please do not create duplicate threads on same topic.
We all are volunteers and need to know what suggestions have already been made to avoid duplication and wasted effort.

---

