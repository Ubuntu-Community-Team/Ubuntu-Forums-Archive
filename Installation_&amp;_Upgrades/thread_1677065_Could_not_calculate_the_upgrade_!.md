---
title: "Could not calculate the upgrade ?!?"
date: 2011-01-28
forum: Installation &amp; Upgrades
---

### Post by whowinsdares on 2011-01-28
[SIZE=4][FONT=Arial Black]Hello, I have been using Ubuntu for about 6 months now but I am still quite a novice. But I just tried to upgrade to Maverick Meercat and I got this error message:

[/FONT][/SIZE]   	 	 	 	p { margin-bottom: 0.21cm; }a:link {  }  [FONT=Times New Roman, serif][SIZE=3]Could not calculate the upgrade [/SIZE][/FONT]
 [FONT=Times New Roman, serif][SIZE=3] [/SIZE][/FONT]
 [FONT=Times New Roman, serif][SIZE=3]An unresolvable problem occurred while calculating the upgrade: [/SIZE][/FONT]
 [FONT=Times New Roman, serif][SIZE=3]E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages. [/SIZE][/FONT]
 [FONT=Times New Roman, serif][SIZE=3] [/SIZE][/FONT]
  [FONT=Times New Roman, serif][SIZE=3]This can be caused by: [/SIZE][/FONT]
  [FONT=Times New Roman, serif][SIZE=3]* Upgrading to a pre-release version of Ubuntu [/SIZE][/FONT]
  [FONT=Times New Roman, serif][SIZE=3]* Running the current pre-release version of Ubuntu [/SIZE][/FONT]
  [FONT=Times New Roman, serif][SIZE=3]* Unofficial software packages not provided by Ubuntu [/SIZE][/FONT]
 [FONT=Times New Roman, serif][SIZE=3] [/SIZE][/FONT]
 [FONT=Times New Roman, serif][SIZE=3]If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.[/SIZE][/FONT]
[FONT=Arial Black][SIZE=4]
[/SIZE][/FONT]
[FONT=Times New Roman, serif][SIZE=3][FONT=Arial Black][SIZE=4]So basically I have no idea what to do...[/SIZE][/FONT]
[/SIZE][/FONT]

---

### Post by zvacet on 2011-01-29
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by whowinsdares on 2011-01-30
> **zvacet said:**
> ```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
```


Thanks for the reply, I ran those 2 separate lines of code and got this: 

```
********@*************:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for **********: 

Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid Release.gpg
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main Translation-en_AU
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/restricted Translation-en_AU
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid Release
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/main Packages
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/restricted Packages
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/main Packages
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/restricted Packages
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]                           
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_AU       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid Release.gpg                             
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_AU          
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_AU    
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_AU      
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_AU    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_AU  
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_AU
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports Release.gpg                   
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_AU
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-proposed Release.gpg                    
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-proposed/restricted Translation-en_AU
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-en_AU 
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-proposed/multiverse Translation-en_AU
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid Release                                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates Release                         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_AU   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-proposed Release                        
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,110B]                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/](http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/) lucid/main Translation-en_AU
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/main Packages                           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/main Sources                            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_AU       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/main Packages                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/restricted Packages             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/restricted Sources              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/main Sources                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/multiverse Sources              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/universe Sources                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/universe Packages               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg                            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/multiverse Packages             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/main Packages                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/restricted Packages           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/universe Packages             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/multiverse Packages           
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_AU
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/main Sources                  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/restricted Sources            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/universe Sources              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/multiverse Sources            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-proposed/restricted Packages            
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main Translation-en_AU
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-proposed/main Packages                  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-proposed/multiverse Packages            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-proposed/universe Packages              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-proposed/restricted Sources             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-proposed/main Sources                   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release                                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-proposed/multiverse Sources             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-proposed/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources                               
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_AU                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_AU
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Sources                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Sources                       
Fetched 2,654B in 7s (360B/s)                                                  
W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
*******@****************:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

I then tried to upgrade again and got the exact same error as in this original post..

Someone sent me a private message and redirected me to this:

[http://ubuntuforums.org/showpost.php?p=10344497&postcount=5](http://ubuntuforums.org/showpost.php?p=10344497&postcount=5)

But I don't know how to uninstall something on Ubuntu, apologies not much of a "techy" here but perhaps what I have put in here will reveal the problem.

The terminal readout above mentions something about my CD drive? I am not sure if it is connected to another problem I have which I can't solve - my DVD player can play video DVD's but it can't read data DVD's and twice now I have had to travel 2 hours to a net cafe to get data I have backed up onto DVD's just to continue working on something.

Data on CD's I can access on this machine

If the problem is related it would be good to get 2 birds with 1 stone here.

I am considering downloading Maverick Meercat and burning to an ISO and doing a reinstall..[SIZE=3]
[/SIZE]

---

### Post by dino99 on 2011-01-30
into a terminal:

sudo rm /var/cache/apt/archives/*

open synaptic and:

- choose "main server"
- deselect "cdroom"

then update, upgrade

---

### Post by kansasnoob on 2011-01-30
Do you have the 10.04 CD in the drive? If so remove it!

---

### Post by kansasnoob on 2011-01-30
Also, open Update Manager and click on Settings. Under the other software tab look for duplication of:

W: Duplicate sources.list entry **[http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner** Packages (/var/lib/apt/lists

This might help you a bit:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Be certain 10.04 is updated before proceeding with the distro upgrade!

---

### Post by whowinsdares on 2011-01-30
[SIZE=4]
[/SIZE]
    [SIZE=4]OK guys, I deleted the duplicate repository entry, but I got this error:[/SIZE]
 

 

 The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
 

 Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 
 Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 
 Some index files failed to download, they have been ignored, or old ones used instead.
 

 [SIZE=4]Also on entering &#8220; sudo rm /var/cache/apt/archives/*  &#8221; I got this response..[/SIZE]
 

 

 *********@**************:~$ sudo rm /var/cache/apt/archives/* 
 [sudo] password for ********:  
 rm: cannot remove `/var/cache/apt/archives/partial': Is a directory 
 

 [SIZE=4]There is no disk in the disk drive.[/SIZE]
[SIZE=4]My Internet connection is working fine
[/SIZE]


[SIZE=4]Thank you very much for your replies, however I am still having some serious issues. Sorry for the hassle but something isn't right here?
[/SIZE]

---

### Post by dino99 on 2011-01-30
look at fstab to deactivate/comment/remove about "cdrom"

gksu gedit /etc/fstab

erything else is comments, dont worry.

---

### Post by whowinsdares on 2011-01-30
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=85ab631f-0412-4e85-a229-c4fc5769b772 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a786cbf5-0bf6-4a0b-bfe3-30e329615642 none            swap    sw              0       0

[SIZE=3]What does this mean, and what do I do to fix this? I honestly haven't any idea regarding this. I have some training in C programming and tiny bit of Java, but thats it I have no idea where this is going. 

Am I meant to edit this file and save it? If so what sections?

Is the CD error why I can't read data DVD's do you think? 
Thanks for your help![/SIZE]

---

### Post by whowinsdares on 2011-01-30
Fixed it, thank you!

I had a repository directed to be sourced from a CD so that was a mistake, then I removed the package:

xserver-xorg-video-nouveau 

..through the synaptic package manager which I hadn't used before, and the upgrade has commenced, so thanks especially to:
jotwebe 

who directed me to:

[http://ubuntuforums.org/showpost.php?p=10344497&postcount=5](http://ubuntuforums.org/showpost.php?p=10344497&postcount=5)

---

