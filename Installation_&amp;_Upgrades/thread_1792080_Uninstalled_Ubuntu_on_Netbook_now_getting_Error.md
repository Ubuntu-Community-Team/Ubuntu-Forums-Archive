---
title: "Uninstalled Ubuntu on Netbook now getting Error"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by Fost325 on 2011-06-27
[LEFT]I'm getting ready to sell my Acer Apsire One netbook. I had Ubuntu Netbook Edition on it. But I needed to remove it to sell it.

I went on to Disk Manager on the XP Partition. I then deleted the Ubuntu Partitions. I then ran the fixmbr.exe file I got from this site [http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php).

After that I went into Acer eRecovery Manager (Since my netbook doesn't have a cd drive it comes with this as a recovery partition) I selected restore to factory conditions and it rebooted itself like normal during a restore. When it started back up it couldn't find anything to boot to.
I now get an (error: no such partition. grub rescue>) error when I try to boot the computer up.
How can I get this back to booting to Windows XP Home.
[/LEFT]

---

### Post by drs305 on 2011-06-27
It looks like Grub is still installed on the MBR.

From the LiveCD, and assuming the Windows partition still has the boot flag and is on sda, try installing lilo and running these commands. Don't run any others and disregard the lilo configuration messages afterward.
```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

This should point the MBR back to your Windows installation. If the boot files are still intact, this should return the boot to the Windows bootloader.

---

