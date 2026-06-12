---
title: "Help:  Broken XP MBR after Ubuntu Install"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by peakay on 2008-02-18
Hi all, Newbie here.

I installed Ubunu last night and need some help establishign dual boto so I can get to Windows XP.  

Here's my scenario:  My system has had 2 40gb hard disks - 1 with only windows xp, the 2nd for data.  After backing up all my data, I installed Ubuntu 7.1 on my 2nd disk as I had plenty of space for it plus my data.

today, I cannot run windows XP.  What I discovered was my windows drive was actually set up in slave position, so * *i think* the windows mbr was probably on the disk i used for ubuntu and is now whacked.

My desired state:  I want to get back to where I can select either xp or ubuntu at startup.  I know you can repair the xp mbr using an xp cd, but can I now write the mbr to the windows drive if the mbr was originally on the master/ubuntu drive?  And, if i try this, might I just whack ubuntu too which is now my only working OS.

Sorry to sound so klutzy here but I am new to Linux and am making a few mistrakes.  :)

---

### Post by Pumalite on 2008-02-18
Post:
sudo fdisk -lu

---

### Post by peakay on 2008-02-18
> **Pumalite said:**
> Post:
sudo fdisk -lu

Thanks Puma.  Can you add just a little more info around this?  Since this problem is potentially coimputer-killng, I want to make sure I know what I'm doing and don't make any more mistakes.

TIA

---

### Post by Pumalite on 2008-02-18
It's just to see your drives and partitions to orient myself to help you. It's a simple command in the Terminal that will not affect your computer at all.

---

### Post by peakay on 2008-02-18
> **Pumalite said:**
> It's just to see your drives and partitions to orient myself to help you. It's a simple command in the Terminal that will not affect your computer at all.

cool..i just don't know enough to understand yet.  here it is below.  sdb is the windows drive, obviously.

isk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9b5d9b5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    15631244     7815591   83  Linux
/dev/sda2        66444840    78156224     5855692+  83  Linux
/dev/sda3        19567170    66444839    23438835    b  W95 FAT32
/dev/sda4        15631245    19567169     1967962+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x358df14f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    80276804    40138371    7  HPFS/NTFS

---

### Post by Pumalite on 2008-02-18
Edit /boot/grub/menu.lst. Backup first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
Then:
gksudo gedit /bootgrub/menu.lst
Add the following below this: ### END DEBIAN AUTOMAGIC KERNELS LIST
title		Windows 
rootnoverify		(hd1,0)
map   (hd0,0) (hd1,0)
map   (hd1,0) (hd0,0)
makeactive
chainloader	+1

Save and exit. Reboot.

---

### Post by peakay on 2008-02-18
thanks.  I did this and it starts booting, but it fails and says ntldr is missing.  

i believe this is because my data disk was setup as master and windows was on the slave drive.  since i installed ubuntu on the (correction: master) drive, i believe it wiped the boot up faciities windows uses.

i *think* i can just use windows xp startup disk and do a fixmbr, but i am afriad it will wipe the ubuntu loader and then both os's will fail.

---

### Post by Pumalite on 2008-02-18
This is because XP is in sdb. It should be in sda. The XP drive should be master and appear as sda.Did you install Windows last?

---

### Post by peakay on 2008-02-18
No, windows has been instaleld for years but what I didn't know was the drive it is on is configured as the slave drive.  I implemented what is outlined here:

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

except that windows was always on the slave drive, not just changed after the ubuntu install.  so i assume i wiped whatever windows needs to boot off the master drive (where ubuntu is now) and even when i make the changed to grub as outlined on the above changes, it fails when i select xindows xp out of grub.

i'm pretty sure i just ned to run the windows xp disk and do a fix mbr on the slave drive, but i'm paranoid about wiping something out.

---

### Post by Pumalite on 2008-02-18
You might want to try this:

Boot Ubuntu Live CD, mount your Windows partition:

sudo mount  -t ntfs-3g  /dev/sda2 /windows

