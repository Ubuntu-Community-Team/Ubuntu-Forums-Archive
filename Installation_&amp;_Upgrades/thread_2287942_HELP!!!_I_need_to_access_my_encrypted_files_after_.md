---
title: "HELP!!! I need to access my encrypted files after a failed upgrade."
date: 2015-07-23
forum: Installation &amp; Upgrades
---

### Post by roymastboom on 2015-07-23
Backstory:
I had a lot of problems with 14.04 (updates wouldn't work, logging in would always start with an error message or three, Ubuntu loading screen would also present an error underneath of unable to mount yadayada drive: s to skip or m for manual mounting)
Then I decided to upgrade to 15.04. I started with 14.10. The upgrade went just fine, until restart. Then it would boot like normal (error message about mounting) and it would then give me a black screen, where white text loaded onto (like "preparing uuid" all ending with "[ok]").
I managed to get into a root shell and to log in once and was able to copy my home directory to an external hard drive. But there was not enough space aparently. Then I decided to do that again but only select the important folders (like 20 gb instead of 300) but was unable to login. When I would use the command "sudo login" and then logged in I got an error message and I was unable to write to the directory my hard drive was mounted to. I then used boot repair, and it didn't change anything. The I selected the option to restore the "MBR" and now i get the error message of "No Operating System" So I don't think I can boot into shell anymore.
Now:
Now I am trying to retrieve my data again via live Usb: but it is encrypted and I get permission denied and not even a readme file when I oped my home -> username directory.
I tried to follow How-to-geek's instructions, but it doesn't work for me since when I run the command "sudo ecryptfs-recover-private" I only get "Info: Searching for encrypted private directories (this might take a while..." and after about a half hour still nothing.
If I install a version of ubuntu, will I be able to retrieve the data? I have hours of filming work that is very valuable to me saved in the home directory.

---

### Post by TheFu on 2015-07-23
So - don't have any help except to learn from this experience.
a) backup, backup backup - ESPECIALLY WHEN ENCRYPTION IS INVOLVED!!@!!!!@#!@#!
b) Never try to "upgrade" a system showing any flaws. It will NOT make it better. Fix any issues first. Also, **always make a backup before beginning any upgrade processes.**
c) Test the restore of any backups.  Honestly, 90% of the point to backups is the restore, right?

Ok - if you can boot off a live CD/USB and post the output from **lsblk**, we might be able to help, a little.  There are different types of encryption. We don't know which type you have yet.  Also the output from **sudo parted -l** would help too.

For "critical data" - nothing replaces good, know-you-can-restore, backups. NOTHING. Not RAID, not hope (I hope it will work), not prayers (God help me!).

Lastly - whenever there are errors or issues, please check the log files in /var/log. Using a search tool is usually desired - like grep.

---

### Post by roymastboom on 2015-07-23
ubuntu@ubuntu:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1   8:1    0 461.9G  0 part /media/ubuntu/6079b714-daef-4531-a814-c75210faf
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0   3.9G  0 part [SWAP]
sdb      8:16   1   7.5G  0 disk 
&#9492;&#9472;sdb1   8:17   1   7.5G  0 part /cdrom
sr0     11:0    1  1024M  0 rom  
loop0    7:0    0   953M  1 loop /rofs

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD5000BPVT-7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  496GB  496GB   primary   ext4            boot
 2      496GB   500GB  4183MB  extended
 5      496GB   500GB  4183MB  logical   linux-swap(v1)


Model:  USB DISK 2.0 (scsi)
Disk /dev/sdb: 8015MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8015MB  8014MB  primary  fat32        boot, lba

I encrypted it as an option when I first installed ubuntu 14.04 btw

---

### Post by TheFu on 2015-07-23
For your reference - it appears you did NOT use whole disk encryption and only used "HOME directory" encryption.  That means when you login (either on the console or through an ssh network connection), the home directory for the account gets decrypted - not the entire /home/ directory structure. It is per-user-id only.  If joe and jane are userids, when joe logs in, only his directory gets decrypted and linked.  Jane's HOME would not. The idea is cool, I'll admit - but it makes automatic backups next to impossible, since users must be logged into the system for these encrypted files to be accessible in a way that helps modern backup tools be efficient.

HOME directory encryption is kinda slow (20% hit), so after a test of a few weeks, I stopped and switch to whole drive encryption, which doesn't have much overhead at all (3-6%). [https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome) might help. [https://www.phoronix.com/scan.php?pa](https://www.phoronix.com/scan.php?pa)

[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Using_in_conjunction_with_Auto-login](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Using_in_conjunction_with_Auto-login) might help. If you understand the setup process, the recovery process should be easier. That's the theory.

Hope those links help.  The HowToGeek isn't a bad place to go for stuff like this, so that was not a bad idea. Sometimes they make stuff like this really easy. Then try AskUbuntu and help.ubuntu.com - pay careful attention to the specific releases involved. Some things change every release.  For non-business stuff, the ubuntuforums seems find too - but because linux is so very flexible, we have to ask questions to get the lay-of-the-land so our advice fits.  A 1 line answer usually is full of 100+ assumptions, which may not be true. ;)

BTW (unrelated) - having 1 huge partition for everything is not a best practice on drives over 100G in size. A case can be made for smaller disks to be split up too - at least for / and /home and swap.  I like to keep large files outside /home as well. By having different partitions, managing backups becomes easier.

---

### Post by roymastboom on 2015-07-23
since i have no os anymore aparently, should i then install ubuntu 15.04 and work from there?
how do i log in then?
I will read the links given and if my questions change ill update this

So yeah,
Looked through the articles, my question still stands though.
Do I now need to install a new ubuntu OS? Do I do that on a partition of unused disk space, and then mount the other partition? What do I do from there then?

---

### Post by oldfred on 2015-07-23
The entire purpose of encryption to prevent anyone from getting to data, if pass phrase does not work.
Or if data is at all valuable you have good backups of that data. And anytime you make major changes to a system, you want to make sure backups are current.

 fsck on encrypted LUKS 
[http://serverfault.com/questions/375090/using-fsck-to-check-and-repair-luks-encrypted-disk](http://serverfault.com/questions/375090/using-fsck-to-check-and-repair-luks-encrypted-disk)

---

### Post by oldos2er on 2015-07-23
Threads merged. Please don't create duplicate threads; it's confusing and it dilutes the community's ability to help.

---

### Post by roymastboom on 2015-07-24
I still want to know whether i should install ubuntu on another partition, and if i do so what to do from there

please help, you have been the most useful so far... should i install ubuntu on unused hdd space? what should i do from there?

TheFu,
please answer my question and dont leave me hanging
pretty please???

TheFu,
Please reply
I need your help
please answer my last question: Should I install Ubuntu on remaining disk space? What do I do from there on?

---

### Post by roymastboom on 2015-07-24
TheFu,
I see you are active, please don't leave me hanging here.
This is very important to me, and you have been the most helpful thus far.

---

