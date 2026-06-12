---
title: "[SOLVED] New Partition On Existing EXT3 Filesystem"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by Ugeen on 2008-10-18
Hello,

Ubuntu:  [Swap Partition FAQ]("https://help.ubuntu.com/community/SwapFaq")

I need to reformat my hard drive but there's about 10 GiBs of data that I would like to move to a partition that hasn't been created, yet.

1. How do I create a new partition via manually or GParted with the following specs?

I added some more memory to the computer since that last reinstall.

2. Do I need to increase the linux-swap partition at this time?  If so, how do I go about doing that since GParted doesn't allow me to make changes to any of the Filesystems?  Swapoff, maybe?  I guess that I could just wait until I reinstall xUbuntu. That would be easier, right?

Operating System
[LIST]
[*]Installed:  xUbuntu
[*]Version:  8.04
[*]Desktop Environment:  Xfce
[*]Release:  Hardy Heron for i386
[/LIST]
System Monitor says
[LIST]
[*]System tab
[LIST]
[*]Ubuntu
[LIST]
[*]Release 8.04 (hardy)
[*]Kernel Linux 2.6.24-21-generic
[/LIST]
[*]Hardware
[LIST]
[*]Memory:  3.0 GiB
[*]Processor 0:  Intel(R) Pentium(R) 4 CPU 2.80GHz
[*]Processor 1:  Intel(R) Pentium(R) 4 CPU 2.80GHz
[/LIST]
[*]System Status
[LIST]
[*]Available disk space:  16.3 GiB
[/LIST]
[/LIST]
[*]Resources tab
[LIST]
[*]Memory and Swap History
[LIST]
[*]Memory:  3.0 GiB
[*]Swap:  5 GiB
[/LIST]
[/LIST]
[/LIST]
GNOME Partition Editor (GParted)
[LIST]
[*]Version: 0.3.5
[INDENT]
Partition:  /dev/sda1
Filesystem:  ext3
Mountpoint:  /
Size:  35.68 GiB
Used:  17.59 GiB
Unused:  18.09 GiB
Flags:  boot
[/INDENT]
[INDENT]
Partition:  /dev/sda2
Filesystem:  extended
Mountpoint:
Size:  1.57 GiB
Used:  ---
Unused:  ---
Flags:
[/INDENT]
[INDENT]
[INDENT]
Partition:  /dev/sda5
Filesystem:  linux-swap
Mountpoint:
Size:  1.57 GiB
Used:  ---
Unused:  ---
Flags:  
[/INDENT]
[/INDENT]
[/LIST]

GNOME Partition Editor gives me the following error when I try to unmount.  FYI:  I understand why it will not allow me to unmount /dev/sda1.

> 
**Could not unmount /dev/sda1**

The partion could not be unmounted from the following mountpoints:

/

Most likely other partitions are also mounted on these mountpoints.  You are advised to unmount them manually.

[INDENT]
> **Ugeen said:**
> 
The following website walked me through the process of mounting my partition drive.

