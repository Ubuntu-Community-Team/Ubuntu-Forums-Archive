---
title: "Grub Error 21"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by lorenzodeangeli on 2008-11-07
Hello everybody,

I tried to install Ubuntu on my computer by an external CD which I had previously burnt following the instructions I found on the Ubuntu website.

I was succesfull in the installation, but as I restarted i cannot access neither Ubuntu or Windows XP. It says Grub Error 21. 

Do you have any suggestions to give?

Thanx

Lorenzo

---

### Post by klytu on 2008-11-07
> **lorenzodeangeli said:**
> Hello everybody,

I tried to install Ubuntu on my computer by an external CD which I had previously burnt following the instructions I found on the Ubuntu website.

I was succesfull in the installation, but as I restarted i cannot access neither Ubuntu or Windows XP. It says Grub Error 21. 

Do you have any suggestions to give?

Thanx

Lorenzo

If you installed from a LiveCD, you can try reinstalling GRUB. There are detailed instructions here: 

[http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck](http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck)

and here as well:

[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by lorenzodeangeli on 2008-11-07
alright, I followed the instructions but thats what happens>

sudo mount -t ext3 /dev/sda6 /mnt/root
mount> special device /dev/sda6 does not exist

Do you have any ideas

---

### Post by caljohnsmith on 2008-11-07
When you restart your computer, do you see a message similar to "press ESC to see menu"? If yes, press ESC to get the Grub menu. If not, then how about booting your Live CD, opening a terminal (Applications > Accessories > Terminal) and doing:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands, and also post the output of:
```
sudo fdisk -lu
```
Reboot, and let me know if you still get the Grub error 21.

---

### Post by lorenzodeangeli on 2008-11-07
When i restart my computer I dont see anything like Press Esc to see Menu, just Grub Error 21..

i opened a terminal and typed one of the two commands you suggested, find /boot/grub/stage1 or find /grub/stage1, it doesn-t go through, just says

Error 15 File not found

Any idea what to do?

---

### Post by caljohnsmith on 2008-11-07
How about first posting:
```
sudo fdisk -lu
```
And we can work from there.

---

### Post by lorenzodeangeli on 2008-11-07
it says

unable to open /lu

---

### Post by lorenzodeangeli on 2008-11-07
sorry, i was wrong,here-s what it says

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6180a8e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    14651279     7325608+   7  HPFS/NTFS
/dev/sda3        73256400   156296384    41519992+   f  W95 Ext'd (LBA)
/dev/sda5        73256463   156296384    41519961    7  HPFS/NTFS

---

### Post by caljohnsmith on 2008-11-07
Your 80 GB sda drive only has NTFS partitions on it, no Linux partitions. Did you install Ubuntu inside Windows? Do you have another drive besides the 80 GB sda drive that maybe has Ubuntu on it? Please explain the steps you took to install Ubuntu.

---

### Post by lorenzodeangeli on 2008-11-07
i dowloaded the file from the Ubuntu website, and saved it on my desktop, I have Windows XP.

Then I downloaded a program, suggested by Ubuntu, to burn the file on an external cd. I then entered the CD and tried Ubuntu without installing it at first. Then, I installed it following the guided procedure. It said it would have partitioned the disk into two parts, 50% for Windows, 50% for Ubuntu. At the end of the installation, I chose my username and password, then restarted the computer, and saw the error..

do you need more detailed explanation or is that clear_

---

### Post by lorenzodeangeli on 2008-11-07
actually a friend of mine did something more, i think he entered the partition editor and might have erased something...

---

### Post by caljohnsmith on 2008-11-07
OK, how about posting:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
sudo mkdir /mnt/sda1 /mnt/sda5
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda5 /mnt/sda5
ls -l /mnt/sda1 /mnt/sda5
```
And you only have the one 80 GB HDD?

---

### Post by lorenzodeangeli on 2008-11-07
/mnt/sda1:
total 4297415
-rwxrwxrwx 1 root root     45056 2005-01-27 10:48 autorun.exe
-rwxrwxrwx 1 root root        49 2002-06-08 05:18 Autorun.inf
-rwxrwxrwx 1 root root      2048 2004-08-04 12:00 ETFSBOOT.COM
drwxrwxrwx 1 root root      4096 2004-09-17 07:31 Minint
-rwxrwxrwx 1 root root     47564 2004-08-04 12:00 ntdetect.com
-rwxrwxrwx 1 root root    260272 2004-08-04 12:00 ntldr
drwxrwxrwx 1 root root         0 2005-03-23 20:24 RCD_CSTM
-rwxrwxrwx 1 root root  45780898 2004-09-17 07:34 RCVPRT.img
-rwxrwxrwx 1 root root      2626 2005-03-14 06:31 SNYHDRCV.INI
drwxrwxrwx 1 root root      4096 2005-03-23 20:24 Sony
-rwxrwxrwx 1 root root 503419049 2005-03-11 07:34 Sony2.pac
-rwxrwxrwx 1 root root 441832451 2005-03-11 07:36 Sony3.pac
-rwxrwxrwx 1 root root 328133199 2005-03-11 07:29 Sony4.pac
-rwxrwxrwx 1 root root 387268627 2005-03-11 07:30 Sony5.pac
-rwxrwxrwx 1 root root    530217 2004-04-22 09:01 SonydNT.img
-rwxrwxrwx 1 root root 671103458 2005-03-14 05:33 sony.i01
-rwxrwxrwx 1 root root 671139071 2005-03-14 05:36 sony.i02
-rwxrwxrwx 1 root root 231786412 2005-03-14 05:38 sony.i03
-rwxrwxrwx 1 root root 492849807 2005-03-14 05:38 sony.img
-rwxrwxrwx 1 root root 626309267 2005-03-11 07:34 Sony.pac
drwxrwxrwx 1 root root         0 2005-03-23 20:24 SUPPORT
drwxrwxrwx 1 root root         0 2005-03-23 20:25 VAIO Applications
drwxrwxrwx 1 root root         0 2005-03-23 20:25 VALUEADD
-rwxrwxrwx 1 root root        10 2004-08-04 12:00 WIN51
-rwxrwxrwx 1 root root        10 2004-08-04 12:00 WIN51IP
-rwxrwxrwx 1 root root        10 2004-08-04 12:00 WIN51IP.SP2
-rwxrwxrwx 1 root root       167 2002-08-29 12:00 winbom.ini

/mnt/sda5:
total 308
drwxrwxrwx 1 root root      0 2005-09-26 18:03 Contenuti
drwxrwxrwx 1 root root   4096 2008-10-28 18:57 Docs Lorenzo
drwxrwxrwx 1 root root  40960 2008-11-06 17:45 downloads
drwxrwxrwx 1 root root  28672 2008-11-06 17:54 Fotolorenzo
drwxrwxrwx 1 root root 237568 2008-11-06 19:02 Musica
drwxrwxrwx 1 root root      0 2005-09-26 16:16 RECYCLER
drwxrwxrwx 1 root root   4096 2005-09-26 15:47 System Volume Information
drwxrwxrwx 1 root root      0 2005-09-26 18:03 VAIO Entertainment

yes, only the 80 GB HDD. but i have an external one if needed

---

### Post by caljohnsmith on 2008-11-07
It would help if you would also post the output of those dd commands so I can get an idea of how Grub is installed on your HDD. According to what you posted, it looks like sda1 is a Windows recovery partition, and sda5 is your documents and files. There is a large unused amount of space between sda1 and sda5 though, over 30 GB. That may be where your lost Windows partition is. I have no idea what happened during your installation, but it looks like your Windows partition is gone, and there are no linux partitions. If you want to try and recover your Windows partition, you could use "testdisk". First post the output of:
```
sudo fdisk -l
```
Then make sure the Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "proceed", Y/N depending on if you have any Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. Post the output of that screen if you would like help recovering your Windows partition.

---

### Post by CMR_98823 on 2008-11-07
Post Removed. Sorry 'bout that.

---

### Post by meierfra. on 2008-11-08
CMR_98823:  Do you  get the grub errors before the grub menu appears? Or after you select Ubuntu at the grub menu. Post  "sudo fdisk -l" and "menu.lst".  But please respond  in your own thread. You shouldn't interrupt other threads, while people are waiting for  your response in your own thread.

---

### Post by lorenzodeangeli on 2008-11-08
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6180a8e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         912     7325608+   7  HPFS/NTFS
/dev/sda3            4561        9729    41519992+   f  W95 Ext'd (LBA)
/dev/sda5            4561        9729    41519961    7  HPFS/NTFS

---

### Post by lorenzodeangeli on 2008-11-08
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1   911 254 63   14651217 [Recovery Partiti
 3 E extended LBA          4560   0  1  9728 254 63   83039985
 5 L HPFS - NTFS           4560   1  1  9728 254 63   83039922 [VAIO]











*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Quick Search]  [ Backup ]
                            Try to locate partition

---

### Post by lorenzodeangeli on 2008-11-08
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1   911 254 63   14651217 [Recovery Partition]
D FAT32 LBA              765   1  1  9728 254 63  144006597 [NO NAME]
D HPFS - NTFS            912   0  1  4559 254 63   58605120 [VAIO]
D HPFS - NTFS           4560   1  1  9728 254 63   83039922 [VAIO]









Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 7501 MB / 7153 MiB

---

### Post by lorenzodeangeli on 2008-11-08
you say It would help if you would also post the output of those dd commands

what do you mean?

sorry if it took me a while

any hope?

---

### Post by caljohnsmith on 2008-11-08
> **lorenzodeangeli said:**
> ```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]P[/COLOR] HPFS - NTFS              0   1  1   911 254 63   14651217 [Recovery Partition]
[COLOR="Red"]D[/COLOR] FAT32 LBA              765   1  1  9728 254 63  144006597 [NO NAME]
[COLOR="Red"]*[/COLOR] HPFS - NTFS            912   0  1  4559 254 63   58605120 [VAIO]
[COLOR="Red"]L[/COLOR] HPFS - NTFS           4560   1  1  9728 254 63   83039922 [VAIO]

Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 7501 MB / 7153 MiB
```
OK, using your up/down arrow keys, select each partition above, then move the right/left arrow keys to mark them as I have above with "P", "D", "*", and "L" as shown. Based on the info you've given, I'm fairly certain the above partition table changes are correct. That last partition though that I have marked as L, it may be that testdisk will only let you mark it with P; that's fine if testdisk won't let you set it as L. 

Once the partitions are marked as shown above, then press "enter" to continue, and you should be presented with some sort of option to write the partition table changes. After written the changes and quit testdisk, then do:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```
Be careful that you get that "dd" command above exactly right, otherwise it could be dangerous. That will restore your Windows MBR so that you should be able to boot directly into Windows. Go ahead and reboot, see if you can boot into Windows OK, and if not, please post the new output of:
```
sudo fdisk -l
```
And we can work from there.

