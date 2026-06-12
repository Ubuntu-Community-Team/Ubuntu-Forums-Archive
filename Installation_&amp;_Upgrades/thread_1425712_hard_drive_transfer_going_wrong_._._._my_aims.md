---
title: "hard drive transfer going wrong . . . my aims"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by objective on 2010-03-09
Hi All

I've moved to Ubuntu and I'm loving it !  My install went well - couple of problems, but nothing to worry about - and I find it far more fun & stable than my XP Windows.  Brilliant!



HOWEVER, I have a disk copy problem.

while I switch to Ubuntu, I still need to access my XP machine for all the software I have loaded on it.  However, since its pretty disk-bound, my aim was to keep it usable while I found (& got up to speed) on the alternatives in --ix environment.  
So, I'm trying to move my old XP desktop to a larger hard drive. 

The current XP installation is on a 80Mb disk.  I was aiming to copy over its contents to a 160Mb disk and make this bootable to replace the original disk.  this should maintain my email use of the XP machine and keep the graphics software usable while I migrate.

more >>>
this is what I aimed to do, next what I did . . . 
----------------------

I'm really grateful to you good people applying your knowledge to help, so I thought I'd split my post into three sections:
- what I'm trying to do
- what I've done so far
and
- the mess I've created for myself, where I am with it and outputs I'm getting.

---

### Post by objective on 2010-03-09
So I connected the 2 drives via USB to my Ubuntu computer.  I then used file browser to select and copy all files on the smaller drive, and copied onto the larger drive. 

The copy seemed to be going well -  around 75Gb of files.  I'd disabled the screen-saver and power management (I think) so the process wouldn't be interrupted.

Well, it looks like it was, and maybe by some power management I didn't disable because the Ubuntu laptop seemed to be in suspend mode when I looked next.

Now I can't mount either external USB drives, (and neither the new drive, or disastrously the original drive is bootable when re-installed back on their computer.

My original PC drive is labelled 
- T41_object
(Its a single NTFS partitioned drive of 80 Gb capacity)

and the new, larger drive is labelled
- caroline
(This is also a single NTFS partitioned drive, but of 160Gb capacity).

----------------------

I'm really grateful to you good people applying your knowledge to help, so I thought I'd split my post into three sections:
- what I'm trying to do
- what I've done so far
and
- the mess I've created for myself, where I am with it and outputs I'm getting.

---

### Post by objective on 2010-03-09
I see both drives in Palimpsest Disk Utility - the disk labels are read and the disk size is reported correctly.  

They are 
/dev/sdc,  
and 
/dev/sdb 
respectively

When I go to the file browser, and select each drive connected via a USB cable I get 
for T41_OBJECT: - 

-----------
Unable to mount T41_OBJECT

Error mounting: mount exited with exit code 13: ntfs_mst_post_read_fixup: magic: 0x454c4946  size: 4096  usa_ofs: 48  usa_count: 2: Invalid argument
Actual VCN (0x3800020036) of index buffer is different from expected VCN (0x4).
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


This is the error I get when connecting the 2nd drive "Caroline" :

-------------
Unable to mount CAROLINE

Error mounting: mount exited with exit code 14: Hibernated non-system partition, refused to mount.
Failed to mount '/dev/sdb1': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, or mount the volume read-only with the 'ro' mount option, or
mount the volume read-write with the 'remove_hiberfile' mount option.
For example type on the command line:

            mount -t ntfs-3g -o remove_hiberfile /dev/sdb1 /media/Caroline


-------
What other info might be useful ??

I have tried to mount the CAROLINE drive by using a terminal session and: 

'sudo mount -t ntfs-3g -o remove_hiberfile /dev/sdb1 /media/Caroline'

This just returns a file usage list so obviously I have some syntax wrong.
Is this a case
 
Right now I'd settle for either drive booting my XP laptop again, so that I can get chased by email again.

I've searched the forums, and realise that I should have slowed down a little, and looked up dd (data dump, I think) and used this to make the transfer.  Oh dear.  Can I retrieve this ??

Sorry this post is sooo long - I split it in the hope that I'm getting the information down that's needed, but not bored everyone with my life story . . .

Anyone help ??

Paul

---

### Post by akand074 on 2010-03-09
Sorry you have a lot of posts and its long and confusing. What is the problem in short? Try restarting your computer and booting back into linux I find the hibernation/resume isn't very good its supposed to be better in the next release. Maybe you will be able to mount them after the restart. Also I don't think copy and pasting the entire partition will make Windows bootable, I may be wrong. It might be better to make an image of the entire drive and then install the image on the other hard drive. Don't delete anything from your old hard drive either until its working perfectly on the other drive. Windows is not very cooperative with things like this.

