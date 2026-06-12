---
title: "Some partition´s questions when i have to install Ubuntu"
date: 2016-10-14
forum: Installation &amp; Upgrades
---

### Post by cristoamh on 2016-10-14
Hello and first of all, i´m sorry about my english beacuse i´m not a native english speaker, but i will try my best.

Well, the main question is because i want to install ubuntu 16.10 (I´ve never have touched Ubuntu before until I´ve tried this week with the trial), right now i have two hard drive, one of them is a ssd drive of 120 Gigas where is installed Windows 10. it takes more or less between 70-80 gigas, so i have 40 gigas of free space. Also i have another hard drive, and HDD and this time this have 2 Terabytes of capacity. Inside of this HDD i have my documents (like pictures, flms, music...) and also is where i install the programs, so i let the SSD just for the SO.

My question is: ¿With only 30 Gigas in SSD is enough to install Ubuntu?¿And if the answer is yes, Windows will go slowler because there are less space?

and the another question is, once Ubuntu have been installed  in case that with 30 gigas will be enough. ¿ Can i share the HDD of 2 TB between Windows and Ubuntu?¿Or i have to do a new partition in the HDD, for example of 500 Gigas, and do something else to save the documents and programs i will use in ubuntu?

Thanks, and sorry if i seem so noob, because i am.

---

### Post by yancek on 2016-10-14
The 40GB of 'free space' must  be that, free or unallocated and outside any windows partition.

30GB should be more than enough for an Ubuntu install, a base install I think being a little over 8GB.  You just need to keep an eye on it if you are installing a lot of software.
I don't see why windows would be slower because you have another system on the drive.
Any programs/software you install will be on the 30GB partition.  Data such as documents, pictures, movies, etc. can be on the external drive formatted vfat or ntfs.  A default windows install is not capable of reading or writing to a Linux filesystem but Linux installs are capable of reading/writing to windows filesystems.

16.10 is a short term release (9 months support) and was just released yesterday so you might be better off using 16.04, your choice.

---

### Post by cristoamh on 2016-10-14
Thank you yancek for your quickly answer.

So if i understood you mean i have to make a partition on the SSD with the 30 GB to install windows, but the second part i dont  understand, i mean, if for example i want to save some documents on the HDD of 2TB, i could without problems? or i have to make another partition for documents i save on linux? ( I` was reading a bit more and i think is something like another partition as /home, i mean a separate partition but i´m not sure and don´t know how to do it)

EDIT: And I want to install 16.10 because trying to use 16.04 i didnt have Ethernet and wifi and was impossible to me find some fix to this, and with 16.10 everything is alright.

---

### Post by oldfred on 2016-10-14
Is system UEFI or BIOS? Or are drives gpt partitioned or MBR(msdos) partitioned?
With Windows you do have to maintain lots of extra space for NTFS to work well. If NTFS gets to 10% free it will get a lot slower. And defrag may then take forever as it has no working room Most suggest 30% free.
Can you move more data to HDD?

Ubuntu has a good NTFS driver that will read & write NTFS. But best not to write into Windows main drive or c: drive. If necessarily mount as read/only. And use a shared NTFS data partition for any data you may want in both systems.
The /home must be a Linux formatted partition to support ownership & permissions at the file level. NTFS does not have that capability.

I normally use 25GB for / (root), but have all data in a data partition on HDD. I used to also have a shared NTFS back when I still used XP, but both of my main working systems are Ubuntu (several versions) only. Some on SSD & some on HDD.

You can partition during install using Something Else, or you can partition in advance with gparted, but still have to use Something Else to choose which partition is which.

       Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
[/URL]
 UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 

[URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