psychocats.net: [http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")

[/INDENT]
Thank you in advance for your help.
Sincerely,
--Ugeen

---

### Post by Partyboi2 on 2008-10-18
Boot a[[COLOR=Blue] gparted live cd[/COLOR]]("http://gparted.sourceforge.net/"). You can not work on partitions while they are in use, so you need to use a live cd. When gparted is open right click on your sda1 partition and make sure that it is unmounted. Then press the resize button and shrink down your sda1 partition so that at the end of it you have 10gig. Then turn your swap off (right click on swap) and resize unallocated space so that the unallocated space is moved to your extended partition. Then make a 10 gig ext3 partition and afterward turn swap back on. 
Remember to back up your data before working on partitions.

---

### Post by Ugeen on 2008-10-18
> **Partyboi2 said:**
> Boot a[[COLOR=Blue] gparted live cd[/COLOR]]("http://gparted.sourceforge.net/"). You can not work on partitions while they are in use, so you need to use a live cd. When gparted is open right click on your sda1 partition and make sure that it is unmounted. Then press the resize button and shrink down your sda1 partition so that at the end of it you have 10gig. Then turn your swap off (right click on swap) and resize unallocated space so that the unallocated space is moved to your extended partition. Then make a 10 gig ext3 partition and afterward turn swap back on. 
Remember to back up your data before working on partitions.

Hello Partyboi2,

I'm getting the following error message.  However, I was able to partition the drive with what you've provided me with.  Thank you.

1. How do I fix this error?

> Failed to mount "10G Volume".

org.freedesktop.hal.storage.mount-fixed
auth_admin_keep_always <-- (action, result).

The following is how I got to the error message.
Disclaimer:  Anyone reading this should read the whole thing since I had to rebooted my system once (1 time), partitioned twice (2 times) and afterward the drive is:  unmounted.

**Using: [GParted]("http://gparted.sourceforge.net/") Live CD**

[LIST=1]
[*]Bootup Attempt
[LIST=2]
[*]Selected GParted Live (Default settings)
[*]The startup paused at:  Setting the system clock.
[LIST]
[*]...waited
[*]...waited
[*]...waited
[/LIST]
[*]Rebooted
[/LIST]


[*]Bootup Attempt
[LIST=2]
[*]Selected GParted Live (Default settings)
Note: It ran through completely this time.
[*]Selected: Don't touch keymap
[*]Graphical Environment
If needed, do the following in a Terminal Window.
(FYI:  I did not need to run this code.)
```
Terminal:  sudo Forcevideo
```
[/LIST]
[/LIST]
**Within Application: GNOME Partition Editor (GParted)**

[LIST=1]
[*]Partition Attempt


[LIST=2]
[*]Unmount Filesystem:  ext3
(Partition:  /dev/sda1)
[LIST=3]
[*]Clicked on Filesystem:  ext3
[*]Clicked on Partition
[*]Unmount was not an option.
[/LIST]


[*]Resize Filesystem: ext3
(Partition:  /dev/sda1)
[LIST=3]
[*]Clicked on Filesystem:  ext3
[*]Clicked on Partition
[*]Clicked on Resize/Move
[*]A window appeared with a title of:  Resize/Move
[LIST=4]
[*]Clicked and draged the right triangle from the right to the left and removing all of the white space.
[*]Clicked on the Resize/Move button.
[/LIST]
[/LIST]
Note: In the GParted window, a new partition was created:
[LIST]
[*]Partition: /dev/sda6
[*]Filesystem:  unallocated
[/LIST]


[*]Toggle Swap:  Swapoff
[LIST=3]
[*]Clicked on Filesystem:  linux-swap
(Partition: /dev/sda5)
[*]Clicked on Partition
[*]Available option:  Swapon
(i.e. Swap is already off.)
[/LIST]


[*]Resize Filesystem: extended
(Partition:  /dev/sda2)
[LIST=3]
[*]Clicked on the Filesystem:  extended
[*]Clicked on Partition
[*]Clicked on Resize/Move
[*]A window appeared with a title of:  Resize/Move
[LIST=4]
[*]Clicked and dragged the left triangle and moved it all the way to the left.
[*]Clicked on the Resize/Move button
[/LIST]
[/LIST]
Note: In the GParted window, the Filesystem:  unallocated moved under the Filesystem:  extended.


[*]New Partition Filesystem: unallocated
[LIST=3]
[*]Clicked on the Filesystem:  unallocated
[*]Clicked on Partition
[*]Clicked on New
[*]A window appeared with a title of:  Create new Partition
[LIST=4]
[*]From the Filesystem options, I selected: ext3
[*]In the New Size (MiB) textbox, I changed it to:  10240
(i.e. 10 MiB)
(Note (does not show in the Create New Partition window): 1 MiB = 1024 KiB)
[*]Clicked on the Add button
[/LIST]
[/LIST]


[*]Resize Filesystem:  linux-swap
[LIST=3]
[*]Clicked on Filesystem:  linux-swap
[*]Clicked on Partition
[*]Clicked on Resize/Move
[*]A window appeared with a title of:  Resize/Move
[LIST=4]
[*]In the New Size (MiB) textbox, I changed it to:  5122 (i.e. 5 MiB)
(Recommended (read in another post):  1.5 x size of memory, which in my case it would be 4.5 MiB but I went a head and made it 5 MiB.  To make it 5 MiB, I had to make the new size:  5122 but 1024 (1 MiB) x 5 = 5210 but that gave me 5.09 MiB) and I'm not sure why.)
[*]Clicked on the Resize/Move button
[/LIST]
[/LIST]


[*]Getting Size of Filesystem:  unallocated
FYI:  I wasn't able to move the Filesystem:  unallocated out of the Filesystem:  extended.
[List=3]
[*]Clicked on Filesystem:  unallocated
[*]Clicked on Partition
[*]Clicked on New
[*]A window appeared with a title of:  Create new Partition
[LIST=4]
[*]Wrote down the New Size (MiB) amount:  4761
[*]Clicked on Cancel
[/LIST]
[/LIST]


[*]Starting Over
[LIST=3]
[*]Clicked on Edit
[*]Clicked on Clear All Operations
[/LIST]
[/LIST]


[*]Partition Attempt


[LIST=2]
[*]Resize Filesystem:  ext3
[List=3]
[*]Clicked on Filesystem:  ext3
[*]Clicked on Partition
[*]Clicked on Resize/Move
[*]A window appeared with a title of:  Resize/Move
[LIST=4]
[*]Updated the value in the New Size (MiB) textbox:
[LIST]
[*]From:  36538
[*]To:  22787
[/LIST]
[*]Clicked on the Resize/Move button
[/LIST]
[/LIST]


[*]Apply Operatoins
Note: From 2.1. (Resize Filesystem: ext3)
[LIST=3]
[*]Clicked on Edit
[*]Clicked on Apply All Operations
[*]A window appeared with the title of:  Apply operations to harddisk
[LIST=4]
[*]Clicked on the Apply button
[*]A window appeared with the title of:  Applying pending operations
[LIST=5]
[*]...waited
[*]...waited
[*]A window appeared with the title of:  Unnamed
(i.e it's an error message)
> Unnamed

An error occurred while applying the operations

See the details for more information.

**IMPORTANT**
If you want support, you need to provide the saved details!
See [http://gparted.sourceforge.net/larry/tips/](http://gparted.sourceforge.net/larry/tips/)
save_details.htm for more information.

[LIST=6]
[*]Clicked on the OK button
[/LIST]
[/LIST]
[/LIST]
[/LIST]


[*]Toggle Swap:  Swapoff
[LIST=3]
[*]Clicked on Filesystem:  linux-swap
(Partition: /dev/sda5)
[*]Clicked on Partition
[*]Clicked on Swapoff
[/LIST]


[*]Resize Filesystem:  linux-swap
[LIST=3]
[*]Clicked on Filesystem: linux-swap
[*]Clicked on Partition
[*]Clicked on Resize/Move
[*]A window appeared with a title of:  Resize/Move
[LIST=4]
[*]In the New Size (MiB) textbox: 5122
(i.e. 5 MiB)
[*]Clicked on the Resize/Move button
[/LIST]
[/LIST]


[*]Apply Operatoins
Note: From 2.4. (Resize Filesystem: linux-swap)
[LIST=3]
[*]Clicked on Edit
[*]Clicked on Apply All Operations
[/LIST]


[*]New Partition Filesystem: unallocated
[LIST=3]
[*]Clicked on the Filesystem:  unallocated
[*]Clicked on Partition
[*]Clicked on New
[*]A window appeared with a title of:  Create new Partition
[LIST=4]
[*]From the Filesystem options, I selected: ext3
[*]In the New Size (MiB) textbox, I changed it to:  10240
(i.e. 10 MiB)
(Note (does not show in the Create New Partition window): 1 MiB = 1024 KiB)
[*]Clicked on the Add button
[/LIST]
[/LIST]


[*]Apply Operatoins
Note: From 2.6. (Resize Filesystem: unallocated)
[LIST=3]
[*]Clicked on Edit
[*]Clicked on Apply All Operations
[/LIST]


[*]Reboot
[LIST=3]
[*]Clicked on the Exit button (i.e. closed GParted)
[LIST=4]
[*]...waited
[*]Clicked on Reboot
[/LIST]
[/LIST]
[/LIST]

**Take a look at the new partition or lack of.**


[LIST=1]
[*]I didn't see the new partition.
[LIST=2]
[*]Format it, I thought?
[/LIST]


[*]Application GParted
(FYI:  I have installed on /dev/sda1 (i.e. I did not reboot with GParted Live CD).
[LIST=2]
[*]Scanning all devices...
[LIST=3]
[*]...waited
[*]...waited
[*]A window appeared with the title of:  Failed to mount "10G Volume".
(i.e it's an error message)
> Failed to mount "10G Volume".

org.freedesktop.hal.storage.mount-fixed
auth_admin_keep_always <-- (action, result).

[LIST=4]
[*]Clicked on Close button
[/LIST]
[/LIST]
[/LIST]


[*]Toggle Swap:  Swapoff
[LIST=2]
[*]Clicked on Filesystem:  linux-swap
(Partition: /dev/sda5)
[*]Clicked on Partition
[*]Clicked on Swapon
[LIST=3]
[*]Scanning all devices...
[LIST=4]
[*]...waited
[*]...waited
[/LIST]
[/LIST]
[/LIST]


[*]Format Filesystem: ext3
(Partition: /dev/sda6)
[LIST=2]
[*]Clicked on Filesystem: ext3 (i.e. /dev/sda6)
[*]Clicked on Partition
[*]Clicked on Format to
[*]Clicked on ext3
[*]Scanning all devices...
[LIST=3]
[*]...waited
[*]...waited
[*]A window appeared with the title of:  Failed to mount "10G Volume".
(i.e it's an error message)
> Failed to mount "10G Volume".

org.freedesktop.hal.storage.mount-fixed
auth_admin_keep_always <-- (action, result).

[LIST=4]
[*]Clicked on Close button
[/LIST]
[/LIST]
[/LIST]
[/LIST]
[/LIST]

Thank you again for all of your help.
Sincerely,
--Ugeen

---

### Post by Ugeen on 2008-10-20
Hello Partyboi2,

I noticed that my Swap is 0 GiB.  However, I turned it on twice (2 times) already.

[LIST=1]
[*]Why is my Swap 0 GiB?  It should be 5 GiB.
[LIST=a]
[*]Do I need to turn it on each time I bootup? ...of course not.  What do I need to do to get this resolved?
[/LIST]
[/LIST]

System Monitor
[LIST]
[*]Resources tab
[LIST]
[*]Swap
[LIST]
[*]0 bytes (0.0%) of 0 bytes
[/LIST]
[/LIST]
[/LIST]
Thank you again for your help.
Sincerely,
--Ugeen

---

### Post by Ugeen on 2008-10-25
> **plucky said:**
> 
Take a look at this link for [Mounting a linux Partition](http://www.psychocats.net/ubuntu/mountlinux) and is also a good place to learn about partitioning.

Hello,

The following website walked me through the process of mounting my partition drive.  However, my swap partition is not turning on at bootup.

psychocats.net: [http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")

Thank you [plucky]("http://ubuntuforums.org/member.php?u=317619") and [psychocats.net]("http://www.psychocats.net/") for all of your help.
Sincerely,
--Ugeen

---

### Post by confused57 on 2008-10-25
You might want to post the output of:
```
gedit /etc/fstab
```
and
```
free
```

Here's another useful website that you might want to bookmark:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by lswb on 2008-10-25
I'm not sure I'm following all the steps you took, but as far as the swap partition, if you resized it, it probably was assigned a new uuid and likely your /etc/fstab just needs to be changed for it to be recognized. You can enter the command

sudo blkid -c /dev/null

in a terminal to get the uuids of all partitions on your system, After you determin which is for the swap partition use cut and paste to change the swap entry in /etc/fstab to the new uuid.

---

### Post by Bucky Ball on 2008-10-25
> **lswb said:**
> I'm not sure I'm following all the steps you took, but as far as the swap partition, if you resized it, it probably was assigned a new uuid and likely your /etc/fstab just needs to be changed for it to be recognized. You can enter the command

sudo blkid -c /dev/null

in a terminal to get the uuids of all partitions on your system, After you determin which is for the swap partition use cut and paste to change the swap entry in /etc/fstab to the new uuid.


That sound about right.

```
sudo blkid
```and ...

```
nano /etc/fstab
```would be helpful for us to sort this out. Think your machine is just looking in all the wrong places.

---

### Post by Ugeen on 2008-10-25
> **lswb said:**
> 
I'm not sure I'm following all the steps you took, but as far as the swap partition, if you resized it, it probably was assigned a new uuid and likely your /etc/fstab just needs to be changed for it to be recognized. You can enter the command

sudo blkid -c /dev/null

in a terminal to get the uuids of all partitions on your system, After you determin which is for the swap partition use cut and paste to change the swap entry in /etc/fstab to the new uuid.

Hello lswb,

Updating the UUID fixed the swap problem.

Thank you again for all of your help.
Sincerely,
--Ugeen

---

### Post by Ugeen on 2008-10-25
Hello,

My new partition is created but I cannot seem to get to it.

[LIST=1]
[*]How can I get to my new partition through the Gnome GUI?
(e.g. Places \ File System -- FYI:  It's not listed.)
[/LIST]
Thank you in advance for your help.
Sincerely,
--Ugeen

---

### Post by Ugeen on 2008-10-26
> **Ugeen said:**
> 
Hello,

My new partition is created but I cannot seem to get to it.

[LIST=1]
[*]How can I get to my new partition through the Gnome GUI?
(e.g. Places \ File System -- FYI:  It's not listed.)
[/LIST]
Thank you in advance for your help.
Sincerely,
--Ugeen

I found my partition drive.
[LIST=1]
[*]Clicked on Places
[*]Clicked on File System
[LIST]
[*]A window appeared with a title of:  File System - File Manager
[/LIST]
[*]Clicked on File System
[*]Clicked on Storage
[*]Clicked on File
[*]Clicked on Properties
[LIST]
[*]A window appeared with a title of:  storage - Properties
[/LIST]
[*]Volume:  10G Volume
[/LIST]
...I tired this folder because inside it there is another folder called, "lost+found," which I was curious why there were two (2) folders with the same name.  That probably sounds a little odd but at least I found what I was looking for. :)

Thank you for all of your help.
Sincerely,
--Ugeen

---

