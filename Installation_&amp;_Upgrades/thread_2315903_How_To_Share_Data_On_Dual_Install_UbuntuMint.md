---
title: "How To Share Data On Dual Install Ubuntu/Mint"
date: 2016-03-03
forum: Installation &amp; Upgrades
---

### Post by david498 on 2016-03-03
I have successfully (?) installed Ubuntu 15.10 alongside Mint 17.3 and am able to boot into either system.  However although I can see the Mint partition as Volume nngb in Ubuntu,  I am not able to access the Home dir  - fdisk -l gives me fdisk: cannot open /dev/sda: Permission denied.  If I boot into Mint I am able to see and access the Ubuntu Volume.  I have a desktop running Skylake i5 which Mint doesn't handle too well as yet, so I wish to use Ubuntu 15.10 in the meantime, and need to be able to access my data dirs on Mint, without having to resort to USB tsfrs.  Is this possible?

---

### Post by oldfred on 2016-03-03
I have multiple installs of Ubuntu and create a shared ext4 /mnt/data partition and link all the typical data folders like Music, Documents, Downloads, etc into /home. Then all data is shared.

Another thread on data:
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)

       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by Dennis N on 2016-03-03
> I am not able to access the Home dir - fdisk -l gives me fdisk: cannot open /dev/sda: Permission denied.

Are you using sudo with the fdisk command? If I run it without sudo, I get exactly the same output:

```
dmn@Roxanne:~$ fdisk -l
fdisk: cannot open /dev/sda: Permission denied
fdisk: cannot open /dev/sdb: Permission denied

```

On this computer, I have Xubuntu 15.10 with Mint 17.3 on another partition and I am able to mount and access the Mint file system from the Xubuntu file manager (open the Mint from side pane) - my user name is the same with same access and permissions. Yes, it should work.

---

### Post by david498 on 2016-03-03
Dennis, yes I had forgotten to run fdisk as sudo - here is the result: 
Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 377587801 377585754   180G 83 Linux
/dev/sda2       377589758 625139711 247549954   118G  5 Extended
/dev/sda5       612741120 625139711  12398592   5.9G 82 Linux swap / Solaris
/dev/sda6       377589760 596215807 218626048 104.3G 83 Linux
/dev/sda7       596217856 612734975  16517120   7.9G 82 Linux swap / Solaris 

I can see the 193GB volume containing Mint, but when I open Home/roodog46 I get the error msg: This link cannot be used because its target &#8220;/usr/share/ecryptfs-utils/ecryptfs-mount-private.txt&#8221; doesn't exist.

---

### Post by oldfred on 2016-03-04
You did not say partition or /home was encrypted. Is it full drive LVM or /home encryption?
You have to use encryption tools and know passphase to mount it.

---

### Post by david498 on 2016-03-04
oldFred, I have not used encryption.  I have wiped the disk and started again, using your suggestion re creating a Data partition and symlinks.  My first effort seemed OK and was working, but when I tried to reboot there was a problem, seemingly caused by the Data partition, as I recognised the UUID amongst the system report.  Anyway I have reinstalled ubuntu and redone the symlinks and fstab.  I have left Mint off at this stage.  Maybe I'll reinstall later, when I have ubuntu working properly.  Thanks for all help.

---

### Post by oldfred on 2016-03-05
It sounds like your entry in fstab may not have been correct.
Always run this after editing fstab to verify it is ok, if it just comes back with no error then ok.
sudo mount -a

---

### Post by david498 on 2016-03-06
Yes, I had a typo in my fstab entry.  I'm sure that I ran sudo mount -a after saving fstab and nothing happened.  I have learnt lots more about using cli and install/boot issues since I started this adventure.  When I first saw the systemctr msg I din't realise I was able to cd to the /etc/fstab and sort things out.  Would have saved me a reinstall or two, lol.  Anyway, once I had corrected the fstab entry I was able to boot and carry on.  Once I had ubuntu up and running, I thought I may as well get Mint done as well, so I rebooted from a fresh iso and voila! it worked perfectly, no sign of the software rendering issues I had been plagued with.  I see now that it was probably because I had updated Mint from 17.2 to 17.3 using the Update Mgr, instead of reinstalling.  Anyway, I am now a happy camper and have both systems sharing /Data.

---

