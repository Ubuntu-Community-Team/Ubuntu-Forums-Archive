---
title: "What partition format should i use?"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by wannaBeHacker on 2006-12-22
Hi i installed ubuntu using to partitions a 9.6GiB  *ext3 and a swap 300MiB partition using ext3

but now that its installed i dont see the harddrive partitions, can someone please tell me what  formats i should of used and what each one is for. PLEASE!

---

### Post by jml on 2006-12-22
With the two partitions you created on install, you will only see one partition.  Swap is a part of the hard drive set aside to store data temporarily.  For example, if a program you are running needs more RAM than you have available on your computer, the computer temporarily stores the data in the swap file.  The reason you can't see it is that in normal oporation you don't need to see it.  The contents change minute by minute.  When you click on and open the icon labeled file system, you are actually seeing the partition formatted with ext3.  If during install, you had opted for more than one ext3 partition then you would have seen two separate icons.

Joe

---

### Post by ericzb on 2006-12-22
well, wannaBeHacker,ext3 is basically a good choice for / ,may be i did not get you, didi u mean u use ext3 for swap, well, i never tried that. normally, linux-swap is the format for swap partition.

if you want to see you partition, try this line
 
    df -h

you can see your partition and partition usage this way

hope helps

---

### Post by wannaBeHacker on 2006-12-22
its not the swap drive i cant see only, its my main root directory i cant see either...

heres my set up

Im using a 37Gb harddrive

20Gb i have used as my first partition in NTF format for my windows XP

which left me with 10GB

upon installing Ubumtu:

I took the following actions.

when i made my root directory i made it 9.7gb/ext3/ "/"

my swap directory took the remaining space left 300mb/ext3/ "swap"



after it was installed, the only icon on the desktop is the partition for my windows.

I think maybe when i made the root directory for ubunto, i should of used "/dev/hda2" instead of just "/"? correct me if im wrong, or does the installation automatically convert  "/" to "/dev/hda2"

---

### Post by wpshooter on 2006-12-22
Your partitions should be setup like this:

/         = root partition    - filesystem type ext3
/home = home partition  - filesystem type ext3
/swap  = swap partition   - filesystem type linux swap

Yes, I think the convertion you refer to will be done automatically.

I think you are looking for something that should not really be there on a Ubuntu/Linux desktop O/S.  Please describe to us in a bit more detail what it is that you are looking for that you are not seeing.

Thanks.

---

### Post by wannaBeHacker on 2006-12-22
I'm looking for a harddrive icon for my root directory, the 9.7Gb partition, i only see the 20gb windows partition

---

### Post by wannaBeHacker on 2006-12-22
or is there no icon for the root directory? if so how can i seewhats in there and how much space i have left...?:confused:

---

### Post by pebo on 2006-12-22
If you are using Gnome try System -> Administration -> System Monitor.
This should show your mounted partitions and usage.
In KDE use Kwikdisk.
I don't think there's anything wrong with your partition setup.
hth

---

### Post by liveder on 2006-12-22
I could just say: go to the menu Y, click in program X, and you have your disk. But since it seems to me that you are not a Linux user, but want to be, I think that it's more instructive to explain you some things first. (I have some time to write :) )


Your question is basically this: Where in the hell is the C: or D: drive, with all its directories (folders) and files?

Well, Linux does not show drives/directories in the same way as windows does.



First a little about paritions.

Suppose you have six partitions in your first IDE drive (hda), three primary and three extended. Well, this is not absolutely correct. A disk can have at most four primary partitions or three primary and one extended partition. When you create a partition in the extended space, you actually create a logical drive. Your partition scheme is thus

hda1 -> primary
hda2 -> primary
hda3 -> primary
hda4 -> extended partition
hda5 -> first logical drive in the extended partition
hda6 -> second logical drive in the extended partition

(From now on, let us call partitions to the logical drives in the extended partition).
Of all the partitions you have, you can only see hda1, hda2, hda3, hda5 and hda6.


Now suppose you have windows installed in the first partition (hda1), and Linux in the other ones. With the exception of swap partition, in Linux all the partitions are mounted (assigned) to a directory, called the root directory (/). In this way you don't have a bunch of disks, but only a structure of directories, some of which may point to disk partitions. You can also do this in windows (see more in [http://en.wikipedia.org/wiki/Root_directory)](http://en.wikipedia.org/wiki/Root_directory)).


Now lets suppose you have hda5 assigned to the root directory and hda3 to the swap space. In Linux you will not see hda3, since you aren't expected to access this space.
Now we have

hda1 -> windows partition
hda3 -> swap partition
hda5 -> /

Why haven't I used hda2 for the root directory? And why is the swap partition assigned to hda3? Because you must have a /boot directory to hold your kernel in order to be able to boot into Linux, and I like to place the boot directory in the first partition used by Linux, the swap space in the second one, and the root directory in the third. It's just a matter of taste (I think).

So, we have

hda1 -> windows partition
hda2 -> /boot
hda3 -> swap partition
hda5 -> /

Now we have a spare partition. What should we do with it?
In Linux you also have a /home directory, which is the home of all user accounts, and were users can place all their files.
Both in windows and Linux , it's a good practice to have all your files in a separate partition. In this way, if something goes terribly wrong with your system, your files are all there (hopefully). In the worst case, you have only to format the other partitions and reinstall your system. Well, the worst case is really when your home partition get weird.

Our partition scheme is then

hda1 -> windows partition
hda2 -> /boot
hda3 -> swap partition
hda5 -> /
hda6 -> /home


Personally I also like to have a separate partition for the /usr (see [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)).

Your /boot partition doesn't have to be bigger then 200 MB, which is enough to hold some kernels. If you don't know where to find your disks in Linux, a separate /boot with 100 MB is twice what you need. Beleave me that you will not compile a kernel in the next month. However, if you hinted to do so in the future, and choose to have a separate partition for /boot, then use 200 MB. 

The size of the remaining partitions (/ included) depends on your needs and partition scheme. For instance, If I have enough disk space, I use a separate partition for /, /usr, /var, /opt, /tmp and /home, if not, I may use one partition for / (which will include /usr, /opt, /var, /tmp) and  one for /home.


Concerning the file system used to format partitions, I prefer reiserfs to ext3 (for all my partitions), because it's much more faster with small files.



Now it's time to tell you were your disk is. If you are using Ubuntu, probably you are using Gnome, so go to Places -> Home Folder and you will see /home/your_folder, or go to Places -> Computer and you will see your other drives (HD, CDR, etc.) and your file system (at least what Gnome is configured to show you, which I think is /home and /media).
If you want to see the entire file system, go to Applications -> Accessories -> Terminal. In the Terminal, type

ls -lah

to list (ls) your file system, in long list mode (-l), showing all the files (-a) and with size displayed in a human readable format (-h). Then type

cd /usr

to change directory (cd) to /usr.


To see your space left, type in the Terminal

df -H

This will display the file system (df), showing used and available space in a human readable format (-H)


Hope this helps.

---

### Post by liveder on 2006-12-22
Just a correction.

I said I use reiserfs for all my partitions. This is not really true, since swap has its own filesystem.

---

### Post by wannaBeHacker on 2006-12-23
WOW! Thank you so much liveder you really cleared things up for me... i could use a friend like you :-k 

Also im about to uninstall windows forever! and never look back! :D

---

