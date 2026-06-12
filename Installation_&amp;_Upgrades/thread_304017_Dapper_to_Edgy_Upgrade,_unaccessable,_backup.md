---
title: "Dapper to Edgy Upgrade, unaccessable, backup?"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by babygigi on 2006-11-21
After an upgrade from Dapper to Edgy, i can not log in anymore, it just loops. i've tried other solutions but so far none have worked for me. It seems as if i need to prepare a fresh install, but i have alot of data that i wish not to lose so i was wondering if there is anyway to access my home folder and desktop from a Live CD, i understand u can access the grub file and i have already done so.. but now what? Thank you in advance

---

### Post by srunni on 2006-11-21
Yes, you can access all your data. I suggest you don't use the Ubuntu Live CD though - use Knoppiz [[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)]. It is specifically made for Live CD usage. You will need to either back stuff up to a flash drive or other external storage, or you will need to do it over a network, by uploading files onto another computer. Note: this will require access to another computer. Also, I reccomend making a separate /home partition when you reinstall Ubuntu, as that totally solves this entire problem - since all your data is stored in /home, you can do a clean install for each release and you won't lose any of your data because only the / partition will get reformatted, and your /home partition will just be mounted by the new install. The /home partition will have your documents, pictures, music, program configurations, etc. All you will need to do is reinstall the programs that aren't installed with the default install.

---

### Post by babygigi on 2006-11-21
so exactly how do i do this? if i'm planning on backing things up on say a flash drive... is it possible to burn it onto dvd's or cd's? and is it also possible to use the ubuntu live cd because i am unable to access the knoppix live cd... i've never really done this so i need rather detailed instructions. thanks in advance

---

### Post by bulldog on 2006-11-21
Just boot the live cd.
Make a mount point for your Ubuntu install.
```
sudo mkdir /mnt/rescue
```
If you don't know where Ubuntu is installed
```
sudo fdisk -l  (l as in like)
```
Look where ubuntu is installed for the next command.
Mount your Ubuntu.
```
sudo mount /dev/hd? /mnt/rescue
```hd? stands for the outcome of fdisk.

Now navigate to /mnt/rescue and you see your Ubuntu install.
You can copy it to another hard drive,flash drive or burn it on a cd or DVD.

Goodluck.

---

### Post by babygigi on 2006-11-21
and then when i have my cd... i can boot it up and find all my files there? like things i put into my home file or i had on my desktop under edgy? cuz i've done that before and i just get a bunch of files and a grub and a lost and found folder... what do i do with that?

---

### Post by bulldog on 2006-11-21
Just go to your home folder and select the files you want to keep and copy them to a flash drive.
Or start your burning app and navigate to the /mnt/rescue/home folder and select your data to burn it on a cd-r or a DVD.

You have to boot into the live cd first,then type the mentioned commands in a terminal.
This will mount your existing ubuntu hdd to the rescue folder.

---

### Post by babygigi on 2006-11-21
i get a error msg saying that:
/dev/hda is either mounted or /mnt/rescue is busy

my disk is the one that is under Disk: hda 
rite?

because b4 i used hda1 and all i got was a bunch of grub and lost and foudn folders and files

---

### Post by babygigi on 2006-11-21
this is  my fdisk -l
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 15.0 GB, 15020457984 bytes
255 heads, 63 sectors/track, 1826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          31      248976   83  Linux
/dev/hda2              32        1826    14418337+   5  Extended
/dev/hda5              32        1826    14418306   8e  Linux LVM

and tehn when i try to mount it :
ubuntu@ubuntu:~$ sudo mount /dev/hda /mnt/rescue
mount: /dev/hda already mounted or /mnt/rescue busy

---

### Post by babygigi on 2006-11-22
can anybody help? its soo hard to survive without a working computer! thanks in advance

---

