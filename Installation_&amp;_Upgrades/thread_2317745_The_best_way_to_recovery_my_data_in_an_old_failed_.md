---
title: "The best way to recovery my data in an old failed ubuntu"
date: 2016-03-19
forum: Installation &amp; Upgrades
---

### Post by v6rg2 on 2016-03-19
I had problem with my ubuntu and could not enter. So I made a bootable usb and now I am on a live ubuntu (15.10).
I want to install it but I have some data on my hard and want to save it. 
How could I get permission?

---

### Post by sudodus on 2016-03-19
This is something you will do only once, so you need not set up a perfect environment in the live system.

- Have you mounted the partition with your data? In that case maybe it is mounted with read permissions only for root (the superuser), not for your regular user.

Either you change the mounting so that your regular user will get permissions, or you save the file with a tool, that runs with root permissions. 

- Do you need help with mounting the partition with your data?

- Do you want a graphical user interface, or can you use terminal window commands for saving the files?

***cp*** and ***rsync*** are good command line tools

```
sudo cp ...
#or
sudo rsync ...
```

***nautilus*** is the file browser of standard Ubuntu. Graphical programs should be run it with ***gksudo*** (or sudo -H) to avoid overwriting your configuration files with root permissions.

```
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install gksu

gksudo nautilus &
```

---

### Post by v6rg2 on 2016-03-19
> **sudodus said:**
> This is something you will do only once, so you  need not set up a perfect environment in the live system.

***nautilus*** is the file browser of standard Ubuntu. Graphical programs should be run it with ***gksudo*** (or sudo -H) to avoid overwriting your configuration files with root permissions.

```
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install gksu

gksudo nautilus &
```


I installed gksudo and then type gksudo in terminal, then in a  run program small window, I ran nautilus (as root) and now I can go to  thatdirectory but it's changed!
There is onlytwo files: 1. Access-your-private-data.desktop 2. README.txt
I'm confused!
Yes, I need help with mounting the partition with my data in a

---

### Post by sudodus on 2016-03-19
Please close nautilus and the other windows, where you have root permissions. This is to reduce the risk of destroying important files while you try to do other things than copying files.

In order to know what you should mount and how to mount it, please run the following commands

```
df

sudo lsblk -fm
```

and post the output in a reply.

Indicate if possible which partition to mount - from where you want to recover the files :-)

---

### Post by v6rg2 on 2016-03-19
```
ubuntu@ubuntu:~$ df
Filesystem     1K-blocks      Used Available Use% Mounted on
udev             1903124         0   1903124   0% /dev
tmpfs             383204     11140    372064   3% /run
/dev/sdb         1150768   1150768         0 100% /cdrom
/dev/loop0       1104256   1104256         0 100% /rofs
/cow             1916008    205848   1710160  11% /
tmpfs            1916008        84   1915924   1% /dev/shm
tmpfs               5120         8      5112   1% /run/lock
tmpfs            1916008         0   1916008   0% /sys/fs/cgroup
tmpfs            1916008      1180   1914828   1% /tmp
cgmfs                100         0       100   0% /run/cgmanager/fs
tmpfs             383204       104    383100   1% /run/user/999
/dev/sda3      450077384 369751148  57440556  87% /media/ubuntu/225daffb-5688-45e9-a1bb-dc997b1b32eb
ubuntu@ubuntu:~$ sudo lsblk -fm
NAME   FSTYPE   LABEL    UUID                                 MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                                                                      sda    465.8G root  disk  brw-rw----
&#9500;&#9472;sda1                                                                   &#9500;&#9472;sda1   5.7G root  disk  brw-rw----
&#9500;&#9472;sda2 ext4              c83538d0-4c3e-4e4c-b116-2e26e2019e0c            &#9500;&#9472;sda2  23.9G root  disk  brw-rw----
&#9492;&#9472;sda3 ext4              225daffb-5688-45e9-a1bb-dc997b1b32eb /media/ubu &#9492;&#9472;sda3 436.2G root  disk  brw-rw----
sdb    iso9660  Ubuntu 15.10 amd64
&#9474;                        2015-10-21-16-17-40-00                          sdb     14.6G root  disk  brw-rw----
&#9500;&#9472;sdb1 iso9660  Ubuntu 15.10 amd64
&#9474;                        2015-10-21-16-17-40-00                          &#9500;&#9472;sdb1   1.1G root  disk  brw-rw----
&#9492;&#9472;sdb2 vfat     Ubuntu 15.10 amd64
                         99B5-7FC8                                       &#9492;&#9472;sdb2   2.2M root  disk  brw-rw----
loop0  squashfs                                               /rofs      loop0    1.1G root  disk  brw-rw----
ubuntu@ubuntu:~$ 

```

