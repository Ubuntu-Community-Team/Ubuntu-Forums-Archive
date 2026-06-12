---
title: "Need Help with root permissions ?"
date: 2011-12-11
forum: Installation &amp; Upgrades
---

### Post by fairbird on 2011-12-11
i have some folders and files and i want to make format to my pc ...  i was formated my usb flash to ( compatible with linux (ext4) )and then i copy all my files from pc to usb flash . after that i was formated my pc and install win 7 and ubuntu 10.04 inside win 7 then i was returned my files from usb to pc ... but when i want to use it i can not and give my error as like picture below ... so what i must to do ? any body have any idea ?
By the way i was tried to made chmod 755 and 777 and also i do ( gksu nautilus ) and made chmod but nothings happend ?

[IMG]http://www.freeimagehosting.net/c26a8[/IMG][IMG]http://www12.0zz0.com/2011/12/11/14/555555888.png[/IMG]


[IMG]http://www.freeimagehosting.net/e133e[/IMG][IMG]http://www13.0zz0.com/2011/12/11/14/451921059.png[/IMG]


Thank's

---

### Post by bulldog on 2011-12-11
Well,you are the owner of the .deb,so the only thing that comes to mind is data corruption.
Download the .deb again and see if that works any better.

---

### Post by fairbird on 2011-12-11
@bulldog
Thank you for replay ...
already i was download new .deb like ( wine 1.2.3 ) and it was worked fine ... but i have more than 100 pakages= 800 MB i can't download it again ... any way to fix permission my pakages ?

---

### Post by bulldog on 2011-12-11
I don't think permissions are an issue,data corruption is probably the culprit.
I think something went wrong when you backed up the data,maybe you removed the USB device too soon from the computer,but if this error appears from every .deb you backed up,the only thing remains to do is to download them again,sorry, I can't be of more help.

---

### Post by fairbird on 2011-12-11
Thank you again....
 
