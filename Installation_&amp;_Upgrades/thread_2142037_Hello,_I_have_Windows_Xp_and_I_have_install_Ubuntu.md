---
title: "Hello, I have Windows Xp and I have install Ubuntu in a second USB harddisk(120Gb)"
date: 2013-05-04
forum: Installation &amp; Upgrades
---

### Post by spi_ on 2013-05-04
Hello, I have Windows Xp and I have install Ubuntu in a second USB harddisk(120Gb) with "wubi", in this harddisk I have and Windows XP files, after 2 years I see in update Ubuntu this: "no space left on device"...Version Ubuntu:No LSB modules are available.Distributor ID:	UbuntuDescription:	Ubuntu 12.04.2 LTSRelease:	12.04Codename:	precise    what can I do?

---

### Post by oldfred on 2013-05-04
It is a bit unusual to have wubi on a second drive. One of the advantages of wubi is that you do not have to create partitions and can easily uninstall as it is just a large file inside the Windows NTFS partition. As a file inside the NTFS partition it has a max of 30GB. It relies on Windows to boot and the NTFS file system, but also then has a Linux file system inside the file. 

But if you are using separate partitions a full install is usually better.
       From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

      
 HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)


Post this from liveCD or if you can boot into wubi currently.
      
 sudo parted /dev/sda unit s print
 sudo parted /dev/sdb unit s print

---

### Post by spi_ on 2013-05-04
I don't understand what can I do, please tell me more details, what is migrate? in one partition is Ubuntu and Windows XP...

---

### Post by oldfred on 2013-05-04
You cannot have Windows XP on an external USB drive, it will not boot from USB devices. So I am confused.

From Ubuntu liveCD/DVD/Flash run this:
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by spi_ on 2013-05-05
hello, nothing again , I see all this messages, what else can I do?

 sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
[sudo] password for vassiliki: 
You are about to add the following PPA to your system:
 Simple tool to repair frequent boot problems.

