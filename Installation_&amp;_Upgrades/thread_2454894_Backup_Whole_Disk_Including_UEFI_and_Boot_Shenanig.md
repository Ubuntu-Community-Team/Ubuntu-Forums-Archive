---
title: "Backup Whole Disk Including UEFI and Boot Shenanigans"
date: 2020-12-08
forum: Installation &amp; Upgrades
---

### Post by holysword on 2020-12-08
Background: I have to send computer to repair, they will wipe the disk and install some other OS to perform tests.

Therefore, as the title says, I'd like to backup a whole disk - not a partition, a full disk, including everything which is needed to make it bootable.

I tried cloning the harddrive with dd, but the clone was broken (I couldn't even mount it; dd showed no error).

I also tried clonezilla, but it cannot clone NVME disks.

I tried installing Ubuntu 20.04 on a side disk, then copy the / over using rsync, dully updating fstab, but somehow GRUB complains that it didn't find the UUID. However, attempting to update GRUB with update-grub makes it not even bootable anymore (I guess it uses the wrong partition as /boot).

Any suggestions?

---

### Post by oldfred on 2020-12-08
I prefer good backup, but plan on reinstall of Ubuntu.
I backup all my data, some system configuration in /etc, list of installed apps & /home which has user configurations.
Then I can easily reinstall & quickly restore data, settings & apps.

I do like to document configuration with Boot-Repair's Summary Report. But that is just for info.

If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)
[https://ubuntuforums.org/showthread.php?t=2368992&](https://ubuntuforums.org/showthread.php?t=2368992&)

---

### Post by TheFu on 2020-12-08
> **holysword said:**
>  Any suggestions?

Pull the current storage out, insert a cheap 16G replacement ssd/hdd/nvme/what ever. Let the shop figure it out. You keep the existing storage at home.

dd/ddresuce work. The problem is that they clone everything, including the "unique" disk/partition identifiers. That means they cannot be connected to the same system at boot time going forward.  Just 1 of the reasons that images are terrible backups.

When you get the machine back, setup solid backups and test the restore steps every quarter or so.  To many times, people make backups for months or years, but never actually test the restore process.  

Good that you found out issues BEFORE they were needed.

f you post the exact dd command used along with data about the source and target storage AND the environment used to run it, we can help.  For example, dd has to be run from an alternate boot OS environment to get a clean clone. t cannot run on the same OS as what is being cloned.  
There are little caveats about file systems too.

---

