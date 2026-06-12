---
title: "Synaptic Update failure-lucid 10.04"
date: 2011-06-09
forum: Installation &amp; Upgrades
---

### Post by livetobefree on 2011-06-09
hello, 

 I'm hoping someone can help me here, when I try to update my system(10.04 Lucid)  it gives me this error message.  


[B]Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'[/B]


Judging by the problem-solutions Ive seen on the forum Im certain an Ubuntu Guru out there has an idea what this means, it may be a simple fix but its beyond me.

---

### Post by wojox on 2011-06-09
Run these three commands in the Terminal Ctrl+Alt+T

```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get clean all 
sudo apt-get update
```

---

### Post by livetobefree on 2011-06-11
Hello and thanks for your suggestion, it seemed to work but then at the end it said there was a problem, here what I got:


[B]empty@empty-zen:~$ sudo rm /var/lib/apt/lists/* -vf 
[sudo] password for empty: 
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_source_Sources'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_Release'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid-security_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid-security_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid-security_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/lock'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
removed `/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_lucid_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_lucid_Release'
removed `/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_lucid_Release.gpg'
empty@empty-zen:~$ sudo apt-get clean all
empty@empty-zen:~$ sudo apt-get update
Get:1 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [198B]
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US      
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg [189B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US        
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Get:4 [http://archive.canonical.com](http://archive.canonical.com) lucid Release [8,215B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg [198B]            
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg [189B]                    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic/main Translation-en_US            
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic/universe Translation-en_US      
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release [57.2kB]                       
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [14.0kB]                          
Get:9 [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages [13.4kB]             
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [581B]                     
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release [44.7kB]               
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release [65.9kB]                       
Get:13 [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources [6,590B]             
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages [1,386kB]   
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages [5,448kB]             
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages [194kB]          
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages [71.5kB]     
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages [1,353kB]                
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages [5,133kB]            
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources [640kB]                   
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources [2,795kB]             
Fetched 17.2MB in 43s (392kB/s)                                                
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
empty@empty-zen:~$ 
[/B]

---

