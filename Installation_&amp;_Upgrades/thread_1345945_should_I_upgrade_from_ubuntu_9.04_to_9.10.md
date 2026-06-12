---
title: "should I upgrade from ubuntu 9.04 to 9.10?"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by hockey97 on 2009-12-04
I want to know if it's safe to upgrade to 9.10. 

I have apache and other server software on my computer would this get deleted? 

My update manager won't work anymore. I get errors... do you think a upgrade will fix this?

I just want to know that any settings I set right now or programs I installed won't get erased when I do a upgrade... just wondering?

---

### Post by phillw on 2009-12-04
> **hockey97 said:**
> I want to know if it's safe to upgrade to 9.10. 

I have apache and other server software on my computer would this get deleted? 

My update manager won't work anymore. I get errors... do you think a upgrade will fix this?

I just want to know that any settings I set right now or programs I installed won't get erased when I do a upgrade... just wondering?

My 9.04 with LAMP upgraded okay to 9.10, with no data loss. - I'd still take a backup, tho !!! (I did)

As to what is wrong with Update manager, could you be a bit more specific ?
As we need to ensure your system is fully upto date with 9.04, before we move to 9.10

Regards,

Phill.

---

### Post by hockey97 on 2009-12-04
well when I click on update manager and see new updates for apache and php etc.

I click update... so it starts to update then I get an error saying 

lsb-release  missing final newline.

the says:

usr/bin/dpkg  returned error code 2

then said error package failed to install: trying to recover...

that is about it.

I then had to close the update manager. I even tried updating one update at a time and still I get this error.

---

### Post by phillw on 2009-12-04
What does this give ?

```
sudo dpkg --configure -a
sudo apt-get update

```

Phill.

---

### Post by hockey97 on 2009-12-04
when I type that in terminal this is what I get:

```
user@hostname:~$ sudo dpkg --configure -a
user@hostname:~$ sudo apt-get update
Hit http://us.archive.ubuntu.com jaunty Release.gpg
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US      
Hit http://security.ubuntu.com jaunty-security Release.gpg          
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Hit http://archive.ubuntu.com jaunty Release.gpg                     
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com jaunty-proposed Release.gpg
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release               
Hit http://archive.ubuntu.com jaunty Release                         
Ign http://us.archive.ubuntu.com jaunty-proposed/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-proposed/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-proposed/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-proposed/universe Translation-en_US
Hit http://us.archive.ubuntu.com jaunty Release
Hit http://us.archive.ubuntu.com jaunty-updates Release
Hit http://us.archive.ubuntu.com jaunty-proposed Release                       
Hit http://security.ubuntu.com jaunty-security/main Packages                   
Hit http://archive.ubuntu.com jaunty/restricted Sources                        
Hit http://us.archive.ubuntu.com jaunty/main Packages                          
Hit http://security.ubuntu.com jaunty-security/restricted Packages   
Hit http://security.ubuntu.com jaunty-security/restricted Sources    
Hit http://security.ubuntu.com jaunty-security/main Sources          
Hit http://security.ubuntu.com jaunty-security/multiverse Sources    
Hit http://archive.ubuntu.com jaunty/main Sources                    
Hit http://us.archive.ubuntu.com jaunty/restricted Packages          
Hit http://us.archive.ubuntu.com jaunty/restricted Sources
Hit http://us.archive.ubuntu.com jaunty/main Sources
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty/universe Sources
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty-proposed/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-proposed/main Packages
Hit http://us.archive.ubuntu.com jaunty-proposed/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty-proposed/universe Packages
Hit http://us.archive.ubuntu.com jaunty-proposed/restricted Sources
Hit http://us.archive.ubuntu.com jaunty-proposed/main Sources
Hit http://us.archive.ubuntu.com jaunty-proposed/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-proposed/universe Sources
Reading package lists... Done

```

---

### Post by phillw on 2009-12-04
Do you have your backup ?

Phill.

---

### Post by hockey97 on 2009-12-04
no, I just backedup my website files. 

