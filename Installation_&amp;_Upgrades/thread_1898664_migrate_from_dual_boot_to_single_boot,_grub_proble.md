---
title: "migrate from dual boot to single boot, grub problem"
date: 2011-12-21
forum: Installation &amp; Upgrades
---

### Post by goodbye-windows(tm) on 2011-12-21
I just deleted my windows 7 partition as I just don't need it anymore. 

But, the grub screen still appears and I have to choose between windows 7 and ubuntu.

I'd like to eliminate the grub screen totally if possible....or, at the minimum eliminate the line that says 'boot to windows'.

After I deleted the windows partition, I did a 'sudo update-grub' in terminal, but the issue seems to be that it is still finding sda2, which is the windows recovery partition...hence it thinks windows is still installed. When looking at the partition, I found sda2 was listed as 'bootable', so I used gparted to eliminate the bootability and retried. But, after doing the grub update command, grub still finds windows 7 partition and lists it when grub starts.

Is there anyway to eliminate the grub screen or to change the screen so windows 7 does not appear as an option when grub starts?

TIA

Art

PS:system is new dell 15r laptop, i5 processor and 6 gb of ram, running the new ubuntu version.

---

### Post by JRV on 2011-12-22
To hide the grub menu:

```

gksudo gedit /etc/default/grub

```
Uncomment the "GRUB_HIDDEN_TIMEOUT=0" line, and then:

```

sudo update-grub

```


To remove Windows 7 from the grub menu:

```

sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub

```

---

### Post by oldfred on 2011-12-22
Grub does not use boot flag. It searches for files it knows are boot files & if it finds them, it assumes it is a bootable partition. 

You can delete (or rename) the Windows files. But, some find they want to go back to Windows for one application or the other. 

Did you make a backup before deleting? If not use recovery partition to make the set of DVDs so you could reinstall if ever needed and then you can delete entire recovery partition.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe

---

