---
title: "Boot Repair"
date: 2015-12-09
forum: Installation &amp; Upgrades
---

### Post by your_name6 on 2015-12-09
Hello,

my computer won't load after the newest automatic Windows 10 update. Following the first automatic restart during the update, a message will pop up:

 error:no such partition. 
entering rescue mode. 
grub rescue>

I run both Windows 10 and ubuntu 15.10 (ubuntu installed after win10). I tried Boot-Repair, which finished successfully, but nothing changed after restarting the computer. The URL that popped up was [http://paste.ubuntu.com/13858460/](http://paste.ubuntu.com/13858460/)

Thank you for any kind of help.

---

### Post by grahammechanical on 2015-12-09
> 1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

There is your answer. Ubuntu is gone.

---

### Post by oldfred on 2015-12-09
Post this, but if BIOS/MBR Windows update forgets to write Linux partition to partition table. Data is still there, and you just need to add entry back into partition table with testdisk or parted rescue.
To see details by sector:
 sudo parted /dev/sda unit s print

      
 [http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

### Post by your_name6 on 2015-12-09
@[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323") Thank you for the answer, I will install ubuntu again. However, my main problem is that no OS will run, and the computer won't work. I'm a beginner and have no experience, could you maybe give me some advice as to how to make any OS work? Do I have to re-install Windows?

---

### Post by oldfred on 2015-12-09
Is system UEFI or BIOS?
But either way you need to get into UEFI/BIOS and set flash drive or DVD as first in boot order, or boot with one time boot key often f10 or f12.

But with UEFI, it also has fast boot which is different than Windows fast start up or always on hibernation.
If fast boot on in UEFI, you may need to cold boot or totally power down system, remove battery if laptop & hold power switch for 10 sec or so to totally drain system. And on boot immediately press correct key to get into your UEFI/BIOS. Some system have to have motherboard battery removed to reset it.

And whether UEFI or BIOS you must have the Windows fast start up off.

---