How can I make a backup of apache and mysql and webmin? Also nvidia graphics driver..

The only thing that is important is my website stuff that is it.

Anything that effects the website. this would be apache and mysql database.

is their a easy command to make a backup of it to my external hard drive?

I have a external hard drive usb device.

---

### Post by phillw on 2009-12-04
There sure is a nice simple way !!

Plug in your external drive, let ubuntu 'see' it then pop back the results of

```
sudo fdisk -l
```

and
```
df -ah | grep dev
```

(To get the | it is usually Shift+\ on the lower left of your keyboard)


Phill.

---

### Post by hockey97 on 2009-12-04
how do I make it save the stuff to the external hard drive? 

don't I have to put a path to direct the saves to the directory of the hard drive?

I will make a folder on my external hard drive.

---

### Post by phillw on 2009-12-04
No, just post the output of the 2 commands i gave you.

I'll give you a script to copy & paste that will backup your system to your external drive (a photo-copy of your system) But i need to know device numbers & space free, etc.

Phill.

---

### Post by hockey97 on 2009-12-04
well could I just use those 2 commands you gave?

---

### Post by phillw on 2009-12-04
The backup is based on this [http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)   except that I can write it far more quickly for you !!

I have a 'how-to' that covers that and fdisk & df in the works at the moment, so people can write their own variants -- When we've gotten you safely backed up & upgraded, you're welcome to have a read of it - It's still got some rough corners on it - But any comments from reading it will be welcome.

You are following it now - as it is how i do my backups, for my server system.

Phill.

---

### Post by phillw on 2009-12-04
I need the output of those two commands to do the --exclude  part of the tar script for you. and where to save the command to for you to run it.

Phill.

---

### Post by hockey97 on 2009-12-04
here is the output:

```
user@hostname:~$ sudo fdisk -l
[sudo] password for user: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec7bec7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       36481   190635322+  83  Linux

Disk /dev/sdb: 61.4 GB, 61471162368 bytes
255 heads, 63 sectors/track, 7473 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004a296

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7380    59279818+  83  Linux
/dev/sdb2            7381        7473      747022+   5  Extended
/dev/sdb5            7381        7473      746991   82  Linux swap / Solaris
df -ah | grep dev
user@hostname:~$ df -ah | grep dev
/dev/sdb1              56G  4.0G   49G   8% /
udev                  375M  160K  375M   1% /dev
tmpfs                 375M   76K  375M   1% /dev/shm
devpts                   0     0     0   -  /dev/pts
/dev/sda2             179G  438M  170G   1% /home

```

---

### Post by phillw on 2009-12-04
> **hockey97 said:**
> here is the output:

```
user@hostname:~$ sudo fdisk -l
[sudo] password for user: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec7bec7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       36481   190635322+  83  Linux

Disk /dev/sdb: 61.4 GB, 61471162368 bytes
255 heads, 63 sectors/track, 7473 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004a296

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7380    59279818+  83  Linux
/dev/sdb2            7381        7473      747022+   5  Extended
/dev/sdb5            7381        7473      746991   82  Linux swap / Solaris
df -ah | grep dev
user@hostname:~$ df -ah | grep dev
/dev/sdb1              56G  4.0G   49G   8% /
udev                  375M  160K  375M   1% /dev
tmpfs                 375M   76K  375M   1% /dev/shm
devpts                   0     0     0   -  /dev/pts
/dev/sda2             179G  438M  170G   1% /home

```

is your usb drive the 64 GB Drive and your main hard-drive the 300 GB drive ?

---

### Post by hockey97 on 2009-12-04
no, my external hard drive is having errors on mounting...

---