---

### Post by sudodus on 2016-03-19
**/dev/sda3** is mounted on **/media/ubuntu/225daffb-5688-45e9-a1bb-dc997b1b32eb**

What can you see on that partition? Only two files?

> There is only two files: 1. Access-your-private-data.desktop 2. README.txt

This is the big partition with 436.2 Gibibytes. What do you expect to find there?

What do you expect to find in the other ext4 partition, **/dev/sda2** ?

And what do you expect to find in the first partition, where ***lsblk*** finds no file system, **/dev/sda1** - Is it or should it be a swap partition?

You can mount the other ext4 partition with the following command,

```
sudo mount /dev/sda2 /mnt
```

***Edit:***  You find its content if you browse to '**Computer**' and then **mnt** with Nautilus:

```
gksudo nautilus &
```

Run it as one single command line (including the & character to release the terminal window).

---

### Post by v6rg2 on 2016-03-19
I expect to find 436.2 files and folders in **sda3**. But when I open it with **sudo nautilus**, I find just two files that are 108 bytes! 
And I dont know about other partitions. look at the picture (attached). That's all of my partitions after **sudo nautilus**.

---

### Post by sudodus on 2016-03-19
1. Is the /dev/sda3 partition encrypted? What is the content of the two files?

2. Please post the output of the following command

```
sudo ls -la /media/ubuntu/225daffb-5688-45e9-a1bb-dc997b1b32eb
```

and what will the following command show (maybe too much to post)?

```
sudo find /media/ubuntu/225daffb-5688-45e9-a1bb-dc997b1b32eb
```