(Here replace sda2 by whatever partition Windows is on)

Copy the first sector of the Ubuntu partition to a file on the Windows partition:

Code:

sudo dd if=/dev/sda3 of=/windows/ubuntu.bin bs=512 count=1

(Be very careful when using "dd". Info on dd)

Add ubuntu to the windows boot loader:

Open "boot.ini" from the Windows partition via
Code:

sudo gedit /windows/boot.ini

Add this line to the end of the file:
c:\ubuntu.bin="Ubuntu"

Save the file.

Reboot and you get should get a menu with a Windows and Ubuntu choice.
__________________

---

### Post by peakay on 2008-02-18
thanks.  between the last and this message, i did try the xp disk and went into the recovery console command to write a new xp mbr to the slave disk (windows), but it warned me aggressively that i could blow out the partitions table and lose all data, so i chickened out.

if i understand you correctly, what yo are suggesting is to write what is on the first sector of the master/ubuntu drive to the slave drive where windows is, correct?  in case this matters, all partitions were newly created when i installed ubuntu on the slave drive, so i am not sure if the needed data is on there (??)

don't mean to be chatty on this, but i want to make sure i don't whack somethign as i have a couple of apps that i must use through windows.

thanks!

---

### Post by froy02 on 2008-02-18
From your post of the results of fdisk, your boot partition for windows does not start at 1 rather it starts at 63 so chainloader +1 may not work. 

Try chainloader +63 and see if that works.

Also re-writing the MBR should not usually mess up your partitions.  The MBR does not have the information for your partitions.

---

### Post by zeph319 on 2008-02-18
Hi
I hope this is not hijacking the thread..
I have a similar problem.
I installed Ubuntu studio on a second hard disk, dual booting with XP which worked fine.
I needed to uninstall as I don't have the time currently to climb the learning curve for US. I followed the instructions here

[http://www.users.bigpond.net.au/hermanzone/p18.htm#If_you_are_about_to_install_Ubuntu](http://www.users.bigpond.net.au/hermanzone/p18.htm#If_you_are_about_to_install_Ubuntu)

using the XP disk to "fixmbr" which worked, and I can now boot into Windows direct on startup. The problem is I can not see my second drive any longer to remove the Ubuntu install and use the storage (the reason for not keeping Ubuntu installed).

Can you help?

edit: I have now found disk management in XP admin tools, formatted D: and can use the storage. Thanks for those considering an answer. Hopefully soon I will have time to try Ubuntu again.

---

### Post by peakay on 2008-02-19
> **froy02 said:**
> From your post of the results of fdisk, your boot partition for windows does not start at 1 rather it starts at 63 so chainloader +1 may not work. 

Try chainloader +63 and see if that works.

Also re-writing the MBR should not usually mess up your partitions.  The MBR does not have the information for your partitions.

Thanks Froy.  I tried ahtis and it did not make a difference.

So, it sounds like I either take a deep breath and use the windows xp disk to recreate the mbr on the winxp drive or use Puma's suggestions, right?

Puma, can you add justa little more detail around what you are suggesting to make me more comfortable before trying?  If that doesn't work, is anythign permanently broken?  I appreciate all the help.

---

### Post by peakay on 2008-02-19
ok, i tried the deep breath approack with the xp disc and i got the following error message using fixmbr /device/harddisk1

"the old master boot record cannot be read"

so, it appears that unless i am able to copy the odl mbr to the other drive, windows does not want to fix it.

---

### Post by Pumalite on 2008-02-19
Try Super Grub to fix your XP MBR if you want to feel more comfortable: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by peakay on 2008-02-19
> **Pumalite said:**
> Try Super Grub to fix your XP MBR if you want to feel more comfortable: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Thanks Puma.  It's less a comfort with the type of actions as it is not having an explanation of what they are so I know what I am doing and don't make a mistake.  If SG is a way to make this simple and more fisher price, i'll try it, but really i just want to know what it is exactly I need to do to correct it and how.  I know just enough to be dangerous at this point,  :)

---

### Post by Pumalite on 2008-02-19
When one is installing a new OS, one should backup all important files as a matter of good practice. Beyond that, all the advice you have gotten here is good and safe. It depends on how you use it. There is a learning curve in any new OS. You cannot learn it overnight. I'll give you a few links to tutorials:

[http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)
[http://www.geekgirls.com/](http://www.geekgirls.com/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)

---

### Post by peakay on 2008-02-19
OK, more actions on this but no solution.  I made a grub disk and played with this for a while.  I went into windows > advanced and used windows fix tool.  it provided a way to uninstall grub from the mbr of the linux drive, but no way to restore the windows mbr.  i think since I completely repartitioned that drive, there is no windows mbr remaining.

OK, so next I used the terminal commands form puma.  

1) tried:  sudo mount -t ntfs-3g /dev/sdb /windows

result:
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

2) tried using some sort of root as I can't tell what if any name there is for the partition is where windows is.  no special partition was made on this disk upon install -- only one partition exists as far as I know.

