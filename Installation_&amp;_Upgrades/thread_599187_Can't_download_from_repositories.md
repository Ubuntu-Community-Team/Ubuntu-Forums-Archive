---
title: "Can't download from repositories"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by ggauche on 2007-11-01
I am having not much fun trying to solve a problem since upgrading to Gutsy a week or so ago.
The main problem is that I cannot connect to any repositories to obtain programs.
Here's what I get when I run:
sudo apt-get update

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)

Now when I installed Gutsy (first via the update method, then 3 or 4 times via the installation CD) I got a message right near the end that said:

"The security updates on security.ubuntu.com couldn't be accessed, so these updates will not be made available to you at this time.
You should investigate this later."

Which is what I have been doing for a week now, here in the forums and on the wider net.
I also get the same message "No route to host" when I try to telnet, for example.
telnet mail.netspace.net.au 25
Trying 1.0.0.0...
telnet: Unable to connect to remote host: No route to host

**So, there's more to it than just a problem with /etc/apt/sources.list**
Although there may be a problem there as well!

Here's some other info that may be helpful:

 netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         mygateway1.ar7  0.0.0.0         UG        0 0          0 eth0


cat /etc/network/interfaces
auto lo
iface lo inet loopback



lspci | grep Eth
02:04.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller

dmesg |grep eth
[   26.552994] natsemi eth0: NatSemi DP8381[56] at 0xefeff000 (0000:02:04.0), 00:02:e3:0b:2d:58, IRQ 9, port TP.
[   44.927092] eth0: DSPCFG accepted after 0 usec.
[   44.927107] eth0: link up.
[   44.927122] eth0: Setting full-duplex based on negotiated link capability.
[   66.022174] eth0: no IPv6 routers present


 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:E3:0B:2D:58  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:e3ff:fe0b:2d58/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3347 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2388 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2129975 (2.0 MB)  TX bytes:246231 (240.4 KB)
          Interrupt:9 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


Any help would be very much appreciated!

---

### Post by dabl on 2007-11-01
That is not one of the sources that my Gutsy installation set up by default. You aren't using Automatix, perchance?

I'm not convinced that your assertion regarding the /etc/apt/sources.list is correct -- can you post it?

---

### Post by ggauche on 2007-11-01
Thanks dabl for looking.
Here 'tis:

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by ggauche on 2007-11-01
...and no, I am not running Automatix

Thanks for any insights.

---

### Post by dabl on 2007-11-01
> **ggauche said:**
> 

# Line commented out by installer because it failed to verify:



I see way more of these than I believe are appropriate.  Not being in Australia, I'm not sure what may be causing this to happen.  Here's what a good sources.list file looks like in the U.S.  Perhaps you can "compare and contrast" and get some ideas -- I'd try to uncomment some of those "commented out by installer" lines, or else find some different repo sources.

> # deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release Candidate amd64 (20071009.1)]/ gutsy main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


---

### Post by ggauche on 2007-11-01
Well, I backed up my sources.list and replaced it with the one you supplied and this is what I got;
sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg                                              
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_AU                                   
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_AU                            
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_AU                      
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_AU                        
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_AU                      
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                                 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_AU                              
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                                   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_AU                                
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_AU                              
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg                                       
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_AU                            
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_AU                      
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_AU                        
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages                                
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_AU                      
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                                           
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                                      
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages                                
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources                                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources                                        
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                                       
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources                                 
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                                  
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                                   
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages                                
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources                                      
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources                                 
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_AU.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_AU.bz2)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_AU.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_AU.bz2)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_AU.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_AU.bz2)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_AU.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_AU.bz2)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_AU.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_AU.bz2)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_AU.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_AU.bz2)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_AU.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_AU.bz2)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_AU.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_AU.bz2)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_AU.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_AU.bz2)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_AU.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_AU.bz2)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_AU.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_AU.bz2)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_AU.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_AU.bz2)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


I tried Add/Remove and got similar results when I hit the Refresh button.

---

### Post by dabl on 2007-11-02
Hmmmmmmmm.

Well, I didn't really mean for you to change out your Australian repos for U.S. repos, assuming you are in or near Australia.  But I wanted you to see what the form of the source repos needs to look like.

Will your browser open any of the Australian sources?  In other words, if you put this URL in your browser address line, does it open a web site:

[http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/)

?


If yes, then just uncomment the lines in your menu.lst that correspond with uncommented lines in my menu.lst.  In other words, you have:

# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted

where I have:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

So you need to remove that "#" from in front of that line and all other lines that need to be open.

What do you see when you open Synaptic and look at the sources (I'm running Kubuntu and can't remember exactly how Synaptic presents the sources)?  Are the universe and multiverse enabled?

:)

---

### Post by beargrab on 2007-11-02
Hey, I am also from Australia and experiencing the same problem.  Strangely enough, if you have the links open in your web browser (firefox in my case) prior to doing your updates, it seems to work.  If you don't, it doesn't.  This is far from ideal, and as I am a newbie I don't know why this is the case (perhaps something to do with cache?).

Hope this helps a little.

---

### Post by ggauche on 2007-11-03
I've restored my original sources.list. Tis is it without comments:
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted

The update manager now seems to know enough to tell me I have 14 updates to get - compiz, firefox, ghostscript, some libs, openssl.

But I can't get them - the connection always fails with 113 no route to host.


I can http to the above sites in Firefox and browse the directories and even ftp files down manually!
But that doesn't seem to make any difference ub getting via sudo apt-get update or Synaptic.

So, can I just ftp down the updates and other software I want and manually install them somehow?

---

### Post by dabl on 2007-11-03
You have to "wget" the repos, and it's not something I have done, unfortunately.  But, upon getting the "key" from the site, you enter it into the "wget" command and that will enable the repo.  It's odd that you had that problem -- must be something up with the Australian repo servers.

---

### Post by ggauche on 2007-11-05
I am still struggling with this.
It LOOKs, from my reading, and the and esp [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch04_:_Simple_Network_Troubleshooting](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch04_:_Simple_Network_Troubleshooting)  like I have a Firewall blocking SOME traffic, and SOME traffic sometimes - but I don't.

I am going to re-install Feisty on another partition to try to compare settings and behaviours (maybe this is double trouble!)

---

### Post by ggauche on 2007-11-06
Now back on Feisty!
I installed Feisty on one partition and Gusty on another.  All the network related config files and tests are the same - well all the ones I know about - yet Feisty works and Gutsy leaves me pretty well stranded in  isolation.

So, I'll settle for Feisty for now and wait until Gutsy is sorted.  Not where I want to be but...

---

### Post by ggauche on 2008-01-29
Well,
Here I am with a new box.  This time with 512 MB of RAM - my old box had only 256 MB of RAM!
I noticed in the installation notes that you need at least 384 MB of RAM to install 7.10.
So THAT could have been my problem all along.

Thank you BP for giving me the new box. It is way ahead of the old thing I was using before!
So 7.10 is absolutely fine with me now!
(And my old Bt848 TV tuner works fine too)

ggauche

---

### Post by Carl H on 2008-01-29
> **ggauche said:**
> 
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)

This is a DNS error. It won't connect because 1.0.0.0 isn't the right IP address for archive.ubuntu.com

1.0.0.0 is a dummy IP address returned by a DNS server when the lookup fails. Possibly something went wrong during installation. I had the same problem installing Debian once.

---

