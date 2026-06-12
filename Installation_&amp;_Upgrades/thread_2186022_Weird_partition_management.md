---
title: "Weird partition management"
date: 2013-11-05
forum: Installation &amp; Upgrades
---

### Post by nkealen on 2013-11-05
I'm installing 12.04 onto a Dell PowerEdge 2650 server that has four SCSI hard drives installed.

[LIST]
[*]sda at 36GB
[*]sdb at 73GB
[*]sdc at 73GB
[*]sdd at 146GB
[/LIST]

I'm having a hard time getting the drives setup the way I'd like. Here's my idea:

[LIST]
[*]the 36GB drive for booting, swap, and root (basically the OS)
[*]the two 73GB drives running at software RAID 1 with the /home dir (my user data)
[*]the 146GB drive mounted /archive (for, uh...archiving)
[/LIST]

If I just select the guided install it only works with the 36GB drive. When I manually try to configure them, it appears I cannot mount /home on the software RAID 1 drive. I don't really know if this is optimal or not. I'd be open to some suggestions.

Also, would it be better to configure the RAID 1 drive and the /archive drive after the install? Any tips?

---

### Post by Bashing-om on 2013-11-05
nkealen; Hi !

Desk top install DVD ? .. does not have the tools to cope with raid.
Down load the server edition of ubuntu.
Then in the install are the tools to set up raid.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by nkealen on 2013-11-05
I'm using the server CD. Somewhere in the manual process of partitioning I'm getting the conflict.

---

### Post by Bashing-om on 2013-11-05
nkealen; OK !

It has been a while since I set up a server/raid ..
Let me get caught up on the other threads and I will hunt up my notes and get back at ya.

[INDENT][INDENT]be on my mind
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-11-05
nkealen; Hey I am back.
The last place I looked is where I found my notes !

Basically it goes like so:
In the installer select "manually edit partition table" not ready yet for doing "Configure software RAID" - The physical partitions must be set up first.

list of physical drives: arrow down highlighting the physical drive (not any of it's partitions) and hit enter -> confirm replacing the existing partition table. That gets you the only entry below this drive as "FREE SPACE".

Do the same for the other drive.
Back on the 1st drive, select that "free space"  (to be /home) and create the partition -> size, file system and mount options. Now instead of plopping a filesystem on this raw partition, enter into the "use as dialog" and set the partition to be a physical volume for RAID.

In the second drive create the exact same partition.
Return to the initial partitioning screen and you should see an identically sized partition under each drive . 
NOW choose "Configure Software RAID at the top of the screen. Agree to write changes to the storage device and then choose to create the MD (Multi Disk) device.

After selecting "RAID 1; you will enter the number of active devices for the array (in your case 2), number of spare devices = 0.
Space bar to check both partitions (sda1 sdb1) and hit finish in the Multidisk dialog to return to the basic partitioner.

You should now see below the 2 physical drives a new drive - the Software RAID device with 1 partition below it. arrow over to it and hit enter, it can now be configured as you would  any partition.
-------------
The process is the same for any other partitions you want to toss into RAID.
Create identical-sized partitions on all the participating physical devices. select to use them as RAID space, enter the MultiDisk configurator and finally create an array that utilizes the real partitions. THEN create the file system on the newly created array.
--------------------

This is an old guide, but the idea is still the same;
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

There may be later guides out, I have not seen any.

[INDENT][INDENT]I hope this helps
[/INDENT][/INDENT]

---

