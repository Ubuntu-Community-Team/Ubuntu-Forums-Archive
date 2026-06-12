---
title: "cannot boot the pc as path of root partition changed mistakenly."
date: 2016-03-11
forum: Installation &amp; Upgrades
---

### Post by bijaydeyp on 2016-03-11
Hi, I am writing this from ubuntu live session(14.4.4lts).  because my
 problem is I can't boot from hdd currently.

today I did some work using GParted partition tool. (see screenshot of old partition & boot options). though I didn't touch any windows partition. I just modified a ntfs logical partition.but I overlooked the changed path names of logical partitions.

the root & swap partition was on /dev/sda6 & /dev/sda7.after modification the path names changed and now the same root & swap partition is on /dev/sda5 & /dev/sda6(see screenshot of new partition).

so when I boot from HDD the GRUB says  .....

error:unknown file system
entering rescue mode
grub rescue>_


can anyone plz help me to fix this as quick as possible?? i have important files on /home directory.

---

### Post by ajgreeny on 2016-03-11
It is most likely that the partitions shown in the /etc/fstab file are now incorrect, hence the inability to boot Ubuntu.

Can you still boot to Windows 7?

Let's see the live OS terminal output of commands ```
sudo blkid -c /dev/null
cat /media/ubuntu/*root-partition*/etc/fstab
``` where root-partition is whatever shows in the Ubuntu file-manager for that installed OS partition.

If you prefer a GUI you can use the file-manager in the live OS, navigate to the /etc/fstab file in the installed OS partition and open it in a text editor.

The first command will show us the UUIDs of all partitions on the hard disk, and the second will show the content of the /etc/fstab file; I think you will need to edit the fstab file to show the correct UUIDs and all should then be OK, but show us the output first and we'll go from there.

---

### Post by bijaydeyp on 2016-03-11
first of all thanks for the reply

"Can you still boot to Windows 7? "
the answer is NO.

here it is ....

```
ubuntu@ubuntu:~$ sudo blkid -c /dev/null
/dev/loop0: UUID="429bb98c-85d5-264d-be07-07f25f8c6e87" TYPE="ext2" 
/dev/loop1: TYPE="squashfs" 
/dev/sda1: LABEL="System Reserved" UUID="F2622FA6622F6F13" TYPE="ntfs" 
/dev/sda2: LABEL="Windows" UUID="FE703488703449A3" TYPE="ntfs" 
/dev/sda5: LABEL="Linux Root" UUID="43a7f190-bf6c-424d-9a56-0ec4ff8e5a25" TYPE="ext4" 
/dev/sda6: LABEL="Linux Swap" UUID="b875a17d-3198-45b1-8552-c68d38aafb02" TYPE="swap" 
/dev/sda7: LABEL="Common Drive" UUID="497AEF676E60A5A7" TYPE="ntfs" 
/dev/sdb1: LABEL="IT'S FOR U" UUID="7C82-353B" TYPE="vfat" 
ubuntu@ubuntu:~$ cat /media/ubuntu/
cat: /media/ubuntu/: Is a directory
ubuntu@ubuntu:~$ 
```

"If you prefer a GUI you can use the file-manager in the live OS, navigate to the /etc/fstab file in the installed OS partition and open it in a text editor."
 i can see the (fstab.d) folder but cannot see the file. & my /home directory is not encrypted.

---

### Post by ajgreeny on 2016-03-11
Sorry but I must have had a "big-fat-finger" moment when I wrote my post above and added code tags in the wrong place instead of making the words "root-partition" italic.  I have now edited that post showing the correct second command to use.

If you can show the content of the /etc/fstab file in the installed OS which you can get to by making sure that root partition is mounted in the live OS by clicking on the appropriate device which will show in the left hand panel of the file-manager.  I do not know how it will show the partition as I do not use nautilus or Ubuntu, but it may show as its label, ie, **Linux Root**.

Copy back here the content of that fstab file and I can have a look and see if I can help get Ubuntu to boot.  I will not be able to help much with your Windows problem, I'm afraid, as I haven't used Windows for about 10 years or more.

---

### Post by bijaydeyp on 2016-03-12
thank you, again
to be honest, I am new to linux world and you are a senior forum member. that's why I think you are the right person to ask for help.

the terminal shows this.........

```
ubuntu@ubuntu:~$ sudo blkid -c /dev/null
/dev/loop0: UUID="429bb98c-85d5-264d-be07-07f25f8c6e87" TYPE="ext2" 
/dev/loop1: TYPE="squashfs" 
/dev/sda1: LABEL="System Reserved" UUID="F2622FA6622F6F13" TYPE="ntfs" 
/dev/sda2: LABEL="Windows" UUID="FE703488703449A3" TYPE="ntfs" 
/dev/sda5: LABEL="Linux Root" UUID="43a7f190-bf6c-424d-9a56-0ec4ff8e5a25" TYPE="ext4" 
/dev/sda6: LABEL="Linux Swap" UUID="b875a17d-3198-45b1-8552-c68d38aafb02" TYPE="swap" 
/dev/sda7: LABEL="Common Drive" UUID="497AEF676E60A5A7" TYPE="ntfs" 
/dev/sdb1: LABEL="IT'S FOR U" UUID="7C82-353B" TYPE="vfat" 
ubuntu@ubuntu:~$ cat /media/ubuntu/"Linux Root"/etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=43a7f190-bf6c-424d-9a56-0ec4ff8e5a25 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=b875a17d-3198-45b1-8552-c68d38aafb02 none            swap    sw              0       0
ubuntu@ubuntu:~$
```

---

### Post by ajgreeny on 2016-03-12
Well apart from the fact that fstab shows the root partition as /dev/sda6 and swap as /dev/sda7 there is nothing faulty about your fstab file and the UUIDs are both correct for root and swap; those two /dev/sda# lines are merely comments and not acted upon as they both start with #.

The only thing I can now suggest is that you look at **Boot-Repair** in my signature below and try running the Boot-Info script from that.

---

### Post by bijaydeyp on 2016-03-13
thanks a lot for your help. [COLOR=#C61919]**ajgreeny**[/COLOR]

---

### Post by bijaydeyp on 2016-03-13
today I reinstalled ubuntu on a different partition & restored that files which were on old /home folder.for others with similar issue can check this [http://www.supergrubdisk.org/2015/01/02/rescatux-0-32b3-tutorial/](http://www.supergrubdisk.org/2015/01/02/rescatux-0-32b3-tutorial/) and [http://youtu.be/dGA8e_A2PeA?t=9m](http://youtu.be/dGA8e_A2PeA?t=9m)

---

