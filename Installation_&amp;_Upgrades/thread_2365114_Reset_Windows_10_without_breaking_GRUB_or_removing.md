---
title: "Reset Windows 10 without breaking GRUB or removing Linux"
date: 2017-07-02
forum: Installation &amp; Upgrades
---

### Post by adhdluke on 2017-07-02
I have Ubuntu 16.04 MATE and Windows 10 set up to dual-boot on my laptop. I want to do a reset (Keep files, reinstall Windows) to attempt to fix some issues. I'm very wary of doing this, because I want to keep my files, and my Linux installation. How should I go about doing this?

---

### Post by yancek on 2017-07-02
What exactly do you mean by 'reset'?  If you are going to do a recovery to factory default settings I expect you will lose any data you have including the Ubuntu installation.  If you are planning to do  a complete re-install of windows 10, you can select the 'Custom' installation option and install it to the current windows partition(s).

---

### Post by oldfred on 2017-07-02
Is system BIOS/MBR or UEFI/gpt?
Windows often forgets with MBR to include any Linux logical partitions when it rewrites partition table. Data is still there, but entry in partition table is gone. Often recoverable, but your only safe way of doing this is to make sure your back up is current. 
You do have backups?
 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by copify on 2017-07-03
> **adhdluke said:**
> I have Ubuntu 16.04 MATE and Windows 10 set up to dual-boot on my laptop. I want to do a reset (Keep files, reinstall Windows) to attempt to fix some issues. I'm very wary of doing this, because I want to keep my files, and my Linux installation. How should I go about doing this?

Take backup Windir/User/{your user}/ 
Take backup Desktop
Take backup what you don't want to lose
-----
Boot Windows using it's DVD then repair it. the most case you won't lose anything but personally I suggest to Delete old windows driver then install fresh.

---

