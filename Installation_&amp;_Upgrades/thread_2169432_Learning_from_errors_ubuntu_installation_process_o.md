---
title: "Learning from errors: ubuntu installation process on a windows/linux system"
date: 2013-08-22
forum: Installation &amp; Upgrades
---

### Post by ventisca on 2013-08-22
Long story short: I overwrote my hard drive partitions with a Linux installation. I know, you heard the joke before... But if you want to read the gory details (and a warning) read the PS.

My drive had several partitions, including windows 8, efi, Linux, a recovery partition and a data partition to use with both Linux and windows. You have all the details in [http://paste.ubuntu.com/6004976/](http://paste.ubuntu.com/6004976/) 

I would be a happy man again if I could get back these last two, but hey beggars can't be choosers. I am right now cloning the drive to another bigger drive... And now my questions start:

1) Ubuntu did a few partitions in the drive while installing. The biggest one takes most of the drive and is ext4. It is basically unused, because I aborted the installation as soon as I noticed my error. My question is... When Ubuntu formatted the disk, did it fill it with zeroes or was it just a "quick format"... Meaning that probably my data is still there waiting to be rescued.

2) As I know the exact location of my old partitions, I tried testdisk to first try and retrieve the old partitions, which gave me a big nothing. Then, I used testdisk to manually write the partitions as they were and with the same file type... To no avail as well. Gparted does not recognise the partitions (it says unknown) and there is no way to read them, that I am aware of. My question is why? I mean, I want to understand how the formatting/partition table works. If the data is still there in the sectors, writing the info of the partition tables shouldn't it reveal it? Maybe the format to another file type does something else that I am unaware of?

Well, any other tips would be welcomed, but at least I want to get something useful from this... And maybe learning how the data structure in the hard drive is written will help me in the future.

Thanks a lot!

PS: The story... In the beginning there was a Toshiba ultrabook with Windows only. As the owner thought that he would be lonely, the owner read a thousand pages of internet and installed Ubuntu and a Data partition. The owner looked at the partition table and said it is good. And the owner was happy. As it was Sunday and the owner was lazy he did not do an image of the disk. One day, the owner decided to make a live USB with Ubuntu. The owner must had been drunk, because he confused the USB stick sdb with one of the partitions of the hard drive sda7. Then, the root partition of Linux was erased and the owner was unhappy. The owner reinstalled the root partition, leaving the home folder as it was, but Ubuntu decided not to follow this and created another home folder inside the home folder. The owner was unhappy and decided to reinstall Ubuntu completely... And clicked on erase Ubuntu 13.04 and replace it with Ubuntu 13.04, instead of a manual install... And all hell broke loose. Warning: the installation of Ubuntu may not recognise the other folders in the hard drive and thinks everything there is Ubuntu and thus erasable

PPS: I am new to this place... Feel free to let me know how many rules I have broken.

---

### Post by TheFu on 2013-08-22
If you want to learn about partition tables, I'd start by learning about partition tables from a high level.
Wikipedia articles [https://en.wikipedia.org/wiki/Master_boot_record](https://en.wikipedia.org/wiki/Master_boot_record) should help.
MBR is just 1 method, there are at least 2 and probably many more methods.
* GPT - [https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table) - the new standard
* APM - [https://en.wikipedia.org/wiki/Apple_Partition_Map](https://en.wikipedia.org/wiki/Apple_Partition_Map) - old Apple method.

From that point, you are beyond most people's knowledge and the best way to understand is to look at the source code for a tool that manages partition tables.  I'd use **parted** as my study source code. It is CLI, non-GUI, which will simplify the code. It supports GPT and MBR and handles newer "Advanced Format" drives by default.  The source code is here: [https://www.gnu.org/software/parted/](https://www.gnu.org/software/parted/) and lots of other places.  I haven't looked at the code myself.

There are 100+ reasons to have good, revisioned, backups. This is just 1 example.

---

### Post by ventisca on 2013-08-22
Thank you for the tips!

As a matter of fact I had already started reading about GPT. Unfortunately, this will not answer to my first question:

1) Does the Ubuntu installation wipe the hard disk completely or just does a quick format and leaves the data there?

It may answer my second question, but if there is anyone out there who knows it I'll appreciate the shortcut:

2) If I know the exact location of my old partition is it enough to build it with parted or testdisk to have the data as it was?

Thanks again

---

### Post by TheFu on 2013-08-23
I don't know the answer to either question. I believe how Ubuntu installs behave has changed over time, so there isn't 1 always true answer.  I do know that if your /home is on a different partition and you do not FORCE a reformat during install, that date will be left alone.  I haven't a clue if it is left alone on / partition or not. Doubtful.  

If you care about your data, you NEED a backup. PERIOD.

Since nobody seems to know the answer to your question, have you considered reading the man pages for parted and/or testdisk?

---

### Post by kamranm1200 on 2013-08-23
> **TheFu said:**
> I don't know the answer to either question. I believe how Ubuntu installs behave has changed over time, so there isn't 1 always true answer.  I do know that if your /home is on a different partition and you do not FORCE a reformat during install, that date will be left alone.  I haven't a clue if it is left alone on / partition or not. Doubtful.  

If you care about your data, you NEED a backup. PERIOD.

Since nobody seems to know the answer to your question, have you considered reading the man pages for parted and/or testdisk?

Actually, the Ubuntu installation has mainly stayed the same for nearly 3 years now. It's a very simple process to install Ubuntu these days.

---

### Post by ventisca on 2013-08-23
Hi again,

Thank you for your replies. I am still looking for the answers to my questions. The issue is not wether or not I need back-ups, which I do need. The issue is wether I can rescue that data and if not at least learn something in the process (besides the need for back-ups).

Anyway, what i have learned up to now is rather interesting. I think that the problem is not wether Ubuntu completely wipes the diskor it just does a "quick format". It seems that changing from ntfs to ext4 is already going to wipe out part of the info. The ext4 file system is completely different than the ntfs... I am still in the learning process, but it seems that while NTFS just has an Master File Table at a certain location, where all the info of the file system is, the ext4 works in blocks all over the hard drive, each block containing some info in a kind of header. This means that, if I am not mistaken, mounting an ext4 file system in a hard drive isalready going to destroy part of the previous information at regular intervals of the hard disk, even if you don't write anything else.

Well, I am still learning and testing with another external hard drive... but right now I think that the culprit of not being able to remount my old partitions is not the formatting itself, but mounting the ext4 file system. If I am right, then probably this post does not belong here, but to the general help.

I'll keep looking and thanks for your attention!

Gabriel

---