---

### Post by lorenzodeangeli on 2008-11-08
I marked the partitions as you said, it worked. As I quit testdisk, it tells me to reboot for the change to take effect. should i do it or type the code as you said?

if i have to reboot, do i do it by closing the live session and restarting the computer?

---

### Post by caljohnsmith on 2008-11-08
> **lorenzodeangeli said:**
> I marked the partitions as you said, it worked. As I quit testdisk, it tells me to reboot for the change to take effect. should i do it or type the code as you said?

if i have to reboot, do i do it by closing the live session and restarting the computer?
You should go ahead and run those commands I gave, otherwise you won't have any hope of booting into Windows. And yes, to reboot, just choose restart from the live session under System > Shutdown, or the icon in the upper right-corner of your screen.

---

### Post by lorenzodeangeli on 2008-11-08
alright, now i can boot into windows, thanx a lot for the help, it really guided me through..this Ubuntu forum community is really helpful

now what do you suggest, I still want to install Ubuntu but i'm afraid the same thing (or even worse) is going to happen..

---

### Post by caljohnsmith on 2008-11-08
I would suggest looking at Herman's website for a good tutorial on setting up a [dual boot with Ubuntu]("http://www.herman.linuxmaniac.net/p22.html"). I would highly recommend backing up your HDD first as a precaution since you had problems before. I think with Herman's tutorial you should be fine though. Good luck.

---

