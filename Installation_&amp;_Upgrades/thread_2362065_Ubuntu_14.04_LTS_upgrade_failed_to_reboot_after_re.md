---
title: "Ubuntu 14.04 LTS upgrade failed to reboot after reset; WUBI root.disk is size 0"
date: 2017-05-23
forum: Installation &amp; Upgrades
---

### Post by aboldventure on 2017-05-23
I had a WUBI install of 14.04 LTS which was running great; performed the upgrade in preparation to move to 16.04 LTS. All was fine up to the point were the upgrade needed to reset the machine.

Upon reset, the Linux boot could not mount the root FS. The error was "File not found" for each of the mount commands.

Booting back into windows, I ran CHKDSK D: /F (The D: drive is where the Ubuntu folder is for WUBI). There were errors and corrections.

Checking the ubuntu folder showed all the expected files, but I noticed root.disk has a size of 0 (zero). This seems incorrect. The swap.disk is rather large at over 300MB.

I have looked at the*.CHK files at the root of the D: drive, they all appear to be related to my windows steam vault install which has been badly behaving the last several window boots. ( I now have it disabled).

I am at a loss as to how to proceed, perhaps someone could give some insight.

My hope is to move to Ubuntu 16.04 LTS using GRUB and with a proper partition, but the best path is to not lose the library installs I have on the original root.disk. I do have a backup of my own work, so there would not be a loss there if recovery were not possible.

Thanks

---

### Post by oldfred on 2017-05-23
The last supported version of wubi was 12.04. Not sure how you got 14.04 to work till now.
       Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)
[https://bugs.launchpad.net/wubi/+bug/1478239](https://bugs.launchpad.net/wubi/+bug/1478239)

Not many old timers here that remember wubi. I never used it.
And wubi was not meant for longer term use. Even the developer of wubi expected you to upgrade to a full partitioned install if you like Ubuntu at the next version release.
Wubi does not work with UEFI/gpt and all new systems with Windows 8 in 2012 were UEFI/gpt, so intended market of Windows users ceased to exist.
 
The root.disk is where all your data is/was. If now 0, it sounds like Windows lost it.
Do not even know if this is still good or not.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by aboldventure on 2017-05-24
Thank you for your reply. Very informative.

As it stands, I will let go of trying to recover the WUBI install. I have my work backed up. I would just have to go through the large install script to recover all the installs.

I plan on doing a dual boot (using grub) of 16.04 LTS, perhaps going forward, I would fair better.

Thanks greatly

---

### Post by aboldventure on 2017-05-25
For those how might see this thread in the future, I'd like to add my own discovery.

Having given up on recovering my root, I was in the position to run an experiment. The cause of the failure was not letting the reboot after "Restart to Continue" proceed to completion. The reboot has some loader noise which is disconcerting -- "sba device i/o errors etc.". The Ubuntu "cylon" status bar would continue for some time. Originally I restarted after about on hour. That was the error. This process on WUBI/Window 7 would take almost 2 hours if left to proceed unhindered. Terminating this prematurely will cause the loss of your root.disk (a possibly other stuff as well).

You can also experience this with a side by side install if you don't let the process complete. Be prepared on some laptops not using SSD to take upwards of 1 to 2 hours for the first boot after install.

I hope that is helpful,
Thanks

---

### Post by oldfred on 2017-05-25
First boot should not take that long.

Occasionally boot can be longer as Ubuntu runs fsck on ext4 partition.
But since converting to ext4, it often relies on the self check internally and does not do the time consuming full fsck.

I know older installs like back with 12.04 had a setting where every 40 or 60 boots it would run the full fsck.

Internal fsck on wubi and if major issues then I could see a fsck taking very long, perhaps waiting to time out.

---

### Post by hakuna_matata on 2017-05-26
> **aboldventure said:**
> For those how might see this thread in the future, I'd like to add my own discovery.

Thank you for adding your discovery. Some notes about your experiences: 
> **aboldventure said:**
> 
I do have a backup of my own work, so there would not be a loss there if recovery were not possible.

The backup of your own work was a good idea. It is always a good idea to create a backup before you upgrade. That doesn't depend on Wubi.

For Wubi you can create a backup by copying the root.disk (and possible other disks except swap.disk) to a save place. If something goes wrong during upgrade, you can easily restore your backup. Or if you decide to migrate Wubi to real partitions you can use your copy of the root.disk. Therefore it is not necessary to run the installation within root.disk. You can also run the [migration script]("https://help.ubuntu.com/community/MigrateWubi#Automatic_migration") from a [Live CD/DVD/USB]("https://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install").
> **aboldventure said:**
> 
but I noticed root.disk has a size of 0 (zero).

As far as I know, Windows marks corrupted files with a size of zero. But that doesn't mean always that the file is gone forever. see e.g. [http://www.easeus.com/file-recovery/restore-0-byte-files.html](http://www.easeus.com/file-recovery/restore-0-byte-files.html) (fix 2 and fix 3)
> **aboldventure said:**
> 
Originally I restarted after about on hour. That was the error. This  process on WUBI/Window 7 would take almost 2 hours if left to proceed  unhindered.

On my experience, upgrades of a Wubi installed Ubuntu are often very slow. Additionally, for 14.04 you need a patch for [an initramfs issue]("https://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted"). It is necessary that the patch is not deleted during the upgrade because 16.04 needs the same patch. As far as I know, there are also reports that the [rw-patch]("https://askubuntu.com/a/454943") within Grub has disadvantages if real problems with the file system of the root.disk occur. So for [Wubiuefi]("https://github.com/hakuna-m/wubiuefi"), we use a variant of the [initramfs-patch]("https://askubuntu.com/a/552041"), which also mounts the root.disk with read-/write access but with the possibility of a fallback to read-only access.

---