### Post by babygigi on 2006-11-22
anybody please??:(

---

### Post by bulldog on 2006-11-22
When you mount you have to specify a partition.**not the whole hda**
If your Ubuntu is on hda5 you mount hda5 not just hda
Which is your Ubuntu hda1 or hda5?
And where is your swap?

Just make another mountpoint and mount them both.
```
sudo mkdir /mnt/ubuntu
```
Then mount hda1 to rescue and hda5 to ubuntu
Now search for your data and copy it.

Try this and let me know

---

### Post by babygigi on 2006-11-22
okay i did that, and for the hda5, i can not mount it to /mnt/ubuntu because it is either busy or hda5 is already mounted. and for hda1, i do not see my files in there, i'll send a screen shot in a bit. oh and the edgydrive folder is one i created myself, there is nothing in it, ignore it. thank you soo much so far and in advanced

---

### Post by babygigi on 2006-11-22
<rant> nvm i need to upload the picture somewhere... and i dnt' have the time right now =) computer still fustrating me.. </rant>

---

### Post by MJN on 2006-11-23
Stick with it - you'll get there!

Try running **mount** to see what's currently mounted and where... then we'll take it from there.

(Caveat to my assistance though - I've just noticed the partition you're after is presumably hda5 (hda1 is only 250MB) but it's an LVM volume for which I have no experience of (the LVM aspect may or not be relevant - I suspect it is but then what would I know?!)

Mathew

---

### Post by bulldog on 2006-11-23
I suppose your data is in your /home folder,so you must know on which partition your /home is.
That partition you should mount with the live cd,and copy your data to a save place.
Then delete all the partitions on your hard disk and start over again.
I should download the gparted live cd to partition your hard disk manually,you can download it here,

[http://sourceforge.net/projects/gparted/](http://sourceforge.net/projects/gparted/)

Burn it to a disk and boot from it.

Now delete all your partitions so you have a clean empty disk with unallocated space.
Right click the unallocated space and choose create new partition.
Make a swap about 1GB
Make a /  (root)  6GB ext3 file system
Make the rest ext3 for your /home partition.
Apply and if done exit gparted live cd.

Now boot the Ubuntu live cd or the alternate cd.
When you come to the partitioner choose manual partitioning [you already did this with gparted]
Now mount the swap as swap the 6GB as your / ,and mount the last partition as your /home.
Format them [check the boxes] and make the / bootable [flag]
Apply and continue the install of Ubuntu.

Now,if all gets well,you have a separate /home where you can store your data,and when you need to reinstall,don't format your /home so your data will not be deleted,just mount /home as /home again.

This all should work and installing should be a piece of cake.

---

### Post by MJN on 2006-11-23
> **bulldog said:**
> I suppose your data is in your /home folder,so you must know on which partition your /home is.
That partition you should mount with the live cd,and copy your data to a save place.

It's those first bits that the OP really needs helping with at this stage...

---

### Post by bulldog on 2006-11-23
> **MJN said:**
> It's those first bits that the OP really needs helping with at this stage...

Yes I know,read the whole topic please........I have already told him how to mount his partitions with the live cd.
But I can't see which partition he used for his /home,so he has to know.

---

### Post by MJN on 2006-11-23
There are only two data partitions on his disc - hda1 and hda5. The first (ext) is 250MB hence I wouldn't have thought /home is in there, and the second (LVM) is >14.5GB so odds are his /home is somewhere in there.

However, when he's followed your (correct) advice he's having no joy hence we need to find out why (why I suggested the optionless mount command).

I don't believe he can mount his LVM partition in the way you're suggesting. Perhaps you know otherwise (I'm a self-confessed ignorant when it comes to LVM).

Of course, when he's got his data back he can follow your comprehensive instructions but let's do one step at a time!

Mathew :)

---

### Post by babygigi on 2006-11-23
i dnt' quite understand, i can not locate which hda has my /homefolder, it doesn't seem to be on hda1, because the only files i find is the grub folder and other files. and hda5 refuses to mount.

---

### Post by gmunger on 2006-11-23
In your case the devices are /dev/hda1, /dev/hda2, /dev/hda5. It looks like /dev/hda1 is "/boot", /dev/hda5 is "/".
try:
sudo mount /dev/hda5 /mnt/rescue


> **babygigi said:**
> this is  my fdisk -l
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 15.0 GB, 15020457984 bytes
255 heads, 63 sectors/track, 1826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          31      248976   83  Linux
/dev/hda2              32        1826    14418337+   5  Extended
/dev/hda5              32        1826    14418306   8e  Linux LVM

and tehn when i try to mount it :
ubuntu@ubuntu:~$ sudo mount /dev/hda /mnt/rescue
mount: /dev/hda already mounted or /mnt/rescue busy

---

### Post by MJN on 2006-11-23
As I've said, your /home is in one of two physical partitions - hda1 or hda5. hda1 is 250MB hence I can't see it being in here, and hda5 is an LVM volume (Logical Volume Management) and at 14.5GB my money is on it being in there.

Someone with LVM experience needs to step in here... as my money is on the fact that as your hda5 is LVM you can't just mount it in the simple way that we're all used to for physical partitions. I hope for your sakes that this isn't the case.

This does beg the question as to why you've used LVM on your disk but that discussion is something we should have when we're all laughing over a pint once you've recovered your data.

Mathew

---

### Post by MJN on 2006-11-23
Okay, here goes - although the following comes with the caveat that I don't understand LVM (however I do understand Google hence let's not let that matter too much! ;)). One thing I do know though is that you're not going to get very far with the 'normal' mounting methods being suggested to you.

Try running **sh /etc/rd.d/rc.lvm2 start** then **vgscan -v **and finally** lvmdisplay** (as root) - if you get nothing back you need to find a LiveCD that supports LVM. If you do get a response, make a note of the **LV Name**(s) - you will likely get several.

Next, create as many mount points as you have LV Names (e.g. /mnt/lv1, /mnt/lv2 etc) then run **mount <LV Name> <mount point> **(substituting as appropriate).

Finally, cross your fingers and have a look in your mount points...

Any joy?

Mathew

---

### Post by babygigi on 2006-11-23
That is the mount information

ubuntu@ubuntu:~$ mount
unionfs on / type unionfs (rw)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-23-386/volatile type tmpfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)

