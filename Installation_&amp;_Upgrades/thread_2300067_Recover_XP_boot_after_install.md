---
title: "Recover XP boot after install"
date: 2015-10-23
forum: Installation &amp; Upgrades
---

### Post by Micah_Denn on 2015-10-23
Okay so I installed alongside XP using the automatic setup option in the installer.

Windows shows in grub but I only get a blinking cursor when I try to boot it.
I ran boot-repair, (boot-info: [http://paste.ubuntu.com/12901732/](http://paste.ubuntu.com/12901732/)) but that didn't fix it.

I booted the recovery console on an XP disk and ran fixboot and fixmbr. After that the machine didn't even boot to grub.

I ran boot-repair again, (boot-info: [http://paste.ubuntu.com/12901980/](http://paste.ubuntu.com/12901980/)) and now I have grub back but I still can't boot windows.

Any suggestion?

---

### Post by yancek on 2015-10-23
The link below has an example of fixing the MBR on xp, it is the microsoft site.  You might check the example to see if there are any differences in what you did and what they recommend.  

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

Your boot repair shows Grub in the MBR pointing to the correct partition with grub.cfg which has an entry for xp pointing to the correct partition with the correct UUID.  You will need to give a little more detail than can't boot windows.  Any error messages, blinking cursor, blue screen?

---

### Post by Micah_Denn on 2015-10-23
> **yancek said:**
> You will need to give a little more detail than can't boot windows.  Any error messages, blinking cursor, blue screen?
Thanks for replying.

I get no errors, just blinking cursor.

---

### Post by oldfred on 2015-10-23
Grub only boots working Windows. 
When you restored the Windows boot loader did it boot Windows correctly?
After any partition resize, Windows needs chkdsk. You can only run that from Windows, a Windows installer or a Windows repair CD or flash drive.

You also show a newer 4K drive, but first partition starts at the old sector 63. With Windows 7 they changed to sector 2048 and Linux changed soon after to use 2048. So your XP is not an original install as there were not 4K drives back then. Is it a copy from another drive and copy did not ever work? And then if a newer system do you have AHCI on? I had to turn that on to use my SSD, but the XP did not work. And that was a plus to me as I finally got rid of Windows.

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

---

### Post by Micah_Denn on 2015-10-23
> **oldfred said:**
> Grub only boots working Windows. 
When you restored the Windows boot loader did it boot Windows correctly?
After any partition resize, Windows needs chkdsk. You can only run that from Windows, a Windows installer or a Windows repair CD or flash drive.

You also show a newer 4K drive, but first partition starts at the old sector 63. With Windows 7 they changed to sector 2048 and Linux changed soon after to use 2048. So your XP is not an original install as there were not 4K drives back then. Is it a copy from another drive and copy did not ever work? And then if a newer system do you have AHCI on? I had to turn that on to use my SSD, but the XP did not work. And that was a plus to me as I finally got rid of Windows.

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

Okay so after I restored the boot loader windows still didnt boot (I had no grub).
I think this machine got a new HDD and a fresh install of XP a couple of years ago.

I'm currently running chkdsk.
After that's finished I will run ```
sudo parted /dev/sda unit s print
``` in ubuntu and check if all the "start" values are multiples of 8. If any are wrong I will resize the partition in gparted and the run chkdsk again.

---

### Post by oldfred on 2015-10-23
If you really want XP, you have to get it working on its own first.

Moving the start of Windows creates major issues.
Chkdsk may fix it, but sometimes other internal settings cause conflicts and only a reinstall resolves it.
It is more that XP is so old and obsolete now that newer hardware just does not work with it.

---