Not all files data corruption ...some files worked and some does not :( also favorites backup for fairfox have same error :confused:

---

### Post by CharlesA on 2011-12-11
Try installing the package using dpkg:

```
sudo dpkg --install packagename.deb
```

---

### Post by fairbird on 2011-12-11
> **CharlesA said:**
> Try installing the package using dpkg:

```
sudo dpkg --install packagename.deb
```

Thank you ...

i got this in terminal 

> raed@ubuntu:~$ cd Desktop
raed@ubuntu:~/Desktop$ sudo dpkg --install wine1.2_1.2.3-0ubuntu1~ppa2~lucid1_i386.deb
dpkg-deb: `wine1.2_1.2.3-0ubuntu1~ppa2~lucid1_i386.deb' is not a debian format archive
dpkg: error processing wine1.2_1.2.3-0ubuntu1~ppa2~lucid1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 wine1.2_1.2.3-0ubuntu1~ppa2~lucid1_i386.deb
raed@ubuntu:~/Desktop$ 


---

### Post by CharlesA on 2011-12-11
That error means that the archive is corrupted.

---

### Post by fairbird on 2011-12-11
So there is no hope ... :(

Thank you all

---

### Post by CharlesA on 2011-12-11
> **fairbird said:**
> So there is no hope ... :(

Thank you all
Where did you get that deb?

---

### Post by fairbird on 2011-12-12
> **CharlesA said:**
> Where did you get that deb?
 
 i was downloaded from symantec centre and i was made backup by aptcd software

---

### Post by CharlesA on 2011-12-12
That is odd.

Try installing wine directly from software center.

---

### Post by fairbird on 2011-12-12
> **CharlesA said:**
> That is odd.
 
Try installing wine directly from software center.
 
I was downloaded already from software center ... but i have another packages and some files like firefox favorites backup i can not use it :(

---

### Post by fairbird on 2011-12-13
Thank you friends...
i was tried but same error show as like in above picture ..

and this picture from APTonCD .. if i want to restore my backup

[IMG]http://www10.0zz0.com/2011/12/13/15/604160261.png[/IMG]

---

### Post by CharlesA on 2011-12-13
Run fsck on the main drive from a livecd and report any errors.

It sounds like the hard drive may be having problems.

Also run any SMART tools from the manufacturer of that drive.

Either that or aptoncd didn't work correctly. I've never used it so I don't know.

Does the same thing happen if you copy the deb files to /var/cache/apt/ ?

---

### Post by fairbird on 2011-12-13
> **CharlesA said:**
> 
 
Does the same thing happen if you copy the deb files to /var/cache/apt/ ?
 
yes friend it was same thing same error

---

### Post by CharlesA on 2011-12-13
Either aptoncd messed something up, or something is wrong with the disk.

Were you able to run fsck ?

---

### Post by fairbird on 2011-12-13
from terminal after run fsck from livecd

```
raed@ubuntu:~$ sudo fsck
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/host/ubuntu/disks/root.disk: clean, 145000/624624 files, 923739/2494464 blocks
raed@ubuntu:~$ fsck
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/host/ubuntu/disks/root.disk: recovering journal
Clearing orphaned inode 148112 (uid=1000, gid=1000, mode=0100600, size=40)
Clearing orphaned inode 147998 (uid=1000, gid=1000, mode=0100600, size=207)
Clearing orphaned inode 147201 (uid=1000, gid=1000, mode=0100644, size=32768)
Illegal inode 1323807182 in orphaned inode list.
/host/ubuntu/disks/root.disk was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -743988 -(744004--744011)
Fix<y>? yes

Free blocks count wrong for group #2 (617, counted=626).
Fix<y>? yes

Free blocks count wrong for group #22 (3019, counted=3028).
Fix<y>? yes

Free blocks count wrong (1570705, counted=1570723).
Fix<y>? yes

Inode bitmap differences:  -141635 -145209 -147201 -147213
Fix<y>? yes

Free inodes count wrong for group #17 (1, counted=3).
Fix<y>? yes

Free inodes count wrong for group #18 (5315, counted=5317).
Fix<y>? yes

Free inodes count wrong (479619, counted=479623).
Fix<y>? yes


/host/ubuntu/disks/root.disk: ***** FILE SYSTEM WAS MODIFIED *****
/host/ubuntu/disks/root.disk: 145001/624624 files (0.1% non-contiguous), 923741/2494464 blocks
raed@ubuntu:~$ 
```

---

### Post by CharlesA on 2011-12-13
Good thing that fsck was able to do the repair. Are you still getting the same error when running dpkg -i ?

---

### Post by fairbird on 2011-12-13
> **CharlesA said:**
> Good thing that fsck was able to do the repair. Are you still getting the same error when running dpkg -i ?

yes friend same thing
> raed@ubuntu:~$ cd Desktop
raed@ubuntu:~/Desktop$ sudo su
root@ubuntu:/home/raed/Desktop# dpkg -i xz-utils_4.999.9beta+20091116-1_i386.deb
dpkg-deb: `xz-utils_4.999.9beta+20091116-1_i386.deb' is not a debian format archive
dpkg: error processing xz-utils_4.999.9beta+20091116-1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 xz-utils_4.999.9beta+20091116-1_i386.deb
root@ubuntu:/home/raed/Desktop#

---

### Post by CharlesA on 2011-12-13
Ok.

Is there a reason you are using aptoncd? Are you able to boot off a livecd and install the deb on there? That would rule out or confirm the hard drive is the problem.

---

### Post by fairbird on 2011-12-13
> **CharlesA said:**
> Ok.
 
Is there a reason you are using aptoncd? Are you able to boot off a livecd and install the deb on there? That would rule out or confirm the hard drive is the problem.
 
but same packages in backup i was used before and worked but now after i was copied backup to usb and made formated to my pc i got this error, some packages from backup worked ok and some doesn't :(

---

