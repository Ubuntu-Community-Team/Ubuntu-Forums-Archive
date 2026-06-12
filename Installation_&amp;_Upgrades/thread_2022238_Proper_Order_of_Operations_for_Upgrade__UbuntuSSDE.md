---
title: "Proper Order of Operations for Upgrade:  Ubuntu/SSD/Encryption?"
date: 2012-07-10
forum: Installation &amp; Upgrades
---

### Post by DBSLLC on 2012-07-10
Hey guys and gals, I have a Netbook running Ubuntu 11.x but the HDD is failing so I'm going to replace it with a new SSD.  In the near future I would also like to upgrade to Ubuntu 12.04 and encrypt the drive/partition since I have lots of client data on it.

What's the suggested order of operations to go from 11.x (unencrypted) with a bad drive to 12.x with a new encrypted SSD all the while preserving my user settings/preferences (if at all possible)?  Would it possible to encrypt only part of the SSD so I could use ~20GB or so to play around with hidden/encrypted partitions after my system is migrated/rebuilt?
  
Thanks!
Phil

---

### Post by DBSLLC on 2012-07-13
Well guys, I decided to just take a stab at this thing so I went ahead and installed Ubuntu 12.x on the new SSD using the alternate method so the drive and swap space are now both encrypted.

Unfortunately when I booted into 12.x I came to find out the /home directory in my old 11.x system is encrypted so I can't move any files over from it (and no passwords I can think of actually work).  If I boot into 11.x I can't mount the 12.x drives because I get the following error:

One or more block devices are holding /dev/mapper/volume--1-SSD1--Logical1

Even if I do managed to get one OS to see the "other" drive, how close will moving my /home directory and installing all the same programs again get me?  Is there a better way to do a forklift Hard Drive upgrade?  If found some methods of cloning a drive but I'm concerned that 1) I won't be able to clone into an encrypted partition and 2) I still have an NTFS partition on the old HDD so if I go through with the cloning process I think Ubuntu will barf if I ever have both instances of the same drive attached - problem is I have an NTFS partition on the old drive that I need to access from time to time.

Any suggestions would be very helpful.  I'd love to finish the transition to SSD this weekend!

Thanks,
Phil

PS Sorry for the self-bump.

---

### Post by DBSLLC on 2012-07-15
Hey guys,

I'm having boot issues as well and they sound like something boot-repair could fix, especially since Yann added support for encrypted drives.

I'm migrating from a HDD to a SSD (as explained [here]("http://ubuntuforums.org/showthread.php?t=2022238")) but I wanted the new drive to be encrypted so I used a Live USB to create two encrypted partitions on the SSD - 102GB for primary and 6GB for swap.  I then copied the primary partition over from the old drive to the new, and did some tuning based on various articles I found online.

Obviously when I booted nothing happened since two out of two drives are encrypted so I created a third unencrypted partition of just 10MB to be the new boot partition; however, I'm having difficulty using boot-repair to configure a valid boot partition on /dev/sda3.  Can you offer any tips to getting the proper MBR/GRUB configuration into the boot partition so it can mount the encrypted drives?

Thanks in advance,
Phil

---

### Post by DBSLLC on 2012-07-15
I now have my Ubuntu 11.x instance cloned over to the encrypted partition on the SSD.  I've also created an encrypted swap partition and small boot partition as well.  Unfortunately I can't figure out how to use boot-repair to build an MBR/GRUB combo in the boot partition that will mount my encrypted drives and proceed with the init.

Any ideas?

Thanks,
Phil

---

### Post by oldfred on 2012-07-16
Moved to your own thread as the only common issue was boot issues. Old thread did not have encryption.
Update
Did not realize you already had a thread. Combined.

Old thread for ref.
[http://ubuntuforums.org/showthread.php?t=2020544](http://ubuntuforums.org/showthread.php?t=2020544)

You cannot just create a partition and say it is boot. You have to move all the files from the boot folder in / (root) and then reconfigure grub & fstab. I think Boot-Repair might reinstall grub2's boot loader if you are booted into the install.

I do not know about encryption so cannot help on that.

---

### Post by DBSLLC on 2012-07-16
Me neither - pretty lost at this point.  Thanks for the thread movement but is there anywhere else I can look for info on my issue?  I feel like this would be a fairly common problem for people migrating to encrypted partitions...

Thanks,
Phil

---

### Post by oldfred on 2012-07-16
The only links I have on encryption:

[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)

How to: Resize an Encrypted Partition (LUKS)
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)

---

