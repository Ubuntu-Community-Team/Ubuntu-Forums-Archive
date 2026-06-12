---
title: "Problems with EFI Boot"
date: 2018-09-16
forum: Installation &amp; Upgrades
---

### Post by simone93 on 2018-09-16
Good morning to everyone,
This morning trying to turn on the pc it gave me the follow errors:
```
error:enviroment block too small.
error: failure reading sector xxx from 'hd0' .
alloc magic is broken at xxx: xxx
Aborted. Press any key to exit.
```

Following some Threads i decided to use boot-repair, but it doesn't fix the problem.

I don' t be able to find how i can do:
```
Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!
```

Here the boot repair paste message:
[HTML]http://paste.ubuntu.com/p/8MPVVD59XS/[/HTML]

---

### Post by yancek on 2018-09-16
Do you have an option on boot to access various boot options such as boot from EFI file?  If you do, select that and see if you can find the file specified in the boot repair report:

> /EFI/ubuntu/shimx64.efi file

Has it been working and just failed?  If so, did you make any changes to the system just prior to the problem and if so, what were they?

---

### Post by oldfred on 2018-09-16
Do not know if this is still valid or not.

[https://askubuntu.com/questions/191852/error-invalid-environment-block-press-any-key-to-continue](https://askubuntu.com/questions/191852/error-invalid-environment-block-press-any-key-to-continue)

Another suggestion has been to totally purge grub and reinstall grub. Easier with Boot-Repair and its advanced options.
       [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by simone93 on 2018-09-16
> **yancek said:**
> Do you have an option on boot to access various boot options such as boot from EFI file?  If you do, select that and see if you can find the file specified in the boot repair report:



Has it been working and just failed?  If so, did you make any changes to the system just prior to the problem and if so, what were they?

I can enter in the Grub and i see:
```
Ubuntu
Advanced option for Ubuntu 
EFI/ubuntu/fwupx64.efi
EFI/ubuntu/mmx64.efi
system setup
```

But with no one i'm able to boot my system.


> **oldfred said:**
> Do not know if this is still valid or not.

[https://askubuntu.com/questions/191852/error-invalid-environment-block-press-any-key-to-continue](https://askubuntu.com/questions/191852/error-invalid-environment-block-press-any-key-to-continue)

Another suggestion has been to totally purge grub and reinstall grub. Easier with Boot-Repair and its advanced options.
       [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

I tried to purge/reinstall the grub but it gave me the same output:
[HTML]paste.ubuntu.com/p/dBQgSVvyJP/[/HTML]

For the other solution that you suggested, i can't find the line that is supposed to be deleted.

Thanks for your help!

---

### Post by oldfred on 2018-09-16
Have you tried Advanced options and the recovery mode boot?

Have you updated UEFI from Asus for your model system?

---

### Post by simone93 on 2018-09-16
Yes, i tried but it gives me the same error.

 2 months ago i upgraded bios version from 300 to 305, using the official guide [https://www.asus.com/support/FAQ/1008859/](https://www.asus.com/support/FAQ/1008859/) .

---

### Post by ubfan1 on 2018-09-16
The /boot/grub/grub.cfg file line 45 has the save_env recordfail   mentioned in question 191852.
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi

---

### Post by oldfred on 2018-09-16
I turn os-prober off and have many other Ubuntu entries. And can boot with a very simple entry.

If you get to grub> or if you get to grub menu and use c for grub command line.
configfile (hdX,Y)/boot/grub/grub.cfg
where X is drive like 0 for sda, and Y is partition like if install is in sda2, (hd0,2).

Or 
set root=(hd0,2)
Linux /vmlinuz root=/dev/sda2
initrd /initrd.img
boot

---

### Post by simone93 on 2018-09-17
Good evening, it's been about 4 hours that I try to fix the problem without any results.
Since I need to work, I decided to format and reinstall ubuntu (16.04.4) after a backup.
The installation was successful, but as soon as I gave the command to upgrade, 16.04.5 was installed and when restarted the computer gave me the same problem.
So I suppose the problem is with the update even if I do not know which, what can I do?

---

### Post by oldfred on 2018-09-17
Does this show an error. Like clearing dirty bit.
       [http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872](http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872)
dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

Ubuntu did something and caused an efibootmgr crash on my system. I thought it was UEFI or grub.
But it turned out to be corruption in my ESP - efi system partition. While Ubuntu read & wrote into the FAT32 ESP, UEFI would not see it.
Running dosfsck said it had an error. But on reboot, UEFI still would not see it, and error re-appeared.
So I backed up ESP, totally refomatted it. And rather than restoring ESP's backups did a full uninstall/reinstall of grub to recreate files & folders in ESP & UEFI boot entries based on new partition. All old entries in ESP are invalid as reformat creates both new UUIDs & GUIDs. UEFI uses GUID to know what partition to use.
And all that worked.
[https://ubuntuforums.org/showthread.php?t=2401166](https://ubuntuforums.org/showthread.php?t=2401166)

[https://bugs.launchpad.net/ubuntu/+source/grub2-signed/+bug/1787692](https://bugs.launchpad.net/ubuntu/+source/grub2-signed/+bug/1787692)

---

### Post by simone93 on 2018-09-19
Good morning,
I do not know how and I do not know why but this morning my computer started with ubuntu 16.04.4, since October 4 I have an important work deadline I would like to block all updates.
After the work deadline, I want to do a clean installation.
Should I close this thread and open a new one later or can I use this?

Thank you all for answering.

---

### Post by oldfred on 2018-09-19
Probably best to start new thread then, if you still have issues.

But make sure you have good backups, now, while system is working. I prefer rsync as then I can script it & add a few extra commands in script.

       discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)
Gui tool:
[http://www.teejeetech.in/p/aptik.html](http://www.teejeetech.in/p/aptik.html)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup) 
    
       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

---

### Post by ubfan1 on 2018-09-19
Run Software and Updates, and under the "Updates" tab, turn off any automatic updates.  You can still manually update when you want to.

---

### Post by simone93 on 2018-10-12
Good morning to everyone, i have finished to install ubuntu 16.04.4, now it's safe to upgrade to 16.04.5 ?  Can i show you what package ubuntu suggested me to upgrade and have your approval to do?

---

### Post by oldfred on 2018-10-12
Did you do good backups?
You said you had important work you had to complete? Is that done?
System should automatically upgrade. Your 16.04.4 reached EOL - end of life in Aug 2018.
[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)

---

### Post by simone93 on 2018-10-16
I have to install ubuntu in the ssd, for this reason i didn't do any backup. My important and personal data are in a external hdd.
I did the same installation that i did in the hdd, but with the ssd i've some trouble, the pc after a couple of starts doesn't recognized ubuntu.

What can I do?

---

### Post by oldfred on 2018-10-16
Even if external drive, you want to have backups. Drives to fail, one user just installed to wrong drive overwriting all his data and other things just happen.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