I am now going to do teh next step, teh one MJN just described.. wish me the  best of luck!

---

### Post by babygigi on 2006-11-23
ubuntu@ubuntu:~$ sh /etc/rd.d/rc.lvm2 start
sh: /etc/rd.d/rc.lvm2: No such file or directory
ubuntu@ubuntu:~$ vgscan -v
  /etc/lvm/.cache: open failed: Permission denied
    Wiping cache of LVM-capable devices
    Wiping internal VG cache
  Reading all physical volumes.  This may take a while...
    Finding all volume groups
  No volume groups found
  /etc/lvm/.cache: fopen failed: Permission denied
ubuntu@ubuntu:~$ sudo lvmdisplay
sudo: lvmdisplay: command not found
 That is the information i got from the last post

---

### Post by babygigi on 2006-11-23
I think this was my problem when i upgraded to edgy
[https://blueprints.launchpad.net/distros/ubuntu/+spec/native-lvm-support](https://blueprints.launchpad.net/distros/ubuntu/+spec/native-lvm-support)

---

### Post by babygigi on 2006-11-23
From searching around i think the Live CD has LVM capabilities, do u think it would work if i just installed lvm2 and lvm-commmon packages onto my hda? i am going to try that now, but it will take a while before i come back! thanks for all the help so far! btw, live CD takes forever to boot but its worth it if its going to save my computer =)

---

### Post by MJN on 2006-11-23
[Message changed having seen your second reply]

Good - try the LiveCD then and, yes, install anything that's got LVM in it's title.

Mathew

P.S. If I ever see that you've used LVM again in a subsequent install then I'll personally hunt you down...

---

