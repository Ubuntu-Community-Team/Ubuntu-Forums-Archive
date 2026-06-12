---
title: "HOWTO Encrypt an Ubuntu 18.04 LTS Installation with TWO Drives (e.g. SSD/HDD)"
date: 2018-05-11
forum: Installation &amp; Upgrades
---

### Post by frogotronic on 2018-05-11
HOWTO Encrypt an Ubuntu 18.04 LTS Installation with TWO Drives (e.g. SSD/HDD):

	This is a guide to FULL DISK ENCRYPTION of an Ubuntu 18.04 LTS install.  Not to be confused with the encryption of just the </home> directory.  These instructions are for the Linux operating systems (OS) known as &#8220;Ubuntu 18.04 LTS&#8221;, which is freely available as a download of about 2 GB.

	This guide assumes that you are familiar with Ubuntu (Linux) and can install the OS from a USB key, or at least understand how to do this procedure &#8211; if you can&#8217;t, find someone who can and the both of you go through it.  This guide also assumes that you have backed up ALL your data prior to beginning this procedure as you will destroy all DATA on ALL drives during this procedure.  YOU HAVE BEEN WARNED!

	This guide is largely a meld of the two procedures from here (David Yates&#8217; blog post) ([https://*davidyat.es/2015/04/03/encrypting-a-second-hard-drive-on-ubuntu-14-10-post-install/](https://*davidyat.es/2015/04/03/encrypting-a-second-hard-drive-on-ubuntu-14-10-post-install/)) and this Ask Ubuntu post ([https://askubuntu.com/questions/21321/move-home-folder-to-second-drive](https://askubuntu.com/questions/21321/move-home-folder-to-second-drive)).

	First things first, why do we wish to do this?  Because if you own a laptop, or other sensitive data on a computer and it gets stolen or lost, it is necessary to be able to protect the data.  You may be legally responsible to have protected the data.  Secondly, many (most) systems now come with a small SSD (fast) for the OS and larger HDD (slow) for the data.  Thirdly, encrypting just the </home> directory is a bad idea as it exposes you to the potential of </home> being hacked, AND slows down the system to a large degree.  FDE requires less overhead and therefore has minimal impact on the performance of the system.

PART I: Install Ubuntu 18.04 LTS on the primary drive (usually the SSD)

	Install Ubuntu 18.04 LTS onto your smaller (usually the SSD) and check (i) erase the disk, (ii) encrypt the installation, and (iii) LVM management. 

	This will result in an encrypted SSD, but will not touch the second (usually HDD) drive.  To prepare this for your home, you should format it using the GUI tool called &#8220;gParted&#8221;.

	sudo apt install gparted

	Open gParted and navigate to your second HDD partition and delete any existing partitions, then create a new PRIMARY PARTITION using the EXT4 file system. You could also label it, but that&#8217;s not necessary.  One gParted is finished, close gParted and now your ready to install the LUKS container on the second drive and then format it.  In the following commands, replace sd?X with the name of your drive, for example <sda1>.

	sudo cryptsetup -y -v luksFormat /dev/sd?X

	Then you&#8217;ll need to decrypt the new partition so that you can format it with ext4, the modern Linux file system preferred by Ubuntu.

	sudo cryptsetup luksOpen /dev/sd?X sd?X_crypt
	sudo mkfs.ext4 /dev/mapper/sd?X_crypt

	If you want to use your second HDD as a regular, frequently accessed hard drive, there&#8217;s a way to automatically mount and decrypt your second drive on startup/login, when your primary hard drive is decrypted.  First you&#8217;ll need to create a keyfile, which acts as a password that you don&#8217;t have to type in every time you start up (like your primary hard drive encryption password).

	sudo dd if=/dev/urandom of=/root/.keyfile bs=1024 count=4
	sudo chmod 0400 /root/.keyfile
	sudo cryptsetup luksAddKey /dev/sd?X /root/.keyfile

	Once the keyfile has been created, add the following lines to /etc/crypttab using nano

	sudo nano /etc/crypttab

	sd?X_crypt UUID=<device UUID> /root/.keyfile luks,discard

	To get your parition&#8217;s UUID, use this command (you need to use sudo it so that all of your partitions show up):

	sudo blkid

	The value you want is the UUID of /dev/sd?X, not dev/mapper/sd?X_crypt. Also make sure to copy the UUID, not the PARTUUID.

	Okay, at this point you should be able to login to your Ubuntu install (entering your encryption password) and it should decrypt both your primary and secondary drives.  At this point, you should check to see if this happens otherwise stop, and solve the issue(s).  Reboot and check to see if this in fact is the case.  If the drive is automatically decrypted, when you choose &#8220;Other Locations&#8221; the second drive should show up in the list and have a lock icon on it, but the icon should be unlocked.

	If the second drive automatically decrypts (as it should), then move on to designating the second drive as the the default location of your </home> folder (with the larger amount of space).

Part II: Move your </home> partition to your larger, secondary drive, usually a HDD

	Temporarily mount the new partition:

	sudo mkdir /mnt/tmp
	sudo mount /dev/mapper/sd?X_crypt /mnt/tmp

	assuming /sd?X is the new partition for HOME

	Now we copy you </home> folder to the new </home> location from the primary drive to the secondary drive.

	sudo rsync -avx /home/ /mnt/tmp

	We then may mount the new partition as HOME with 

	sudo mount /dev/mapper/sd?X_crypt /home

	to make sure all data are present.

	Make HOME permanent, we need edit the fstab entry to automatically mount the </home>.

	sudo nano /etc/fstab

	and add the following line at the end:

	/dev/mapper/sd?X_crypt /home ext4 defaults 0 2

	Reboot; after a reboot, your </home> should reside on the new drive and have plenty of space.

---

