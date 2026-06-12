---
title: "Ubuntu 11.10 64-bit Update manager broken"
date: 2011-11-09
forum: Installation &amp; Upgrades
---

### Post by GisliKarl on 2011-11-09
Every time I try to update it fails with this error

> Failed to download repository information
Check your Internet connection.

W:GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports InRelease: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-backports_InRelease - RunGPGV (2: No such file or directory), W:GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_InRelease - RunGPGV (2: No such file or directory), W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease: Could not open file /var/lib/apt/lists/ppa.launchpad.net_webupd8team_haguichi_ubuntu_dists_oneiric_InRelease - RunGPGV (2: No such file or directory), E:Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_binary-i386_Packages.IndexDiff - open (2: No such file or directory)

---

### Post by bluexrider on 2011-11-09
Try this:
  sudo -i apt-get clean cd /var/lib/apt mv lists lists.old mkdir -p lists/partial apt-get clean apt-get update

---

### Post by GisliKarl on 2011-11-09
> **bluexrider said:**
> Try this:
  sudo -i apt-get clean cd /var/lib/apt mv lists lists.old mkdir -p lists/partial apt-get clean apt-get update
Only thing I get is this

> E: Command line option 'p' [from -p] is not known.

---

### Post by bluexrider on 2011-11-09
This may be more help

