---
title: "Moving system partition - back to front of the disk"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by Lockheed on 2010-01-01
Currently, my disk layout is:
20GB(windows-ntfs) / 250GB data-ext4 / 20GB ubuntu-ext4 / 4gb swap

Since I no longer use windows, I want to move ubuntu to the first place. 

What do I need to change in configuration files, grub and anywhere else?
Shoudl I keep swap where it is or move it, too?

---

### Post by SalahTr on 2010-01-01
You should use **GParted LiveCD**. It doesn't matter where you put swap , it works anyway.

---

### Post by Lockheed on 2010-01-01
There is no way I gonna use ill-conceived GParted. I don't have two weeks to wait for it to finish moving a single file, let alone whole partition.

The quesiton is not how to move the data but what to change in the config files to reflect the change.

---

### Post by SecretCode on 2010-01-01
Why is gparted ill-conceived? That's a pretty strong statement and requires some explanation.

---

### Post by Lockheed on 2010-01-01
Because the simplest operations take hours (sometimes tens of hours) to complete while partitioning software from Acronis or Paragon completes the very same operations under 5 seconds, equally error-less. 
Instead of remeding it, GParted developers claim it is because it is more secure... What use is it if it is unusable?!

---

### Post by SecretCode on 2010-01-01
In my experience gparted only takes more than a minute or two when it's moving large amounts of data. I don't have the kind of drives where any software could move a 10GB partition in 5 seconds. So I still don't know what you're talking about.

---

### Post by Lockheed on 2010-01-01
Moving data takes time, true, but while it takes tens of minutes in, say, Acronis, it can take days in GParted.

What takes seconds in other partitioning software, but hours in GParted is simple partition resizing that does not involve moving data. It is utterly ridiculous and if you are inconceivably lucky not to have been inconvenienced by it, I suggest you google a bit to discover legions of people who are utterly put off from GParted because of this very fact.

Deviating from the deviation, I was wondering if you could advise me on the subject of this topic.

---

### Post by oldfred on 2010-01-01
While technically a hard drive reads the beginning of a drive faster than the end, you will not notice it. Ubuntu is faster than windows because it does not need all the virus and firewall software running in the background. More memory will speed up a system many times more than moving data on a hard drive.

If you move/change partitions the sdx and UUID may change depending on how you do it. That means you have to edit grub files and fstab to have the correct partitions and UUIDs.

---

### Post by Lockheed on 2010-01-01
I am not that concerned about the speed, but rather the reliability. Now, every other boot Ubuntu starts incorrectly, missing, for example, a theme, compiz or a screenlet. I enquired on these forums before about it and the consensus was that this strange behaviour is because Ubuntu is installed on the last partition.

---

### Post by raymondh on 2010-01-01
I've partitioned using fdisk ... but have never 'moved' an existing partition using fdisk, sorry.  Here's a read/reference on fdisk

[http://tldp.org/HOWTO/Partition/fdisk_partitioning.html](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html)

Truth be told, it's been a while since I've used fdisk as I have found/realized that a live gparted CD can do a good job as well (speed and reliability wise).  Just my .02  :)

Have a working/tested back-up of your files before proceeding.

---