3. Please mount /**dev/sda2** and check what you find there!

---

### Post by v6rg2 on 2016-03-19
1. You can see this two files in picture (attached). 
2. 
```
sudo ls -la /media/ubuntu/225daffb-5688-45e9-a1bb-dc997b1b32eb
total 28
drwxr-xr-x  5 root root  4096 Jan 17  2015 .
drwxr-x---+ 3 root root    60 Mar 19 12:46 ..
dr-x------  2 1000 1000  4096 Jan 17  2015 amir
drwxr-xr-x  3 root root  4096 Jan 17  2015 .ecryptfs
drwx------  2 root root 16384 Jan 17  2015 lost+found


```

second one is too much to post.

3. PHow to mount /**dev/sda2**?  (Sorry. I am beginner. :redface:)

---

### Post by oldfred on 2016-03-19
I do not know encryption, and you have to mount and get it to ask for the pass phrase.


If just /home and you click on the Access-your-private-data.desktop does it then ask for password?


If full partition encryption which uses LUKS, not just /home encryption.
 To get Ubuntu to see different encrypted install, example is sdb2, use your encrypted partition:
sudo apt-get update && sudo apt-get install lvm2 cryptsetup
sudo modprobe dm-crypt
sudo cryptsetup luksOpen /dev/sdb2 my-crypt
sudo os-prober
sudo update-grub

---

### Post by sudodus on 2016-03-19
> **v6rg2 said:**
> 1. You can see this two files in picture (attached). 
2. 
```
sudo ls -la /media/ubuntu/225daffb-5688-45e9-a1bb-dc997b1b32eb
total 28
drwxr-xr-x  5 root root  4096 Jan 17  2015 .
drwxr-x---+ 3 root root    60 Mar 19 12:46 ..
dr-x------  2 1000 1000  4096 Jan 17  2015 amir
drwxr-xr-x  3 root root  4096 Jan 17  2015 .ecryptfs
drwx------  2 root root 16384 Jan 17  2015 lost+found


```

second one is too much to post.

3. PHow to mount /**dev/sda2**?  (Sorry. I am beginner. :redface:)

Encryption as I suspected, encrypted with ecryptfs.

You need your password/passphrase to decrypt it.

[SIZE=3]***Edit:*** I suggest that you browse the internet for ***ecryptfs tutorial*** and learn to decrypt it.[/SIZE]

-o-

Use the command line in post #6 to mount it

```
sudo mount /dev/sda2 /mnt
```

---

### Post by sudodus on 2016-03-19
*oldfred*, maybe you can help *v6rg2* to repair the encrypted system. If that works, it will probably be easier than to decrypt it 'from the outside'.

---

### Post by oldfred on 2016-03-19
I have seen posts on repairing LVM encrypted partitions, not not just a /home.
Not sure if standard fsck works or not?
Part of reason why any encryption requires really good regular backups as repair/recovery can be very difficult or is just impossible.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by v6rg2 on 2016-03-19
> **oldfred said:**
> I do not know encryption, and you have to mount and get it to ask for the pass phrase.


If just /home and you click on the Access-your-private-data.desktop does it then ask for password?


If full partition encryption which uses LUKS, not just /home encryption.
 To get Ubuntu to see different encrypted install, example is sdb2, use your encrypted partition:
sudo apt-get update && sudo apt-get install lvm2 cryptsetup
sudo modprobe dm-crypt
sudo cryptsetup luksOpen /dev/sdb2 my-crypt
sudo os-prober
sudo update-grub

Clicked on Acess-your-private-data.desktop and open a terminal and close instantly.
And for these codes:

```
sudo modprobe dm-crypt
ubuntu@ubuntu:~$  sudo cryptsetup luksOpen /dev/sdb2 my-crypt
Device /dev/sdb2 is not a valid LUKS device.
ubuntu@ubuntu:~$  sudo cryptsetup luksOpen /dev/sdb2 my-crypt
Device /dev/sdb2 is not a valid LUKS device.
ubuntu@ubuntu:~$  sudo os-prober
/dev/sda2:Ubuntu 14.04.3 LTS (14.04):Ubuntu:linux
grub-probe: error: cannot find a GRUB drive for /dev/sdb1.  Check your device.map.


```

---

### Post by v6rg2 on 2016-03-19
> **oldfred said:**
> I 
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

```
ubuntu@ubuntu:~$  sudo e2fsck -C0 -p -f -v /dev/sda3
/dev/sda3 is mounted.
e2fsck: Cannot continue, aborting.


ubuntu@ubuntu:~$  sudo e2fsck -f -y -v /dev/sda3
e2fsck 1.42.12 (29-Aug-2014)
/dev/sda3 is mounted.
e2fsck: Cannot continue, aborting.


ubuntu@ubuntu:~$ 


```

---

### Post by sudodus on 2016-03-19
You must unmount the partitions before running e2fsck on them.

```
sudo umount /dev/sda3 /dev/sda2
```

---

### Post by v6rg2 on 2016-03-20
> **sudodus said:**
> You must unmount the partitions before running e2fsck on them.

```
sudo umount /dev/sda3 /dev/sda2
```

```
ubuntu@ubuntu:~$ sudo umount /dev/sda3 /dev/sda3
umount: /dev/sda3: not mounted
umount: /dev/sda3: not mounted
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda3
                                                                               
      209344 inodes used (0.73%, out of 28590080)
       17667 non-contiguous files (8.4%)
         239 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 208755/577
    94264937 blocks used (82.44%, out of 114346496)
           0 bad blocks
           5 large files

      199966 regular files
        9328 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
          41 symbolic links (4 fast symbolic links)
           0 sockets
------------
      209335 files
```




```
ubuntu@ubuntu:~$ sudo umount /dev/sda3 /dev/sda3
umount: /dev/sda3: not mounted
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda3
e2fsck 1.42.12 (29-Aug-2014)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      209344 inodes used (0.73%, out of 28590080)
       17667 non-contiguous files (8.4%)
         239 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 208755/577
    94264937 blocks used (82.44%, out of 114346496)
           0 bad blocks
           5 large files

      199966 regular files
        9328 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
          41 symbolic links (4 fast symbolic links)
           0 sockets
------------
      209335 files
ubuntu@ubuntu:~$ 

```


What should I do now?

---

### Post by oldfred on 2016-03-20
Are you able to open it?
When you click on it, it should ask for passphrase and open.

---

### Post by v6rg2 on 2016-03-20
> **oldfred said:**
> Are you able to open it?
When you click on it, it should ask for passphrase and open.

I entered this code:
```
sudo e2fsck -C0 -p -f -v /dev/sda3
```

This is result:
```
sudo e2fsck -C0 -p -f -v /dev/sda3
                                                                               
      209344 inodes used (0.73%, out of 28590080)
       17667 non-contiguous files (8.4%)
         239 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 208755/577
    94264937 blocks used (82.44%, out of 114346496)
           0 bad blocks
           5 large files

      199966 regular files
        9328 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
          41 symbolic links (4 fast symbolic links)
           0 sockets
------------
      209335 files


```

And then enter this:

```
sudo nautilus
```

In file manager there is no option to chice that partition. Thta is removed from left sidebar!

I closed terminal and nautilus and again typed these:

```
ubuntu@ubuntu:~$ sudo umount /dev/sda3 /dev/sda3
umount: /dev/sda3: not mounted
umount: /dev/sda3: not mounted
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda3
e2fsck 1.42.12 (29-Aug-2014)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      209344 inodes used (0.73%, out of 28590080)
       17667 non-contiguous files (8.4%)
         239 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 208755/577
    94264937 blocks used (82.44%, out of 114346496)
           0 bad blocks
           5 large files

      199966 regular files
        9328 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
          41 symbolic links (4 fast symbolic links)
           0 sockets
------------
      209335 files
ubuntu@ubuntu:~$ sudo nautilus

(nautilus:5457): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(nautilus:5457): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nautilus:5457): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANC
```


And again there is no option for that partition.

---

### Post by oldfred on 2016-03-20
You should only need to run the fsck once, it is not like Windows where you may have to run chkdsk multiple times to clear all errors.

Can you open encrypted file?

---

### Post by v6rg2 on 2016-03-20
> **oldfred said:**
> You should only need to run the fsck once, it is not like Windows where you may have to run chkdsk multiple times to clear all errors.

Can you open encrypted file?

No I cant. :(
As I said, the option in sidebar for sda3 partition is vanished after run fsck.

---

### Post by oldfred on 2016-03-20
Post this:
sudo parted -l

---

### Post by sudodus on 2016-03-20
I think you need to ***mount*** the partition again to see its content.

---

### Post by v6rg2 on 2016-03-20
> **oldfred said:**
> Post this:
sudo parted -l

```
sudo parted -l 
Model: ATA ST9500325AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  6144MB  6143MB
 2      6144MB  31.7GB  25.6GB  ext4
 3      31.7GB  500GB   468GB   ext4


Warning: The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 512 bytes.
Ignore/Cancel? 

```

---

### Post by v6rg2 on 2016-03-20
> **sudodus said:**
> I think you need to ***mount*** the partition again to see its content.


:o
I am so confused now!

Could you please explain how should I do step by step?

---

### Post by sudodus on 2016-03-20
Mounting is described in post #6 and post #11.

Mount each of the partitions separately, first sda2

```
sudo mount /dev/sda[COLOR="#cc0000"]**2**[/COLOR] /mnt
```

Browse to /mnt and look at the content.2

Unmount

```
sudo umount /mnt
```

and mount the other ext4 partiiton sda3

```
sudo mount /dev/sda[COLOR="#cc0000"]**3**[/COLOR] /mnt
```

Browse to /mnt and look at the content.

---

### Post by v6rg2 on 2016-03-20
```
sudo mount /dev/sda2 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
ubuntu@ubuntu:~$ cd /mnt
ubuntu@ubuntu:/mnt$ ls
amir  lost+found
ubuntu@ubuntu:/mnt$ sudo nautilus

(nautilus:5771): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(nautilus:5771): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nautilus:5771): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
ubuntu@ubuntu:/mnt
```

In graphical file manager I searched amir directory and again there is two files (README.txt and Private...)

---

### Post by v6rg2 on 2016-03-20
And same for sda3:

```
sudo mount /dev/sda3 /mnt
mount: /dev/sda3 is already mounted or /mnt busy
       /dev/sda3 is already mounted on /mnt
ubuntu@ubuntu:~$ gksudo nautilus &
[1] 6387


```

---

### Post by sudodus on 2016-03-20
You should ***unmount*** /mnt before mounting the new partition to it. See post #26

---

### Post by sudodus on 2016-03-20
> **v6rg2 said:**
> ```
sudo mount /dev/sda2 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
ubuntu@ubuntu:~$ cd /mnt
ubuntu@ubuntu:/mnt$ ls
amir  lost+found
ubuntu@ubuntu:/mnt$ sudo nautilus

(nautilus:5771): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(nautilus:5771): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nautilus:5771): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
ubuntu@ubuntu:/mnt
```

In graphical file manager I searched amir directory and again there is two files (README.txt and Private...)

It seems this file system on /dev/sda2 is damaged (cannot be mounted).

---

### Post by sudodus on 2016-03-20
I think /dev/sda3 should be fine now, possible to mount and look at with nautilus. Please try to open it according to *oldfred*'s suggestion in post #18

***Edit:*** Run ```
df
``` to find what is preventing the mounting! Maybe /dev/sda3 is automounted again?

---

### Post by v6rg2 on 2016-03-20
> **sudodus said:**
> You should ***unmount*** /mnt before mounting the new partition to it. See post #26

I am not familiar with terminal commands. How to browse /mnt and how to unmount it?
And now that data may be damaged, what should I do?    :|

---

### Post by sudodus on 2016-03-20
1. Run ```
df
``` and post the output.

2. Depending on what we see, maybe unmount and mount /dev/sda3 according to post #26 (the two last command lines in post #26)

---

### Post by v6rg2 on 2016-03-20
> **sudodus said:**
> 1. Run ```
df
``` and post the output.

2. Depending on what we see, maybe unmount and mount /dev/sda3 according to post #26 (the two last command lines in post #26)


```
df
Filesystem     1K-blocks      Used Available Use% Mounted on
udev             1903124         0   1903124   0% /dev
tmpfs             383204     11132    372072   3% /run
/dev/sdb         1150768   1150768         0 100% /cdrom
/dev/loop0       1104256   1104256         0 100% /rofs
/cow             1916008    212016   1703992  12% /
tmpfs            1916008        84   1915924   1% /dev/shm
tmpfs               5120         8      5112   1% /run/lock
tmpfs            1916008         0   1916008   0% /sys/fs/cgroup
tmpfs            1916008      1172   1914836   1% /tmp
cgmfs                100         0       100   0% /run/cgmanager/fs
tmpfs             383204       108    383096   1% /run/user/999
/dev/sda3      450077384 369751148  57440556  87% /mnt


```

What we see?  :D

---

### Post by sudodus on 2016-03-20
You have succeeded to mount /dev/sda3 to /mnt :-D

Now you can run ```
gksudo nautilus &
``` again and browse to /mnt ('Computer' and 'mnt'), select 'view hidden files' and try to doubleclick on whatever files you see. Will it work like oldfred suggests in post #18, (it should ask for passphrase and open)?

-o-

It is getting late here, and I will soon leave the keyboard for tonight, but I hope there will be other people (from other timezones), who can help you.

Good luck :-)

---

### Post by v6rg2 on 2016-03-20
Thanks a lot.
But in this directory there is no my files. look at the pictures I taked from my fle manager.

---

### Post by oldfred on 2016-03-20
I do not know which file you open for an encrypted /home. But when you click on one or the other it should be asking for a passphrase. 
If it is not asking for it, do you have the software for encryption?
Or do you not know passphase?

More info:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Mount_Passphrase](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Mount_Passphrase)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

---

### Post by sudodus on 2016-03-21
Those files belong to the encrypted system. ***Try double-clicking on them***. If still no luck,

- try again too boot into the installed (and encrypted) Ubuntu system (now that you have repaired the file system)

- browse the internet for ***ecryptfs tutorial*** and read the links, where you can find useful information - I think you will find valuable tips how to decrypt your files, but as *oldfred* says, you need your password/passphrase.

---

### Post by v6rg2 on 2016-03-21
But when you click on one or the other it should be asking for a passphrase.
&#1617;I clicked on **Access-your-private-data.desktop** and asked nothing! 
(Also I know just a password of my dead UBUNTU and dont know anything about **passphrase**)
If there is one way to recovery my fies from that partition please help me. I am a beginner in Linux and dont familiar with comands.  :|

---

### Post by sudodus on 2016-03-21
Did you read any tutorial about ecryptfs? Was it too much?

I know - recovering an encrypted system is difficult, but it should be possible. I have seen threads here at the Ubuntu Forums about it (but I have never done it myself, I have only tested installing encrypted systems).

Search for threads about encrypted home and ecryptfs in the [security sub-forum](http://ubuntuforums.org/forumdisplay.php?f=338) and via [Advanced Search](http://ubuntuforums.org/search.php?search_type=1)

[B]See this link: [[SOLVED] How can I mount a backup of an encrypted home folder?](http://ubuntuforums.org/showthread.php?t=2311227)
[/B]
and this link: [http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

---

