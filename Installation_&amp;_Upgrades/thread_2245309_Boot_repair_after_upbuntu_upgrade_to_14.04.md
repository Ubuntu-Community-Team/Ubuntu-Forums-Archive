---
title: "Boot repair after upbuntu upgrade to 14.04"
date: 2014-09-22
forum: Installation &amp; Upgrades
---

### Post by suriya3 on 2014-09-22
Hi,
I recently tried to upgrade by system to Ubuntu 14.04.  After the upgrade from the software center, I get a grub terminal with  no options to boot from. I ran a boot repair but using the a live USB  and the following report was generated.

[http://paste.ubuntu.com/8404501/](http://paste.ubuntu.com/8404501/)

Could you please help me out in restoring my system?

Is there a way I could revert the upgrade to the previous os?

---

### Post by oldfred on 2014-09-22
The only way to revert is to restore the full backup you made before you upgraded.

Your grub menu is not showing any kernels and it says it did a purge but then could not download new grub & kernels.
You do show a separate /boot partition. 

Do you have Internet connected? With an Ethernet cable not wireless?
Did you have any ppa? Those almost always cause issues. And they now are not in the sources, but seperate. Your sources look like they all are trusty now. Please review and confirm.
Did you have any proprietary drivers for video or Internet?

---

### Post by suriya3 on 2014-09-22
Unfortunately, I did not create a full backup before upgrade. 

I do have internet through ethernet cable. 
I had an R-package installed through a ppa. I am not sure what trusty-repositories are, but I had added them in the cource of the boot repair, which required me to select a repository to add.
I did not use any proprietary drivers.

---

### Post by oldfred on 2014-09-22
Boot-Repair requires its own ppa, but that is in the live installer and just temporary, not installed to your actual install. 

If R was installed I would think it has a trusty ppa, but issues on upgrades are ppa that do not have the newer version yet and upgrade then cannot finish.

If Boot-Repair is not reinstalling grub & new kernels with its version of chroot, you need to manually chroot. 
I missed before that not only did you have /boot as a separate partition but you have /usr and /tmp & /usr/local as separate partitions. Those are probably the issue with both upgrade & Boot-Repair. Boot-Repair only offers the option to add /boot to a chroot.

Most chroot instructions only show mounting / (root), a few may mention /boot or have a footnote saying if /boot is separate then you must also mount it. But I have not seen any instructions on all the other system partitions, but you probably need to mount them also. Default install of Ubuntu is / (root) and swap. A few have separate /boot but even that is not needed with most desktops. And adding the extra partitions means you must add them in the chroot.

You will have to add your extra partitions in the same fashion as adding /boot in chroot.

 To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
[http://en.wikipedia.org/wiki/Chroot](http://en.wikipedia.org/wiki/Chroot)
Kernel panic at boot: not syncing. No init found - chroot to resolve
[http://ubuntuforums.org/showthread.php?t=2228437](http://ubuntuforums.org/showthread.php?t=2228437)

Once chrooted.
      
 #Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

 # uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a

---

### Post by suriya3 on 2014-09-24
Thank you oldfred.

I followed the instructions in  [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) and mounted the following partitions: / (sda3), /boot (sda1), /tmp (sda7), /usr (sda5), /usr/local (sda6)

sudo mkdir /mnt/temp /mnt/temp/boot 
sudo mount /dev/sda3 /mnt/temp
sudo mount /dev/sda1 /mnt/temp/boot
sudo mount /dev/sda7 /mnt/temp/tmp
sudo mount /dev/sda5 /mnt/temp/usr
sudo mount /dev/sda6 /mnt/temp/usr/local

for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf

Finally when I try to chroot, I get the following error:
sudo chroot /mnt/temp
"chroot: failed to run command ‘/bin/bash’: No such file or directory"

I verified that I am able to run /mnt/temp/bin/bash from the terminal but I am not able to chroot /mnt/temp directory.

Can I execute the rest of the commands using sudo? If not, could you please suggest what should be going wrong with chroot?


The output of 'df -H:
Filesystem      Size  Used Avail Use% Mounted on
/cow            4.2G   63M  4.2G   2% /
/dev            4.2G  4.1k  4.2G   1% /mnt/temp/dev
tmpfs           834M  1.4M  832M   1% /run
/dev/sdb1        16G  1.1G   15G   7% /cdrom
/dev/loop0      985M  985M     0 100% /rofs
none            4.1k     0  4.1k   0% /sys/fs/cgroup
tmpfs           4.2G  1.1M  4.2G   1% /tmp
none            5.3M     0  5.3M   0% /run/lock
none            4.2G   78k  4.2G   1% /run/shm
none            105M   62k  105M   1% /run/user
/dev/sr0        737M  737M     0 100% /media/ubuntu/UDF Volume
/dev/sda3       7.8G  494M  6.9G   7% /mnt/temp
/dev/sda1        92M   24M   63M  28% /mnt/temp/boot
/dev/sda7        15G  138M   15G   1% /mnt/temp/tmp
/dev/sda5        20G  6.2G   13G  34% /mnt/temp/usr
/dev/sda6       9.8G  7.0G  2.3G  76% /mnt/temp/usr/local


Thanks
Suriya

---

### Post by oldfred on 2014-09-24
This command only mount the items in the list:
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done

But your df command does look like everything is mounted.

I do not know details of chroot, but I think the bash you run to execute the chroot is from your live installer. Only after you chroot will root be in your /mnt/temp. So you need bash in /bin/bash to run the chroot.

Are you using Ubuntu live installer? Other versions of Linux may have bash in a different folder?

---

### Post by suriya3 on 2014-09-24
I had separately mounted the rest of the files (see first set of commands in previous post. 
I am using the liveUSB (Ubuntu 14.04) installer and I have checked that both /bin/bash and /mnt/temp/bin/bash commans are present.

Regards
Suriya

---

### Post by oldfred on 2014-09-24
I do not see why you would get an error on the sudo chroot command?

Perhaps the reiserfs file system on /tmp? Not sure you have to mount that for chroot. And live installer probably does not have the driver for reiserfs.

---