### Post by hockey97 on 2009-12-04
here is the output with the external hard drive connected:
```
user@hostname:~$ sudo fdisk -l
[sudo] password for user: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec7bec7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       36481   190635322+  83  Linux

Disk /dev/sdb: 61.4 GB, 61471162368 bytes
255 heads, 63 sectors/track, 7473 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004a296

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7380    59279818+  83  Linux
/dev/sdb2            7381        7473      747022+   5  Extended
/dev/sdb5            7381        7473      746991   82  Linux swap / Solaris
user@hostname:~$ df -ah | grep dev
/dev/sdb1              56G  4.0G   49G   8% /
udev                  375M  156K  375M   1% /dev
tmpfs                 375M   76K  375M   1% /dev/shm
devpts                   0     0     0   -  /dev/pts
/dev/sda2             179G  417M  170G   1% /home

```

no the 64gb drive and the 300gb drive is 2 hard drives that is connected to my computer.

the external hard drive is a usb device. It's a seagate 500gb that black with a blue led looking external hard drive.

---

### Post by sitex on 2009-12-05
[SIZE=2][COLOR=DarkGreen]If some one plan to upgrade Ubuntu 9.04 to Ubuntu 9.10 he can simply use Update Manager...
1. Goto System -> administration -> Update Manager.
2. Click on Upgrade Button.

Then continue with steps...
you can get more details with related screen shots with [solutionz.yolasite.com]("http://solutionz.yolasite.com") [click here to go to the site.]("http://solutionz.yolasite.com")[/COLOR][/SIZE]

---

### Post by phillw on 2009-12-05
> **sitex said:**
> [SIZE=2][COLOR=DarkGreen]If some one plan to upgrade Ubuntu 9.04 to Ubuntu 9.10 he can simply use Update Manager...
1. Goto System -> administration -> Update Manager.
2. Click on Upgrade Button.

Then continue with steps...
you can get more details with related screen shots with [solutionz.yolasite.com]("http://solutionz.yolasite.com") [click here to go to the site.]("http://solutionz.yolasite.com")[/COLOR][/SIZE]

Indeed. - he will, but not without a backup !!!!

Phill.

---

### Post by phillw on 2009-12-05
> **hockey97 said:**
> here is the output with the external hard drive connected:
```
user@hostname:~$ sudo fdisk -l
[sudo] password for user: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec7bec7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       36481   190635322+  83  Linux

Disk /dev/sdb: 61.4 GB, 61471162368 bytes
255 heads, 63 sectors/track, 7473 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004a296

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7380    59279818+  83  Linux
/dev/sdb2            7381        7473      747022+   5  Extended
/dev/sdb5            7381        7473      746991   82  Linux swap / Solaris
user@hostname:~$ df -ah | grep dev
/dev/sdb1              56G  4.0G   49G   8% /
udev                  375M  156K  375M   1% /dev
tmpfs                 375M   76K  375M   1% /dev/shm
devpts                   0     0     0   -  /dev/pts
/dev/sda2             179G  417M  170G   1% /home

```no the 64gb drive and the 300gb drive is 2 hard drives that is connected to my computer.

the external hard drive is a usb device. It's a seagate 500gb that black with a blue led looking external hard drive.

Hi -- Sorry - needed sleep (UK time). CAn you go into Places, you should see the external drive listed - click on it & it should mount. When it mounts can you post the outputs of the fdisk & df again,

Regards,

Phill.

---

### Post by houseworkshy on 2009-12-17
If you have onboard nvidia then don't do it.  I did a couple of weeks ago and it trashed my system as far as resolution and refresh rates went.  Since then I have followed all the advice I could find on the forums to no avail.  Even trying to format the lot and reinstall previous versions of Ubuntu hasn't put me back where I was.  Plus for some reason my cd can no longer detect any disk as bootable bar linux disks so even going back to vista cant be done.  Dreadful, dreadful, release for anyone with a crt and using onboard GeForce 6150SE nForce 430.  Without driver 800 by 600 max with it max 640 x 480 at 50hz

---

### Post by houseworkshy on 2009-12-20
The mvidia driver has been fixed since my last comment.  So I withdraw the comment about the releace ...it wasn't releace it was the proprietry driver.  That and me not understanding grub 2.

---

