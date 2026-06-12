---
title: "boot two distros on 2 different hdd"
date: 2021-11-08
forum: Installation &amp; Upgrades
---

### Post by dshock on 2021-11-08
I have an older desktop with 3 HDD installed. HDa has Manjero 20.3 KDE installed, HDb has  Ubuntu 20.4LTS installed and HDc has linux mint 20.3. All 3 are SATA attached to mobo. I can boot Manjaro and Mint in this configuration but not ubuntu. I can disconnect mint and manjaro and boot ubuntu as a seperate drive. How can Iget all 3  to boot from the boot screen that lists all 3 drives?

---

### Post by TheFu on 2021-11-08
Are all legacy BIOS boot or 
are they all UEFI.

You cannot mix. We'll, you can, but it will be a major hassle to switch between the legacy and UEFI booting systems.  

Just a guess.

Why not just use virtual machines? Much safer and you can run all 3 OSes + 50 others, without rebooting.

---

### Post by Bashing-om on 2021-11-08
dshock; Hello

I too multi-boot with multiple drives.
I can relate my solution - may not suit your every need - however.

Considering that ALL installs are bios !

I have one install that I consider my primary "work" install that controls all boot codes for all the installs; The secondary installs I isolate such that only selecting that drive in bios boots the selected install ( in the event that I hose up my primary system).

In each of the secondary installs disable  /etc/grub.d/30_os-prober:
```

sudo chmod -x /etc/grub.d/30_os-prober

```
and update grub in these secondary installs - one at a time !:
```

sudo update-grub

```

then in your primary run the update to propagate the changes:
```

sudo update-grub

```

os-prober in the primary will pick up the other installs for its boot menu - while with os-prober disabled in the secondaries will only see the boot code for that single instance. This also prevents recursion of the boot codes !

Alternately I do highly recommend Cavsfan's MaintenanceFreeCustomGrub2Screen that has the added bonus of pretty pictures :D
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

[INDENT]ain't nothing but a thing[/INDENT]

---

### Post by grahammechanical on 2021-11-08
Assuming that HDa is actually sda then load Manjaro and run

```
sudo update-grub
```

Does the printout show Ubuntu on sdb and Linux mint on sdc? If it does then with sda having boot priority you will see a Grub boot menu that will allow you to chose between the three operating systems. Every time the other OS get a kernel upgrade you must then run that command again. All this is assuming that the three installs are either UEFI or BIOS and not mixed. As queried by The Fu.

Regards

---

### Post by oldfred on 2021-11-08
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO (unless 21.10)
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If BIOS better to have each grub installed to each MBR, but BIOS will only directly boot one. Then better to modify that grub to not need updates with every change of kernel or grub in the other installs. 
If UEFI, only one system will be default.
How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

---

### Post by yancek on 2021-11-09
Running boot repair as suggested by oldfred above would be the best way to get detailed information to resolve your problem.
This would be a good time to get out those detailed notes you took during each install indicating whether some or all installs are Legacy or UEFI or a mix of the two. There are quite a number of possibilities and they should all be answered with the boot repair output.

---