### Post by babygigi on 2006-11-23
This is what i have got from the Live CD from version 5.10 
buntu@ubuntu:~$ vgscan -v
  /etc/lvm/.cache: open failed: Permission denied
    Wiping cache of LVM-capable devices
    Wiping internal cache
  Reading all physical volumes.  This may take a while...
    Finding all volume groups
  /dev/hda: open failed: Permission denied
  /dev/loop0: open failed: Permission denied
  /dev/hda1: open failed: Permission denied
  /dev/loop1: open failed: Permission denied
  /dev/hda2: open failed: Permission denied
  /dev/loop2: open failed: Permission denied
  /dev/loop3: open failed: Permission denied
  /dev/loop4: open failed: Permission denied
  /dev/hda5: open failed: Permission denied
  /dev/loop5: open failed: Permission denied
  /dev/loop6: open failed: Permission denied
  /dev/loop7: open failed: Permission denied
  No volume groups found
  /etc/lvm/.cache: fopen failed: Permission denied
ubuntu@ubuntu:~$ sudo lvmdisplay
sudo: lvmdisplay: command not found
ubuntu@ubuntu:~$ sudo vgscan -v
    Wiping cache of LVM-capable devices
    Wiping internal cache
  Reading all physical volumes.  This may take a while...
    Finding all volume groups
    Finding volume group "Ubuntu"
  Found volume group "Ubuntu" using metadata type lvm2
ubuntu@ubuntu:~$ sudo sh /etc/rd.d/rc.lvm2 start
sh: /etc/rd.d/rc.lvm2: No such file or directory

I am going to try with version 5.04 Live CD because i dnt' see any LV names here

---

### Post by MJN on 2006-11-23
That's looking good (forgot to mention to prefix vgscan with sudo) - scrap the rc.d command from now on - this was just to load LVM if the LiveCD didn't already have it running.

Now try **sudo vgdisplay**

Mathew

---

### Post by babygigi on 2006-11-23
root@ubuntu:/home/ubuntu # sudo vgdisplay
  --- Volume group ---
  VG Name               Ubuntu
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               13.75 GB
  PE Size               4.00 MB
  Total PE              3520
  Alloc PE / Size       3520 / 13.75 GB
  Free  PE / Size       0 / 0
  VG UUID               AE17at-YgXP-xBAE-BR3J-Y1i2-SwLn-bV9UcB


that is from 5.04 badger is that the one? or hoary? lol cn't remember well that got back results

---

### Post by MJN on 2006-11-23
Anything more with **sudo vgdisplay -v    **?

---

### Post by MJN on 2006-11-23
And **sudo** **lmdisplay    **?