[http://askubuntu.com/questions/13065/how-do-i-fix-the-gpg-error-no-pubkey](http://askubuntu.com/questions/13065/how-do-i-fix-the-gpg-error-no-pubkey)

---

### Post by GisliKarl on 2011-11-09
> **bluexrider said:**
> This may be more help

[http://askubuntu.com/questions/13065/how-do-i-fix-the-gpg-error-no-pubkey](http://askubuntu.com/questions/13065/how-do-i-fix-the-gpg-error-no-pubkey)
Thank you for the link, will let you know if it works :D

---

### Post by GisliKarl on 2011-11-09
It didn't work, tried every answer. Everytime I do sudo apt-get update in the terminal I get this

> gislikarl@gislikarl-ubuntu:~$ sudo apt-get update
[sudo] password for gislikarl: 
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                               
Ign [http://deb.opera.com](http://deb.opera.com) stable InRelease                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports InRelease                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports InRelease                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources                       
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main Sources/DiffIndex         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted Sources/DiffIndex   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Sources                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe Sources/DiffIndex     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse Sources/DiffIndex   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main amd64 Packages/DiffIndex  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted amd64 Packages/DiffIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Get:3 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe amd64 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse amd64 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main i386 Packages/DiffIndex   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted i386 Packages/DiffIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe i386 Packages/DiffIndex
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports InRelease: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-backports_InRelease - RunGPGV (2: No such file or directory)
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_InRelease - RunGPGV (2: No such file or directory)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures were invalid: BADSIG C2518248EEA14886 Launchpad VLC
E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_binary-i386_Packages.IndexDiff - open (2: No such file or directory)
gislikarl@gislikarl-ubuntu:~$ 

---

### Post by bluexrider on 2011-11-10
can you post the contents of your /etc/apt/source.list file?

---

### Post by GisliKarl on 2011-11-10
Couldn't find a source.list file but there was a sources.list file which I assume you were meaning :) here is the content

> deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://speglar.simnet.is/ubuntu/](http://speglar.simnet.is/ubuntu/) oneiric main restricted
deb-src [http://speglar.simnet.is/ubuntu/](http://speglar.simnet.is/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://speglar.simnet.is/ubuntu/](http://speglar.simnet.is/ubuntu/) oneiric-updates main restricted
deb-src [http://speglar.simnet.is/ubuntu/](http://speglar.simnet.is/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://speglar.simnet.is/ubuntu/](http://speglar.simnet.is/ubuntu/) oneiric universe
deb-src [http://speglar.simnet.is/ubuntu/](http://speglar.simnet.is/ubuntu/) oneiric universe
deb [http://speglar.simnet.is/ubuntu/](http://speglar.simnet.is/ubuntu/) oneiric-updates universe
deb-src [http://speglar.simnet.is/ubuntu/](http://speglar.simnet.is/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://speglar.simnet.is/ubuntu/](http://speglar.simnet.is/ubuntu/) oneiric multiverse
deb-src [http://speglar.simnet.is/ubuntu/](http://speglar.simnet.is/ubuntu/) oneiric multiverse
deb [http://speglar.simnet.is/ubuntu/](http://speglar.simnet.is/ubuntu/) oneiric-updates multiverse
deb-src [http://speglar.simnet.is/ubuntu/](http://speglar.simnet.is/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://speglar.simnet.is/ubuntu/](http://speglar.simnet.is/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://speglar.simnet.is/ubuntu/](http://speglar.simnet.is/ubuntu/) oneiric-backports main restricted universe multiverse

deb [http://speglar.simnet.is/ubuntu/](http://speglar.simnet.is/ubuntu/) oneiric-security main restricted
deb-src [http://speglar.simnet.is/ubuntu/](http://speglar.simnet.is/ubuntu/) oneiric-security main restricted
deb [http://speglar.simnet.is/ubuntu/](http://speglar.simnet.is/ubuntu/) oneiric-security universe
deb-src [http://speglar.simnet.is/ubuntu/](http://speglar.simnet.is/ubuntu/) oneiric-security universe
deb [http://speglar.simnet.is/ubuntu/](http://speglar.simnet.is/ubuntu/) oneiric-security multiverse
deb-src [http://speglar.simnet.is/ubuntu/](http://speglar.simnet.is/ubuntu/) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free

---

### Post by bluexrider on 2011-11-11
Back up your /var/lib/lists/sources.list say to your desktop or documents file.

From the Terminal type the following commands :
sudo rm /var/lib/apt/lists/* -vf

and
sudo apt-get update



This  will delete the older entries and download the latest ones after which the error should no longer be there.

---

### Post by GisliKarl on 2011-11-11
I didn't have a sources.list in /var/lib/lists and after running sudo rm /var/lib/apt/lists* -vf and sudo apt-get update I still get errors

> gislikarl@gislikarl-ubuntu:~$ sudo apt-get update
[sudo] password for gislikarl: 
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en
Ign [http://speglar.simnet.is](http://speglar.simnet.is) oneiric InRelease                                 
Ign [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates InRelease                         
Ign [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports InRelease                       
Get:1 [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security InRelease [198 B]              
Ign [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security InRelease                        
Get:2 [http://speglar.simnet.is](http://speglar.simnet.is) oneiric Release.gpg [198 B]                     
Get:3 [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-updates Release.gpg [198 B]             
Ign [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-backports Release.gpg                     
Ign [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/main Sources/DiffIndex           
Ign [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/restricted Sources/DiffIndex     
Ign [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/universe Sources/DiffIndex       
Ign [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/multiverse Sources/DiffIndex     
Ign [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/main amd64 Packages/DiffIndex    
Ign [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/restricted amd64 Packages/DiffIndex
Ign [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/universe amd64 Packages/DiffIndex
Ign [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/multiverse amd64 Packages/DiffIndex
Ign [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/main i386 Packages/DiffIndex     
Ign [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/restricted i386 Packages/DiffIndex
Ign [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/universe i386 Packages/DiffIndex 
Hit [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security/multiverse i386 Packages/DiffIndex
W: GPG error: [http://speglar.simnet.is](http://speglar.simnet.is) oneiric-security InRelease: File /var/lib/apt/lists/partial/speglar.simnet.is_ubuntu_dists_oneiric-security_InRelease doesn't start with a clearsigned message
E: Could not open file /var/lib/apt/lists/speglar.simnet.is_ubuntu_dists_oneiric-security_multiverse_binary-i386_Packages.IndexDiff - open (2: No such file or directory)
gislikarl@gislikarl-ubuntu:~$ 

---

### Post by bluexrider on 2011-11-11
> **GisliKarl said:**
> Couldn't find a source.list file but there was a sources.list file which I assume you were meaning :) here is the content

With the exception of that one "natty" entry the rest looks fine. But that one isn't the problem anyway.

I noticed that you have amd64 and i386 packages both. We need additional insight on this problem. I am to help any longer.

---

### Post by GisliKarl on 2011-11-13
What do you think I could do to fix this problem?

---