Website: [https://launchpad.net/boot-repair](https://launchpad.net/boot-repair)
 More info: [https://launchpad.net/~yannubuntu/+archive/boot-repair](https://launchpad.net/~yannubuntu/+archive/boot-repair)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpXhj3p_/secring.gpg' created
gpg: keyring `/tmp/tmpXhj3p_/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpXhj3p_/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                    
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                     
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B]        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources/DiffIndex                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources/DiffIndex          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources/DiffIndex            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources/DiffIndex          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages/DiffIndex          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages/DiffIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages/DiffIndex      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages/DiffIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
Fetched 198 B in 1s (115 B/s)
Reading package lists... Done
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
vassiliki@ubuntu:~$ sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 boot-repair : Depends: boot-sav but it is not going to be installed
               Recommends: gawk but it is not going to be installed
               Recommends: pastebinit but it is not going to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-41-generic but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-41-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
vassiliki@ubuntu:~$ sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libqt4-webkit
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.2.0-41 linux-headers-3.2.0-41-generic
  linux-headers-3.2.0-41-generic-pae
The following NEW packages will be installed:
  linux-headers-3.2.0-41 linux-headers-3.2.0-41-generic
  linux-headers-3.2.0-41-generic-pae
0 upgraded, 3 newly installed, 0 to remove and 4 not upgraded.
5 not fully installed or removed.
Need to get 0 B/13.7 MB of archives.
After this operation, 78.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 720971 files and directories currently installed.)
Unpacking linux-headers-3.2.0-41 (from .../linux-headers-3.2.0-41_3.2.0-41.66_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-41_3.2.0-41.66_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-41/drivers/net/wimax/i2400m/Kconfig.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-41/drivers/net/wimax/i2400m/Kconfig'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking linux-headers-3.2.0-41-generic (from .../linux-headers-3.2.0-41-generic_3.2.0-41.66_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-41-generic_3.2.0-41.66_i386.deb (--unpack):
 error creating directory `./usr/src/linux-headers-3.2.0-41-generic/include/config/dvb/capture': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking linux-headers-3.2.0-41-generic-pae (from .../linux-headers-3.2.0-41-generic-pae_3.2.0-41.66_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-41-generic-pae_3.2.0-41.66_i386.deb (--unpack):
 error creating directory `./usr/src/linux-headers-3.2.0-41-generic-pae/include/config/dvb/capture': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-41_3.2.0-41.66_all.deb
 /var/cache/apt/archives/linux-headers-3.2.0-41-generic_3.2.0-41.66_i386.deb
 /var/cache/apt/archives/linux-headers-3.2.0-41-generic-pae_3.2.0-41.66_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
vassiliki@ubuntu:~$

---

### Post by fantab on 2013-05-05
can you post the Screenshot of your partitions from Windows 'Disk management' utility? Can you also, post the output of the command: *sudo fdisk-l*
Also, you MUST BACK UP ALL YOUR IMPORTANT DATA.

---

### Post by spi_ on 2013-05-05
hello, I attach from Window disk management, the Ubuntu is in Vassiliki Gini (E:) Partition, I wait for your answer...

---

### Post by oldfred on 2013-05-05
Because wubi is full you cannot update nor add Boot-repair to it. You can download a live version and install it to a flash drive or DVD and then add Boot-Repair to it. New versions are oversize so you cannot use CDs anymore.

How large is wubi? It has a max of 30GB, and your partition is larger so you may be able to expand if not the full size already.

       Resize wubi - bcbc
[https://help.ubuntu.com/community/ResizeWubiDisk](https://help.ubuntu.com/community/ResizeWubiDisk)
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

      
 Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by fantab on 2013-05-05
Okay. WUBI install are for Windows users to "Try Ubuntu" for a longer period of time, it is not intended to be use as a permanent install. If you like Ubuntu you MUST seriously consider "TRUE" Dual-Boot, meaning install Ubuntu on it own separate partition and not inside Windows. It is very easy to do so; oldfred in his post# was making this point and gave you some links on how to migrate. However, I'd suggest a clean install to keep it as simple as possible for you. Let us know if you are willing to switch to true dual boot. If you are ready then:

BACK UP ALL YOUR IMPORTANT DATA. 
Do have 32bit processor or 64bit? If you don't know then you can run the following command from Terminal in Ubuntu:
```
uname -m
```
If it says: x86_64 then its 64bit, if it says: x86 or i686 then its 32 bit.


[Download Ubuntu]("http://www.ubuntu.com/download/desktop") (either 32bit or 64bit depending on the achitecture of your machine)and Burn the downloaded .iso to a disk, either DVD or USB. On the same webpage you will also find instructions on how burn .iso to disk and how to install.

If you have any difficulty get back here and we'll help you.

Good Luck...

---

### Post by spi_ on 2013-05-05
hello, this resize lost my Windows XP data in the same partition? I wait for your answer...

---

### Post by oldfred on 2013-05-05
You have to have space for the resize. wubi is just another large file inside the NTFS partition. And NTFS partitions work best if you have 30% free space. Once down to 10% they become very slow.
Of course with any system change backups are required.

---

### Post by bcbc on 2013-05-05
Please boot the Wubi install and post the result of:

```
df -h
```

In the short term you can free up space as follows:
```
sudo apt-get autoremove
sudo apt-get autoclean
```

You can make more space by deleting older kernels. This script will uninstall all but the last two: 
[https://raw.github.com/bcbc/utilities/master/clean_kernel.sh](https://raw.github.com/bcbc/utilities/master/clean_kernel.sh)

If it finds more than two kernels, it will uninstall them (for this you have to enter your password). To run it:
```
wget https://raw.github.com/bcbc/utilities/master/clean_kernel.sh
bash clean_kernel.sh
```

e.g.
```

bcbc@13:30:43:~$ wget https://raw.github.com/bcbc/utilities/master/clean_kernel.sh
--2013-05-05 13:30:46--  https://raw.github.com/bcbc/utilities/master/clean_kernel.sh
Resolving raw.github.com (raw.github.com)... 199.27.75.133
Connecting to raw.github.com (raw.github.com)|199.27.75.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 976 [text/plain]
Saving to: ‘clean_kernel.sh’


100%[======================================>] 976         --.-K/s   in 0s      


2013-05-05 13:30:46 (28.8 MB/s) - ‘clean_kernel.sh’ saved [976/976]


bcbc@13:31:01:~$ bash clean_kernel.sh
[sudo] password for bcbc:

```

---

### Post by spi_ on 2013-05-06
I can these who you writes to me , but if not resize the current Ubuntu, how can I remove it and download again wubi and Ubuntu?

---

### Post by fantab on 2013-05-06
To remove/uninstall WUBI_Ubuntu you have to go to "Add or Remove Programs" in Windows XP, locate Ubuntu, select it and remove/uninstall Ubuntu. Thats it.

---

### Post by bcbc on 2013-05-06
If you uninstall Wubi it deletes all your data you had on the install and it's not recoverable.

The reason I ask for the information is to see the situation and then offer advice. The only command you have to run just checks the space available: df -h

The other stuff can free up space just to give you a little temporary relief but it's not required.

---