---

### Post by objective on 2010-03-09
Hi Akand074
The short answer is I have 2 drives.
One used to have a bootable XP on it, with lots of valuable programs that would take ages (like days) to reinstall.  Now this 80Gb NTFS drive won't boot its laptop when reinstalled.  
The other drive was just formatted as a NTFS single (160Gb) partition.  I can't look at the drive to see how much has copied over, but after installing in a laptop, it doesn't boot.

Thanks for the suggestion to reboot my ubuntu install, and try again.  Tried that, with no joy.

Any suggestions gratefully received!

Paul

---

### Post by objective on 2010-03-09
How about this section of the info I posted:
"NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important!"

How do I run chkdsk /f on either drive, when they won't boot.  Is chkdsk a UNIX command?

Cheers
P

---

### Post by objective on 2010-03-09
How about this bit:
"The NTFS partition is hibernated. Please resume and shutdown Windows
properly, or mount the volume read-only with the 'ro' mount option, or
mount the volume read-write with the 'remove_hiberfile' mount option.
For example type on the command line:

            mount -t ntfs-3g -o remove_hiberfile /dev/sdb1 /media/Caroline"

Should I be looking to delete a "hibernate" file on the drive ??

---

### Post by akand074 on 2010-03-09
Sorry about that I had a lab to go to. So the original windows that you want to copy, does that still boot? Also chkdsk is a windows command, if you have you have a windows cd you can run into a command prompt and run it. If you go to Places in the menu does it not show the other partitions/hard drives?

Type this into the terminal (Accessories > Terminal):

```
sudo fdisk -l
```

It will prompt you for your password, just type it in and press enter. and then paste the results here.

---

### Post by objective on 2010-03-09
Hi Mate

Here is the result of exactly what you suggested:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9eba324c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14408   115732228+  83  Linux
/dev/sda2           14409       14593     1486012+   5  Extended
/dev/sda5           14409       14593     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x86082d4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xf08bf08b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       10337    78147688+   7  HPFS/NTFS

------
So /dev/sda1, /dev/sdb1, /dev/sdc1, can be addressed by the look of it.

Really appreciate your time,
many thanks
Paul

---

### Post by akand074 on 2010-03-09
Not a problem, so which hard drive are you trying to mount? The 160GB hard drive is sdb, the 80GB hard drive is sdc. Try mounting it this way (open terminal and paste this):

```
sudo mkdir /media/sdb1
```

then mount it using

```
mount /dev/sdb1 /media/sdb1
```

switch sdb1 with sdc1 if you want the 80GB hard drive mounted. That should likely work to see the content of the hard drive. If you manage to get in and all the files are correctly pasted on the drive you can try using a windows CD to repair the start up so it becomes bootable, or you can find another way to transfer your windows to another hard drive. Let me know if your able to mount it first and then we'll work from there.

---

### Post by objective on 2010-03-10
Hi Ak

Sorry for the delay, had to get some sleep.
Here's what I get :

paul@paul-laptop:~$ sudo mkdir /media/sbd1
[sudo] password for paul: 
paul@paul-laptop:~$ mount /dev/sdb1 /media/sdb1
mount: only root can do that

I understand that ''sudo' prefix asks for root privileges, and it seemed to accept my password OK.   

So I tried:

paul@paul-laptop:~$ sudo mount /dev/sdb1 /media/sdb1 

and got this:

paul@paul-laptop:~$ sudo mount /dev/sdb1 /media/sdb1
ntfs_mst_post_read_fixup: magic: 0x454c4946  size: 4096  usa_ofs: 48  usa_count: 2: Invalid argument
Actual VCN (0x3800020036) of index buffer is different from expected VCN (0x4).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

-----------

Does this help ?  (My root sudo doesn't seem to persist for very long)

Thanks for your support here

Paul

---

### Post by akand074 on 2010-03-10
Sorry for the delay I had class all day. Hmm well I'm stumped, try forcing it using:

```
mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
```

but it looks like the windows partition is corrupted and the only way to fix it is using Windows installer cd and choose the repair and try running chkdsk /f

Also check out this thread, it might be a little helpful:

[http://ubuntuforums.org/showthread.php?t=1142397](http://ubuntuforums.org/showthread.php?t=1142397)

---