tried:  sudo mount -t ntfs-3g /dev/sdb /

NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

any ideas?  again, I believe any mbr for windows was wiped off the master disk when I repartitioned the disk and installed ubuntu.

thanks,

---

### Post by Pumalite on 2008-02-19
From your fdisk -lu:
'/dev/sdb1 * 63 80276804 40138371 7 HPFS/NTFS'

Windows is supposed to be in sdb1

---

### Post by peakay on 2008-02-19
here's what i get.  denied access both ways...

sudo mount -t ntfs-3g /dev/sdb1 /
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 / -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 / ntfs-3g defaults,force 0 0
paul@office-ubuntu:~$ mount -t ntfs-3g /dev/sdb1 / -o force
mount: only root can do that
paul@office-ubuntu:~$

---

### Post by Pumalite on 2008-02-20
sudo

---

### Post by peakay on 2008-02-20
results:

paul@office-ubuntu:~$ sudo mount -t ntfs-3g /dev/sdb1 / -o force
[sudo] password for paul:
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
paul@office-ubuntu:~$ sudo dd if=/dev/sda3 of=/windows/ubuntu.bin bs=512 count=1
dd: opening `/windows/ubuntu.bin': No such file or directory

---

### Post by peakay on 2008-02-20
you know, i think there may also be somethign wrong with the drive windows is on.  when i was in recovery consol yeterday, i could not see subsiredtories from a dir dos command and i don't seem to see contents on the disk form linux.

how can i check this form linux??

---

### Post by dstew on 2008-02-20
It sounds like your ntfs partition has errors on it. I don't know if you can check this with any of the usual Ubuntu tools, although you might try ```
sudo fsck -t ntfs /dev/sdb1
```For a real solid check, use the Windows **chkdsk** command from the Recovery console.

---

### Post by Pumalite on 2008-02-20
You can use Knoppix Live CD too: [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)

---

### Post by peakay on 2008-02-21
ok, the disk checks out on a chkdsk, but bootcfg /scan fails and i cannot do a bootcfg /rebuild as a result.  I'm pretty sure windows is toast.

ubuntu is nice and stable, but i wish i hadn't blown out xp....

---

### Post by peakay on 2008-02-24
OK, just to close the loop on this, I could never get the windows xp install to work again, so i had to completely reinstall the OS.  Not tragic since i had everythign backed up save some files ont he desktop and all my installed apps, but a real time waster.  Not sure how it happened, but I recommend disconnecting your windows drive if you are doing ubuntu on a 2nd drive.

fwiw, one time saver for anyone reinstalling windows is to use google pack (pack.google.com) to install and update a bunch of software at once.  openoffice is on there, so with a few clicks you can really install a lot of vital software.  not as easily as ubuntu obviously, but it does make it easy and saves time.

Thanks to all for the tries at helping.  Both OSs are up and workign together without problems now.

---

### Post by Pumalite on 2008-02-24
Glad you got it working. Good Luck.

---

