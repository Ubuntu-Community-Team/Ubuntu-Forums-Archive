---
title: "Reinstalling the OS (by reformatting / ) with encrypted home partition"
date: 2014-02-01
forum: Installation &amp; Upgrades
---

### Post by gianfranco2 on 2014-02-01
Hello everyone, I wanted to upgrade my system to Xubuntu 13.10 (I'm currently using 13.04, which is no longer supported); however, there might me a problem - my home directory is encrypted (this is a laptop and encryption in my case is a necessity) and I am afraid that after reformatting the *root* directory it might not be mounted or recognized by the OS and I will not be able to access my files again (almost a third of them has not been backed-up). The home directory is on a separate partion (*/dev/sda5*) (this was done on purpose, in the event I needed to reinstall the OS without losing the contents of the home directory):

[ATTACH=CONFIG]250015[/ATTACH]

The laptop has a UEFI motherboard but the drive, as you can see, has an MBR partition table (this was done to make the installation of Xubuntu easier, which however took me several attempts to install properly and be recognized during boot even after MBR was successfully created with Gparted). 

So, how do I format the root directory and reinstall the OS, at the same making sure the encrypted home (I have its passphrase) is recognized by the new system and I am able to access it? 

Also, I have another concern: you might have noticed that there is a 1.02 MB of unallocated space at the end of the drive; when formatting and trying to merge two adjacent partitions with Gparted on another laptop with Windows, I noticed that sometimes, a similar thing would occur between the two, making it seemingly impossible to move and merge them. 
Is there a possiblity that such a thing might occur here, making the installation of the new OS on / impossible or blocking /home from being used no matter what? And how to prevent that?

---

### Post by TheFu on 2014-02-02
Make of backup of any data you don't want to loose. Be certain to use a backup tool that maintains user, group and permissions.
This is required before any update, upgrade or when touching partitions anyway, to protect against data loss.

Backup, backup, backup (10% of the effort) and restore (other 90%)!

---

### Post by oldfred on 2014-02-02
Some info on backing up. I do not use encryption.
 Includes chroot:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

Do not worry about 1MB extra on drive. With the new rounding for 4K drives and SSDs partitions now may show larger gaps. Before you had the spaces between partitions but they were not quite large enough to show.

---

### Post by gianfranco2 on 2014-02-03
Well, thank you for suggesting me to back up, but this is why I formatted the drive like this: in case I did not have access to an external HDD, and I needed to reinstall the system wiping the partition clean while keeping my personal files and retaining some privacy, I placed / and /home on two different partitions.
@oldfred, correct me if I'm wrong, but the first link you provide simply shows how to mount and enter the encrypted folder; I am also aware of the excellent howtogeek article - in fact, when I could no longer access my encrypted home on Ubuntu 12.04 a year ago, it helped me recover my data. But I do not need to recover the data - to restate what I am trying to do: I need to format or to erase root - which was placed on a different partition to make reinstalls easy and avoid losing personal data - to make sure it can be used for reinstalling or installing a different Linux distro; once reinstalled, I want the system to recognize the old home partition, be able to mount it, log into it, assign a new passphrase to the encrypted home folder for security reasons, make the OS memorize the passphrase (and sort of "tie" or "link" itself to it, assuming, of course, that's necessary) and then to be able to automatically mount it and log into it each time my user password is entered (when prompted for it after I power on the computer)...in other words, just as it normally happens when you log in. So, I wonder, does the first link you provide allow me to do that?  
(I tried to reinstall the operating system (Xubuntu 13.04) on a different laptop but with a similar partitioning scheme (although it had two primary Windows partitions - sda1 and sda2) and, despite choosing /home as my home folder (I also did the same thing with the swap partition, not hoping to recover that one, anyway), I could not get past the login screen - the screen simply went blank for a second and then went back to the password prompt. So, that option apparently does not work.)

---

### Post by TheFu on 2014-02-03
I guess we were not clear.
a) we don't know (at least I don't know) if reinstalling the OS will or will not wipe the data OR if it will recognize and make any previously encrypted data accessible. I don't know.
b) I **do know** that if you backup the data from the encrypted areas prior to doing any OS update, then install the new OS, then restore that same data to the new partitions, it will be available. Use or do not use encryption as you like during the new OS install.

Sorry we weren't clear.
Sorry we don't know the answer.

There is a known method to get the final result desired, just not in the way hoped with 100% pre-knowledge of the outcome.

backup - OS re-install - restore.

---

