---
title: "Can't boot back to windows"
date: 2013-01-22
forum: Installation &amp; Upgrades
---

### Post by Shaddonius on 2013-01-22
I have been using windows until my video card died. Then, I tried switching between various linux distros (installing them on my other hard drive) and xubuntu seemed pretty economically while also user friendly. But the thing is, I can't get windows for the hell of it to boot back. Trough various googling, I heard I'm supposed to swap hdds in GRUB2 but I have no idea how to do that since all guides are for GRUB. Here's my partition setup :

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e069f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   307470335   153734144   83  Linux
/dev/sda2       307472382   312580095     2553857    5  Extended
/dev/sda5       307472384   312580095     2553856   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa2e5b534

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   819202047   409600000    7  HPFS/NTFS/exFAT
/dev/sdb2   *   819202048  1953525167   567161560    7  HPFS/NTFS/exFAT

```

If it's not explicit enough in the pasta (due to formatting), Xubuntu 12.10 x64 is installed on sda1 and Windows 7 Pro x86 is installed on sdb2.

---

### Post by darkod on 2013-01-22
Depending if the XP disk was present when installing xubuntu, first try in terminal:
sudo update-grub

Does that detect XP on sdb2? If it does, it should add it to the boot menu. Reboot and try booting it.

---

### Post by Shaddonius on 2013-01-22
> **darkod said:**
> Depending if the XP disk was present when installing xubuntu, first try in terminal:
sudo update-grub

Does that detect XP on sdb2? If it does, it should add it to the boot menu. Reboot and try booting it.

Sadly, this does not work. I should also mention in the OP that it's about windows 7. Here's the result : 

```

shaddox@C3PO:~$ sudo update-grub
[sudo] password for shaddox: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-36-generic
Found initrd image: /boot/initrd.img-3.2.0-36-generic
Found linux image: /boot/vmlinuz-3.2.0-35-generic
Found initrd image: /boot/initrd.img-3.2.0-35-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
done

```

---

### Post by darkod on 2013-01-22
Are you sure you didn't have the small win7 partition with its boot files on sda and you deleted it while installing xubuntu? Win7 often puts boot files on another partition, which can sometimes be on another disk. If you delete this partition, it can't boot.

From xubuntu open sdb2 and see if these files/folders exist:
/bootmgr
/boot/BCD

Those are the win7 boot files. If they are not on sdb2 or sdb1, you deleted them. Grub2 looks only for boot files, not the actual files. Your win7 can be there, without boot files it won't get detected and booted.

---

### Post by Shaddonius on 2013-01-22
> **darkod said:**
> Are you sure you didn't have the small win7 partition with its boot files on sda and you deleted it while installing xubuntu? Win7 often puts boot files on another partition, which can sometimes be on another disk. If you delete this partition, it can't boot.

From xubuntu open sdb2 and see if these files/folders exist:
/bootmgr
/boot/BCD

Those are the win7 boot files. If they are not on sdb2 or sdb1, you deleted them. Grub2 looks only for boot files, not the actual files. Your win7 can be there, without boot files it won't get detected and booted.

Ohhhhhhh, so this was it. Thanks for the tip, I did not know this. 

Is there any way to fix this other than reinstalling the OS?

---

### Post by darkod on 2013-01-22
There should be, if you have the win7 dvd (or at least a rescue cd). sdb2 already has a boot flag on it, which is good, because it should have it.

I suggest you shut down and disconnect the ubuntu disk so that win7 doesn't mess up anything. After that boot with the win7 dvd, after selecting the language, etc, on the next screen there should be a Repair This Computer option at the bottom.
Run the process and it should fix the missing boot files. You might need to run it 3-4 times because it seems to fix one thing at a time.

If the auto repair doesn't work even after that, there are some manual commands. Lets see how the auto process does first.

If you prefer the manual commands, you have them here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Look at the first post in the section for Vista and 7. In fact, the manual commands might be better than the auto method, I'm not sure since I never needed to use this.

After win7 can boot by itself, connect the ubuntu disk again and make sure you boot from it, otherwise win7 will load directly. The first time there will be no win7 in the grub menu until you boot ubuntu once and run the update-grub again. That should detect the repaired win7 boot files.

---

