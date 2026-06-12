---
title: "I think I broke Synaptic"
date: 2007-07-17
forum: Installation &amp; Upgrades
---

### Post by peterson2k4 on 2007-07-17
Ok, well I did it now!  I tried to download some software via Add/Remove and I got the following message


This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

After I did that I got the following in the terminal

[INDENT]paul@paul-desktop:~$ sudo apt-get update
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                 
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                           
Get:2 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US      
Get:3 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release.gpg [191B]                
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US              
Get:5 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]                  
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Translation-en_US
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Translation-en_US
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Translation-en_US              
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US              
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US        
Get:7 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release.gpg [189B]                     
Ign [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty/screenlets Translation-en_US             
Get:8 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]                  
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Translation-en_US  
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                               
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release                             
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US     
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release.gpg [191B]            
Hit [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release                                  
Err [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release                                  
  
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Packages                       
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Packages
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Sources
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Packages
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Translation-en_US 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Translation-en_US
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B] 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Packages           
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Sources            
Get:12 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release [6906B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release                         
Ign [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty/screenlets Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Fetched 7295B in 1s (4003B/s)
Reading package lists... Done
W: GPG error: [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7
W: You may want to run apt-get update to correct these problems
paul@paul-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  avant-window-navigator: Depends: libawn0 but it is not installed
E: Unmet dependencies. Try using -f.
paul@paul-desktop:~$ sudo apt-get upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following NEW packages will be installed:
  libawn0
The following packages will be upgraded:
  clamav clamav-base clamav-daemon clamav-docs clamav-freshclam clamtk compiz
  compiz-core compiz-dev compiz-fusion-plugins-extra
  compiz-fusion-plugins-main compiz-fusion-plugins-unofficial
  compiz-fusion-plugins-unsupported compiz-gnome compiz-plugins
  compizconfig-settings-manager flashplugin-nonfree libclamav2
  libcompizconfig0 libcompizconfig0-dev libdecoration0 libdecoration0-dev
  libgl1-mesa-dev libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa
  libglu1-mesa-dev mesa-common-dev mesa-utils
29 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 28.7MB/28.7MB of archives.
After unpacking 102kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy libdecoration0-dev 1:0.5.1+git20070716~3v1ubuntu0 [35.1kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe libclamav2 0.90.2-0ubuntu1.3 [371kB]
Get:3 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy libdecoration0 1:0.5.1+git20070716~3v1ubuntu0 [45.4kB]
Get:4 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy compiz-plugins 1:0.5.1+git20070716~3v1ubuntu0 [281kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe clamav-base 0.90.2-0ubuntu1.3 [204kB]
Get:6 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy compiz-core 1:0.5.1+git20070716~3v1ubuntu0 [465kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe clamav-freshclam 0.90.2-0ubuntu1.3 [9694kB]
Get:8 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy compiz-gnome 1:0.5.1+git20070716~3v1ubuntu0 [165kB]
Get:9 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy compiz 1:0.5.1+git20070716~3v1ubuntu0 [28.8kB]
Get:10 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy compiz-dev 1:0.5.1+git20070716~3v1ubuntu0 [55.9kB]
Get:11 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy compiz-fusion-plugins-main 0.0.1+git20070716~3v1ubuntu0 [206kB]
Get:12 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy compiz-fusion-plugins-extra 0.0.1+git20070717~3v1ubuntu0 [184kB]
Get:13 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy compiz-fusion-plugins-unofficial 0.0.1+git20070716~3v1ubuntu0 [117kB]
Get:14 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy compiz-fusion-plugins-unsupported 0.0.1+git20070716~3v1ubuntu0 [33.3kB]
Get:15 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy compizconfig-settings-manager 0.1.0+git20070715~3v1ubuntu0 [459kB]
Get:16 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy libcompizconfig0-dev 0.0.1+git20070716~3v1ubuntu0 [49.8kB]
Get:17 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy libcompizconfig0 0.0.1+git20070716~3v1ubuntu0 [50.4kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe clamav 0.90.2-0ubuntu1.3 [870kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe clamav-daemon 0.90.2-0ubuntu1.3 [177kB]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe clamav-docs 0.90.2-0ubuntu1.3 [1005kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe clamtk 2.32-1~feisty1 [39.6kB]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main libgl1-mesa-dev 6.5.2-3ubuntu8 [25.0kB]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main mesa-common-dev 6.5.2-3ubuntu8 [175kB]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main libgl1-mesa-dri 6.5.2-3ubuntu8 [13.3MB]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main libgl1-mesa-glx 6.5.2-3ubuntu8 [143kB]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main libglu1-mesa-dev 6.5.2-3ubuntu8 [257kB]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main libglu1-mesa 6.5.2-3ubuntu8 [239kB]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main mesa-utils 6.5.2-3ubuntu8 [45.0kB]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse flashplugin-nonfree 9.0.48.0.0ubuntu1~7.04.0 [15.5kB]
Fetched 28.7MB in 51s (554kB/s)                                                
Preconfiguring packages ...
(Reading database ... 158980 files and directories currently installed.)
Unpacking libawn0 (from .../libawn0_0.1.2+svn20070715~3v1ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libawn0_0.1.2+svn20070715~3v1ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn-svn
Preparing to replace libclamav2 0.90.2-0ubuntu1.2 (using .../libclamav2_0.90.2-0ubuntu1.3_i386.deb) ...
Unpacking replacement libclamav2 ...
Preparing to replace clamav-base 0.90.2-0ubuntu1.2 (using .../clamav-base_0.90.2-0ubuntu1.3_all.deb) ...
Unpacking replacement clamav-base ...
Preparing to replace clamav-freshclam 0.90.2-0ubuntu1.2 (using .../clamav-freshclam_0.90.2-0ubuntu1.3_i386.deb) ...
 * Stopping ClamAV virus database updater freshclam                      [ OK ] 
Unpacking replacement clamav-freshclam ...
Preparing to replace clamav 0.90.2-0ubuntu1.2 (using .../clamav_0.90.2-0ubuntu1.3_i386.deb) ...
Unpacking replacement clamav ...
Preparing to replace clamav-daemon 0.90.2-0ubuntu1.2 (using .../clamav-daemon_0.90.2-0ubuntu1.3_i386.deb) ...
 * Stopping ClamAV daemon clamd                                          [ OK ] 
Unpacking replacement clamav-daemon ...
Preparing to replace clamav-docs 0.90.2-0ubuntu1.2 (using .../clamav-docs_0.90.2-0ubuntu1.3_all.deb) ...
Unpacking replacement clamav-docs ...
Preparing to replace clamtk 2.31-0ubuntu1 (using .../clamtk_2.32-1~feisty1_all.deb) ...
Unpacking replacement clamtk ...
Preparing to replace libdecoration0-dev 1:0.5.1+git20070712~3v1ubuntu0 (using .../libdecoration0-dev_1%3a0.5.1+git20070716~3v1ubuntu0_i386.deb) ...
Unpacking replacement libdecoration0-dev ...
Preparing to replace libdecoration0 1:0.5.1+git20070712~3v1ubuntu0 (using .../libdecoration0_1%3a0.5.1+git20070716~3v1ubuntu0_i386.deb) ...
Unpacking replacement libdecoration0 ...
Preparing to replace libgl1-mesa-dev 6.5.2-3ubuntu7 (using .../libgl1-mesa-dev_6.5.2-3ubuntu8_all.deb) ...
Unpacking replacement libgl1-mesa-dev ...
Preparing to replace mesa-common-dev 6.5.2-3ubuntu7 (using .../mesa-common-dev_6.5.2-3ubuntu8_all.deb) ...
Unpacking replacement mesa-common-dev ...
Preparing to replace libgl1-mesa-dri 6.5.2-3ubuntu7 (using .../libgl1-mesa-dri_6.5.2-3ubuntu8_i386.deb) ...
Unpacking replacement libgl1-mesa-dri ...
Preparing to replace libgl1-mesa-glx 6.5.2-3ubuntu7 (using .../libgl1-mesa-glx_6.5.2-3ubuntu8_i386.deb) ...
Unpacking replacement libgl1-mesa-glx ...
Preparing to replace libglu1-mesa-dev 6.5.2-3ubuntu7 (using .../libglu1-mesa-dev_6.5.2-3ubuntu8_i386.deb) ...
Unpacking replacement libglu1-mesa-dev ...
Preparing to replace libglu1-mesa 6.5.2-3ubuntu7 (using .../libglu1-mesa_6.5.2-3ubuntu8_i386.deb) ...
Unpacking replacement libglu1-mesa ...
Preparing to replace compiz-plugins 1:0.5.1+git20070712~3v1ubuntu0 (using .../compiz-plugins_1%3a0.5.1+git20070716~3v1ubuntu0_i386.deb) ...
Unpacking replacement compiz-plugins ...
Preparing to replace mesa-utils 6.5.2-3ubuntu7 (using .../mesa-utils_6.5.2-3ubuntu8_i386.deb) ...
Unpacking replacement mesa-utils ...
Preparing to replace compiz-core 1:0.5.1+git20070712~3v1ubuntu0 (using .../compiz-core_1%3a0.5.1+git20070716~3v1ubuntu0_i386.deb) ...
Unpacking replacement compiz-core ...
Preparing to replace compiz-gnome 1:0.5.1+git20070712~3v1ubuntu0 (using .../compiz-gnome_1%3a0.5.1+git20070716~3v1ubuntu0_i386.deb) ...

Unpacking replacement compiz-gnome ...
Preparing to replace compiz 1:0.5.1+git20070712~3v1ubuntu0 (using .../compiz_1%3a0.5.1+git20070716~3v1ubuntu0_all.deb) ...
Unpacking replacement compiz ...
Preparing to replace compiz-dev 1:0.5.1+git20070712~3v1ubuntu0 (using .../compiz-dev_1%3a0.5.1+git20070716~3v1ubuntu0_i386.deb) ...
Unpacking replacement compiz-dev ...
Preparing to replace compiz-fusion-plugins-main 0.0.1+git20070712~3v1ubuntu0 (using .../compiz-fusion-plugins-main_0.0.1+git20070716~3v1ubuntu0_i386.deb) ...
Unpacking replacement compiz-fusion-plugins-main ...
Preparing to replace compiz-fusion-plugins-extra 0.0.1+git20070711~3v1ubuntu0 (using .../compiz-fusion-plugins-extra_0.0.1+git20070717~3v1ubuntu0_i386.deb) ...
Unpacking replacement compiz-fusion-plugins-extra ...
Preparing to replace compiz-fusion-plugins-unofficial 0.0.1+git20070711~3v1ubuntu0 (using .../compiz-fusion-plugins-unofficial_0.0.1+git20070716~3v1ubuntu0_i386.deb) ...
Unpacking replacement compiz-fusion-plugins-unofficial ...
Preparing to replace compiz-fusion-plugins-unsupported 0.0.1+git20070711~3v1ubuntu0 (using .../compiz-fusion-plugins-unsupported_0.0.1+git20070716~3v1ubuntu0_i386.deb) ...
Unpacking replacement compiz-fusion-plugins-unsupported ...
Preparing to replace compizconfig-settings-manager 0.1.0+git20070712~3v1ubuntu0 (using .../compizconfig-settings-manager_0.1.0+git20070715~3v1ubuntu0_i386.deb) ...
Unpacking replacement compizconfig-settings-manager ...
Preparing to replace flashplugin-nonfree 9.0.31.0.2ubuntu1 (using .../flashplugin-nonfree_9.0.48.0.0ubuntu1~7.04.0_i386.deb) ...
Unpacking replacement flashplugin-nonfree ...
Preparing to replace libcompizconfig0-dev 0.0.1+git20070711~3v1ubuntu0 (using .../libcompizconfig0-dev_0.0.1+git20070716~3v1ubuntu0_i386.deb) ...
Unpacking replacement libcompizconfig0-dev ...
Preparing to replace libcompizconfig0 0.0.1+git20070711~3v1ubuntu0 (using .../libcompizconfig0_0.0.1+git20070716~3v1ubuntu0_i386.deb) ...
Unpacking replacement libcompizconfig0 ...
Errors were encountered while processing:
 /var/cache/apt/archives/libawn0_0.1.2+svn20070715~3v1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/INDENT]

please please help me out.

---

### Post by 505 on 2007-07-17
Try to run this command first:

sudo dpkg --force-overwrite -i /var/cache/apt/archives/libawn0_0.1.2+svn20070715~3v1ubuntu1_i386.deb

It will install libawn0 and force the overwrite of files belonging to another package. Than run your command again.

---

