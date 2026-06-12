---
title: "After upgrade to Win10: System starts directly Windows10, no grub menu appears"
date: 2020-04-01
forum: Installation &amp; Upgrades
---

### Post by tobiaz on 2020-04-01
[COLOR=#222222][FONT=Arial]Hi,[/FONT][/COLOR][COLOR=#222222][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#222222][FONT=Arial]I have a dual boot PC (windows + ubuntu16.04). [/FONT][/COLOR]
[COLOR=#222222][FONT=Arial]The ubuntu16.04 was originally a ubuntu14.04 that I upgraded several months ago.[/FONT][/COLOR]
[COLOR=#222222][FONT=Arial]In January, I updated from windows 7 to windows 10. 
[/FONT][/COLOR]
[COLOR=#222222][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#222222][FONT=Arial]Afterwards Ubuntu was not accessible any more, as no grub(2?) menu appeared.
[/FONT][/COLOR]
[COLOR=#222222][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#222222][FONT=Arial]I fiddled somehow around and now I am able to start windows 10.[/FONT][/COLOR]
[COLOR=#222222][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#222222][FONT=Arial]Unfortunately, the grub(2?) menu still does not appear during startup of the PC.
[/FONT][/COLOR]
[COLOR=#222222][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#222222][FONT=Arial]Today I did some activities following [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 
[/FONT][/COLOR]
[COLOR=#222222][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#222222][FONT=Arial]The latest log can be found here: **[https://paste.ubuntu.com/p/6rm5n7wgKW/](https://paste.ubuntu.com/p/6rm5n7wgKW/)**
[/FONT][/COLOR]
[COLOR=#222222][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#222222][FONT=Arial]What can I do to get grub(2?) again working so that I can have both Windows and Ubuntu?[/FONT][/COLOR]
[COLOR=#222222][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#222222][FONT=Arial]Thanks in advance,


Tobiaz



[SIZE=1]PS: if it helps, this is the list of my today's (not very systematic) tries. Some tries lead to a bootable Windows 10 configuration, others not.[/SIZE]

[SIZE=1]
[/SIZE]
[SIZE=1][https://paste.ubuntu.com/p/Q27zqXjMXJ/](https://paste.ubuntu.com/p/Q27zqXjMXJ/)
[https://paste.ubuntu.com/p/pB5rvmCd37](https://paste.ubuntu.com/p/pB5rvmCd37)
[https://paste.ubuntu.com/p/bfBcK4md4N/](https://paste.ubuntu.com/p/bfBcK4md4N/)
[https://paste.ubuntu.com/p/NJds5CCdXG](https://paste.ubuntu.com/p/NJds5CCdXG)
[https://paste.ubuntu.com/p/Rvp5njQxpQ](https://paste.ubuntu.com/p/Rvp5njQxpQ)
[https://paste.ubuntu.com/p/6rm5n7wgKW](https://paste.ubuntu.com/p/6rm5n7wgKW)[/SIZE]



[/FONT][/COLOR]

---

### Post by oldfred on 2020-04-01
You have been bit by the Windows bug.
They may call it a feature? 
you have to restore partition & reinstall grub to MBR. 

Make sure Windows 10's fast start up is off. And have a way to temporarily restore a Windows boot loader to MBR as Windows updates will turn fast start up back on & then grub will not boot Windows. You have to restore Windows boot loader, fix Windows & restore grub. This hassle is avoided with UEFI installs.

Windows "forgets" to write Linux logical partitions on major updates in BIOS mode.
Partition and data is still there if not otherwise erased and you just need to add back the missing partition table entry.
Note that you have a large gap in your extended partition which is where your Linux partition is.

```
Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *           63    803249    803187 392.2M  7 HPFS/NTFS/exFAT
/dev/sda2          803250 391595085 390791836 186.4G  7 HPFS/NTFS/exFAT
/dev/sda3       391596032 392781823   1185792   579M 27 Hidden NTFS WinRE
/dev/sda4       [COLOR=#ff0000]392783870[/COLOR] 976771071 583987202 278.5G  5 Extended
/dev/sda5       [COLOR=#ff0000]926613504[/COLOR] 976771071  50157568  23.9G 82 Linux swap / Solaris


```

Your Linux partition will be a few sectors after the start of the extended and end a few sectors before the start of swap.
I think partitions have to have 1 or 2 sectors as a minimum separation, but may have more.

Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988) &
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[https://www.gnu.org/software/parted/manual/parted.html#rescue](https://www.gnu.org/software/parted/manual/parted.html#rescue)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[https://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition](https://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition)

---

