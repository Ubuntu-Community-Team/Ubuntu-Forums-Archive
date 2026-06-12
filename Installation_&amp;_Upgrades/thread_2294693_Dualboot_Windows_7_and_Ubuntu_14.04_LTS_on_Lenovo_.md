---
title: "Dualboot Windows 7 and Ubuntu 14.04 LTS on Lenovo Thinkpad T550"
date: 2015-09-12
forum: Installation &amp; Upgrades
---

### Post by Haselmaus on 2015-09-12
Hi

I just bought a Lenovo Think Pad T550 with a 256 GB SSD drive (I know, not much) and Windows 7.
I would like to install Ubuntu 14.04 LTS for Dualbooting. Unfortunately the pre-partition on my drive is
kinda, well, stupid in my sense. There is this unused 7 GB Lot.
I have already created a bake-up stick. Can I erase the Q-Folder to create more space?
Any ideas how I should create my partitions for Ubuntu, since I can just create 4 primary partitions?

Thanks

[ATTACH=CONFIG]264379[/ATTACH]

---

### Post by iulian X on 2015-09-12
> **Haselmaus said:**
> 

I just bought a Lenovo Think Pad T550 with a 256 GB SSD drive (I know, not much) and Windows 7.
I would like to install Ubuntu 14.04 LTS for Dualbooting. [B]Unfortunately the pre-partition on my drive is
kinda, well, stupid in my sense. There is this unused 7 GB Lot. [/B]

Leave that space alone if you dont want to have problems with the SSD in the future, i think is over provisioning : 

[(http://www.kingston.com/us/ssd/overprovisioning)"][URL="http://www.kingston.com/us/ssd/overprovisioning"]www.kingston.com/us/ssd/overprovisioning]("[http://www.kingston.com/us/ssd/overprovisioning)[/URL]

[http://ubuntuforums.org/showthread.php?t=2294472&p=13354943#post13354943](http://ubuntuforums.org/showthread.php?t=2294472&p=13354943#post13354943)

---

### Post by Bucky Ball on 2015-09-12
Welcome. As you have Windows 7, it is probably installed in UEFI mode if it came preinstalled in the machine. Get into the BIOS and have a look around. Do you see any evidence of UEFI or fast startup? If you are installed in UEFI and you are intending to dual-boot with Windows, you need to install Ubuntu in UEFI mode, and yes, you can then have more than four partitions. In this case, you don't need to wipe any partitions or drives. You need to make some space, though, as you have nowhere to install Ubuntu.

Tell us how you go with the BIOS, give us more detail about the final result you are after, then we'll see where to go from here.

PS: You've created a backup system USB? Windows recovery USB? Be sure of this as this is your only way to reinstall Windows if things go pear-shaped (or selling the machine for instance).

You can do wipe the drive using the Ubuntu install media, but provide more info, first. :)

---

### Post by Haselmaus on 2015-09-12
Thank you. 
I am not completely new to Ubuntu, but new to ThinkPads and SSD drives.
I already checked before I bought the computer if dual boot is possible, yes, there is UEFI (this was a precondition, otherwise I would have decided for another model)
Actually I prefer to work only with Ubuntu, but I sometimes need Windows for "special" occasions.
I created a recovery medium like it is explained here [https://support.lenovo.com/us/en/documents/ht004960](https://support.lenovo.com/us/en/documents/ht004960)
(Lenovo sends no back up DVD) That's the reason, why there is an separate Back-up drive at lenovo Computers, which take also some space (about 15 GB)

---

### Post by yancek on 2015-09-12
The "Q" folder you refer to is your Recovery partition.  If you created a recovery disk when you first booted windows, you would use that to access the recovery partition and set windows back to factory default settings.  If you delete that partition, your recovery disk will be useless.  The link you posted explains how to do this.  If you have a complete backup of some type of the windows systems I suppose it won't matter.  If you want to install Ubuntu, shrink the partition you have the windows system on as it is over 200GB.  Use the Disk Management tool in windows to do that.

---

### Post by oldfred on 2015-09-13
Even if your hardware is UEFI, your  install is in BIOS boot mode or CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

And in BIOS mode you have the 4 primary partition limit.
Windows only boots in BIOS mode from MBR(msdos) partitioned drives, so you cannot easily convert to UEFI with gpt partitioning.

      
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