(sorry for this shotgun approach but it's as good as I can offer)

---

### Post by babygigi on 2006-11-23
root@ubuntu:/home/ubuntu # sudo vgdisplay -v
    Finding all volume groups
    Finding volume group "Ubuntu"
  --- Volume group ---
  VG Name               Ubuntu
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               13.75 GB
  PE Size               4.00 MB
  Total PE              3520
  Alloc PE / Size       3520 / 13.75 GB
  Free  PE / Size       0 / 0
  VG UUID               AE17at-YgXP-xBAE-BR3J-Y1i2-SwLn-bV9UcB

  --- Logical volume ---
  LV Name                /dev/Ubuntu/root
  VG Name                Ubuntu
  LV UUID                l5hvjV-5KjT-W6I9-1vfD-6of7-rZ0J-riVTVV
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                13.16 GB
  Current LE             3368
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:2

  --- Logical volume ---
  LV Name                /dev/Ubuntu/swap_1
  VG Name                Ubuntu
  LV UUID                ROxSTM-74En-LlXU-yQzy-qY1R-qanS-06Zx30
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                608.00 MB
  Current LE             152
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:3

  --- Physical volumes ---
  PV Name               /dev/hda5
  PV UUID               tWpDVF-aqW4-0aSR-l0Cb-bQJR-UNno-mko14O
  PV Status             allocatable
  Total PE / Free PE    3520 / 0

root@ubuntu:/home/ubuntu # sudo lmdisplay
sudo: lmdisplay: command not found

---

### Post by MJN on 2006-11-23
Looking good!

Now try:

mkdir /mnt/test
sudo mount /dev/Ubuntu/root /mnt/test

...(deep breath)...

ls -l /mnt/test

Anything?

Mathew

---

### Post by babygigi on 2006-11-23
root@ubuntu:/home/ubuntu # sudo mkdir /mnt/test
root@ubuntu:/home/ubuntu # sudo mount /dev/ubuntu/root /mnt/test
mount: you must specify the filesystem type

is the file system type LVM? or etc3? and where do i  put it?

---

### Post by babygigi on 2006-11-23
nvm
lol typed it wrong

---

### Post by babygigi on 2006-11-23
root@ubuntu:/home/ubuntu # ls -l /mnt/test
total 160
drwxr-xr-x    2 root root  4096 2006-11-19 21:38 bin
drwxr-xr-x    2 root root  4096 2006-07-21 20:11 boot
lrwxrwxrwx    1 root root    11 2006-07-21 20:11 cdrom -> media/cdrom
drwxr-xr-x    2 root root  4096 2006-07-21 20:18 debootstrap
drwxr-xr-x   14 root root 28672 2006-11-19 21:51 dev
drwxr-xr-x  125 root root  8192 2006-11-23 18:19 etc
drwxr-xr-x    3 root root  4096 2006-07-21 20:37 home
drwxr-xr-x    2 root root  4096 2006-07-21 20:12 initrd
lrwxrwxrwx    1 root root    29 2006-11-19 21:56 initrd.img -> boot/initrd.img-2.6.17-10-386
lrwxrwxrwx    1 root root    29 2006-09-19 12:03 initrd.img.old -> boot/initrd.img-2.6.15-27-386
drwxr-xr-x   22 root root  8192 2006-11-20 17:02 lib
drwxr-xr-x    2 root root 49152 2006-07-21 20:10 lost+found
drwxr-xr-x    5 root root  4096 2006-11-18 02:13 media
drwxr-xr-x    2 root root  4096 2005-10-05 09:37 mnt
drwxr-xr-x    4 root root  4096 2006-11-20 22:50 opt
drwxr-xr-x    2 root root  4096 2005-10-05 09:37 proc
drwxr-xr-x    9 root root  4096 2006-11-23 17:19 root
drwxr-xr-x    2 root root  8192 2006-11-19 21:10 sbin
drwxr-xr-x    2 root root  4096 2006-07-21 20:12 srv
drwxr-xr-x    2 root root  4096 2005-10-09 21:03 sys
drwxrwxrwt    5 root root  4096 2006-11-23 18:19 tmp
prw-r-----    1 root root     0 2006-07-22 02:48 usplash_fifo
drwxr-xr-x   14 root root  4096 2006-11-20 16:41 usr
drwxr-xr-x   16 root root  4096 2006-11-19 20:49 var
lrwxrwxrwx    1 root root    26 2006-11-19 21:56 vmlinuz -> boot/vmlinuz-2.6.17-10-386
lrwxrwxrwx    1 root root    26 2006-09-19 12:03 vmlinuz.old -> boot/vmlinuz-2.6.15-27-386

---

### Post by MJN on 2006-11-23
nvm?

Anyway, you're done - it's all there!

---

### Post by babygigi on 2006-11-23
GOT IT!!! =) thanks soo much!!! okay this should become  a sticky or something. okay now i jsut hope my computer is fast enough to burn everythign to cds =P thanks soo much! oh btw to whom ever it was... i'm a she

---

### Post by babygigi on 2006-11-23
nvm - never mind

---

### Post by MJN on 2006-11-23
> **babygigi said:**
> GOT IT!!! =) thanks soo much!!! okay this should become  a sticky or something. okay now i jsut hope my computer is fast enough to burn everythign to cds =P thanks soo much! oh btw to whom ever it was... i'm a she

Glad to hear it... I think I'm off for a lie down.

Do me a favour won't you, don't ever use LVM again?

Mathew

(P.S. As for being a she.... sorry)

---

### Post by babygigi on 2006-11-23
it is really okay, after all u helped me with i can't be upset. Okay how on earth did i use LVM in the first place is a question to me, but i will figure out how to not in the future, i think Bulldog had a way to not, i will go back to it later~ thank you again

---

