---
title: "Update Manager Issues"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by Hath1 on 2009-12-03
Please help.

I'm a computer professional (Programmer Analyst), but relatively a Linux/Ubuntu newbie.

I have successfully installed Ubuntu Desktop 9.10 i386 on my laptop and an older "salvaged" PC, and gotten them to update successfully.  I have also attempted to install it on an HP Compaq Proliant DL380 G2 (clean install), but am having difficulties with the Update Manager/Software Sources/apt-get, etc. on this particular setup.

I then booted from a freshly burned install CD (.iso md5 checked ok, burned in K3B w/ Verify --> OK) and chose to boot to the Memory Test Option, and it ran 3 full passes with default settings with no issues.  Rebooted and checked the install media --> OK.

I thought maybe something went wrong with the install the first time, so I then clean reinstalled Ubuntu (re-formatted all partitions), but am still getting the following error from the Software Sources after choosing ANY mirror and clicking the Reload button on the "The information about available software is out-of-date" dialog box:

[[IMG]http://img200.imageshack.us/img200/4748/softwaresources.th.png[/IMG]]("http://img200.imageshack.us/i/softwaresources.png/")

The text of the error message includes something along these lines (I have tried many times with many different mirrors, but at a minimum they always list at least one Packages.bz2 error):

> Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/karmic/main/binary-i386/Packages.bz2](http://archive.linux.duke.edu/ubuntu/dists/karmic/main/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2](http://archive.linux.duke.edu/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.
I have searched the forums for quite some time but have not been able to find the solution.


Since similar problems in these forums often ask for the output of running some commands, here is the output from running. . .


```
sudo apt-get clean
```> <nothing>```
sudo apt-get update
```> Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic Release.gpg
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic/main Translation-en_US
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic/restricted Translation-en_US
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic/universe Translation-en_US
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic/multiverse Translation-en_US
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-updates Release.gpg
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-updates/main Translation-en_US
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-updates/restricted Translation-en_US
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-updates/universe Translation-en_US
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-updates/multiverse Translation-en_US
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-security Release.gpg
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-security/main Translation-en_US
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-security/restricted Translation-en_US
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-security/universe Translation-en_US
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-security/multiverse Translation-en_US
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic Release         
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-updates Release 
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-security Release                     
Get:1 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic/main Packages [1,353kB]            
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic/restricted Packages
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic/main Sources                         
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic/restricted Sources                   
Get:2 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic/universe Packages [5,133kB]         
27% [1 Packages bzip2 2650112] [2 Packages 408102/5,133kB 7%]                  
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic/main Packages       
  Sub-process /bin/bzip2 returned an error code (2)
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic/universe Sources                      
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic/multiverse Packages                   
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic/multiverse Sources                   
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-updates/main Packages                 
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-updates/restricted Packages           
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-updates/main Sources                  
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-updates/restricted Sources            
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-updates/universe Packages             
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-updates/universe Sources              
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-updates/multiverse Packages           
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-updates/multiverse Sources            
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-security/main Packages                
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-security/restricted Packages          
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-security/main Sources                 
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-security/restricted Sources           
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-security/universe Packages            
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-security/universe Sources             
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-security/multiverse Packages          
Hit [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic-security/multiverse Sources           
99% [2 Packages bzip2 2699264]                                       613kB/s 0s
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic/universe Packages                     
  Sub-process /bin/bzip2 returned an error code (2)
Fetched 6,486kB in 10s (629kB/s)                                               
W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/karmic/main/binary-i386/Packages.bz2](http://archive.linux.duke.edu/ubuntu/dists/karmic/main/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2](http://archive.linux.duke.edu/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.```
sudo gedit '/etc/apt/sources.list'
```> # deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverseUsing the Update Manager or apt-get upgrade also came up with errors the first time I had installed Ubuntu, but I haven't run them yet on this current install as I'm hoping that the Software Sources issues can be solved first, and I'd like to leave the system in as nearly pristine a state as possible to aid in troubleshooting, especially if the solution helps out other people who may run into this or a similar issue.  (I have two other machines that are capable of updating successfully on my LAN, all using DHCP, so I do not think that the network is the issue.)

Please let me know how to supply any additional information that may be helpful in resolving this issue.

Thank you!

---

### Post by wilee-nilee on 2009-12-03
Some times a server could be having problems or the repository be pointed at could be. you might try a different server from software sources choose other then select best.

---

### Post by Hath1 on 2009-12-03
> **wilee-nilee said:**
> Some times a server could be having problems or the repository be pointed at could be. you might try a different server from software sources choose other then select best.

  Thank you, but I have already tried at least 5 different sources, I think that there's something else going on here!

---

### Post by wilee-nilee on 2009-12-03
> **Hath1 said:**
> Thank you, but I have already tried at least 5 different sources, I think that there's something else going on here!

I also notice in the apt source list that you haven't opened the multiverse and a couple of others.

---

### Post by Hath1 on 2009-12-03
> **wilee-nilee said:**
> I also notice in the apt source list that you haven't opened the multiverse and a couple of others.

 It is checked in my Software Sources Ubuntu tab.  Everything is checked except "Source Code" and "Cdrom..."  I believe lines 16-29 in my sources opens the multiverse, although I really am quite new to Linux/Ubuntu, so maybe I'm not looking at something right?

---

### Post by wilee-nilee on 2009-12-03
> **Hath1 said:**
> It is checked in my Software Sources Ubuntu tab.  Everything is checked except "Source Code" and "Cdrom..."  I believe lines 16-29 in my sources opens the multiverse, although I really am quite new to Linux/Ubuntu, so maybe I'm not looking at something right?

My mistake it's the backports and,
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
The backports some say don't open but I alway do and have no problems the canonical I would open, you can do it from software sources or just go to the apt source list and remove the # and the space. I am not sure if this is the root of your problem but I occasionaly get that 1st gui you showed and just don't update until it's gone or look at what may be removed or updated via a terminal sudo apt-get update, or synaptic.

---

### Post by Hath1 on 2009-12-03
OK, this gets even stranger.  I transferred the downloaded files from the affected PC to a SMB share on an XP machine and transferred from there to my functional Ubuntu laptop, and archive manager on the laptop is unable to extract these "bad" files.  I then downloaded the files from the working laptop using the same url referenced in this thread, and then the working laptop was able to extract the bz2 files successfully.  Even weirder:  I copied the "good" bz2 files to the SMB share from the working laptop.  If I open them on the affected PC directly from the SMB share, then archive manager can extract them successfully to the desktop.  If, however, I first copy the "good" files to the desktop on the affected PC, archive manager is again unable to extract them!  If I had to make one guess at this point, I would say there is some kind of file corruption going on with the affected PC.

---

### Post by Hath1 on 2009-12-03
OK, I have been copying the 2 files from SMB share to the Desktop on the affected PC (same source files each time) and running md5sum on each after each copy, and the md5sum result keeps changing!  Something is really screwed here!

At first I thought maybe it could be an EXT4 bug (I mounted / as EXT4 on hardware RAID1), but the files on my desktop should be under /home (is this correct?) which I created as EXT3 on hardware RAID5.  Therefore I don't think this could be EXT4.  Could the CPU or RAM or NIC be flaking out?  I'm going to boot into Goldmem in a minute and then go to bed.  Anyone know of any Cpu-stress-tests I could run to detect CPU errors if the RAM tests out OK, or NIC/LAN stress tests if it's the net card?

Thank you,

-Ryan

---

