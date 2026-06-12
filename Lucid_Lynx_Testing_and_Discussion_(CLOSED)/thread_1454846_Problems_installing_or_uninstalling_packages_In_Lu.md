---
title: "Problems installing or uninstalling packages In Lucid Lynx"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by putush on 2010-04-15
I have been using Lucid Lynx over a week now after migrating from 9.10. Everything was working fine till I wanted to revert back to Rhythmbox as my music manager. When trying to install through the software channels (I had previously un-installed it) I was shown an error message and the install failed.

I tried doing this with numerous other packages. All of them failed to install (even through the terminal). Even uninstallations are stagnated.

All of this started since yesterday. I had an automatic update 2 days back. 

I am posting the error messages 
this is on the terminal

> putush@Putush:~$ sudo apt-get install rhythmbox
[sudo] password for putush: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-desktopcouch-records desktopcouch erlang-inets erlang-syntax-tools
  python-pycurl libsctp1 erlang-mnesia libindicate-gtk2 python-gtkspell
  couchdb-bin python-couchdb python-avahi erlang-xmerl lksctp-tools
  erlang-crypto python-egenix-mxdatetime python-egenix-mxtools erlang-ssl
  python-desktopcouch erlang-runtime-tools erlang-base erlang-public-key
  python-indicate
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  media-player-info rhythmbox-plugin-cdrecorder rhythmbox-plugins
Suggested packages:
  python-coherence brasero rhythmbox-plugin-coherence
The following NEW packages will be installed:
  media-player-info rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins
0 upgraded, 4 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 1,735kB of archives.
After this operation, 17.8MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  media-player-info rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins
Install these packages without verification [y/N]? y
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main media-player-info 6-1
  404  Not Found [IP: 111.91.91.34 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main rhythmbox 0.12.8-0ubuntu1
  404  Not Found [IP: 111.91.91.34 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main rhythmbox-plugin-cdrecorder 0.12.8-0ubuntu1
  404  Not Found [IP: 111.91.91.34 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main rhythmbox-plugins 0.12.8-0ubuntu1
  404  Not Found [IP: 111.91.91.34 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/m/media-player-info/media-player-info_6-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/m/media-player-info/media-player-info_6-1_all.deb)  404  Not Found [IP: 111.91.91.34 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox_0.12.8-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox_0.12.8-0ubuntu1_i386.deb)  404  Not Found [IP: 111.91.91.34 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox-plugin-cdrecorder_0.12.8-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox-plugin-cdrecorder_0.12.8-0ubuntu1_i386.deb)  404  Not Found [IP: 111.91.91.34 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox-plugins_0.12.8-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox-plugins_0.12.8-0ubuntu1_i386.deb)  404  Not Found [IP: 111.91.91.34 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
putush@Putush:~$ When i run apt-get update it shows:
> putush@Putush:~$ sudo apt-get update
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release.gpg
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN          

..... MANY OTHER SIMILAR.....

Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-backports/multiverse Sources            
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-backports/universe Sources              
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages                           
  404  Not Found [IP: 111.91.91.34 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Packages                     
  404  Not Found [IP: 111.91.91.34 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Sources                      
  404  Not Found [IP: 111.91.91.34 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Sources                            
  ......MANY OTHER SIMILAR......
  404  Not Found [IP: 111.91.91.34 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-backports/multiverse Sources            
  404  Not Found [IP: 111.91.91.34 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-backports/universe Sources              
  404  Not Found [IP: 111.91.91.34 80]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources              

Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found [IP: 111.91.91.34 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 111.91.91.34 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz)  404  Not Found [IP: 111.91.91.34 80]

_[U].... many other similar....._[/U]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/source/Sources.gz)  404  Not Found [IP: 111.91.91.34 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/source/Sources.gz)  404  Not Found [IP: 111.91.91.34 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
putush@Putush:~$ Please help. Thanks in advance

---

### Post by alarme on 2010-04-15
This is a problem with /etc/apt/sources.list

You are trying to reach: 
[http://in.archive.ubuntu.com/ubuntu/dists/lucid](http://in.archive.ubuntu.com/ubuntu/dists/lucid)

but the files are on:
[http://in.archive.ubuntu.com/ubuntu/ubuntu/dists/lucid](http://in.archive.ubuntu.com/ubuntu/ubuntu/dists/lucid)

To solve, try Synaptic -> Config -> Repositories 

and choose other server to reconfigure your sources.list

---

### Post by anishmangal2002 on 2010-04-15
> **alarme said:**
> This is a problem with /etc/apt/sources.list

You are trying to reach: 
[http://in.archive.ubuntu.com/ubuntu/dists/lucid](http://in.archive.ubuntu.com/ubuntu/dists/lucid)

but the files are on:
[http://in.archive.ubuntu.com/ubuntu/ubuntu/dists/lucid](http://in.archive.ubuntu.com/ubuntu/ubuntu/dists/lucid)

To solve, try Synaptic -> Config -> Repositories 

and choose other server to reconfigure your sources.list

+1
I was facing the same issue. The fix suggested here worked. 
The old sources.list was working till yesterday. Has this change been made today?

---

### Post by jpds on 2010-04-15
There appears to have been a misconfiguration on the server which was hosting [http://in.archive.ubuntu.com/](http://in.archive.ubuntu.com/) - I have notified the admin of the issue.

Temporarily, I have had in.archive.ubuntu.com pointed at London to reduce the number of affected users for now, this will be reverted when the mirror is back.

Mirror issues should be reported to mirrors -- at -- ubuntu.com in future. :)

---

### Post by putush on 2010-04-16
Thanks a lot. Then I will wait for a couple of days and retry everything then.

---

### Post by lupe on 2010-04-20
Tofay, I got a similar problem with de.archive.ubuntu.com (using apport as an example just because it is alphabetically the first):

# apt-get --download-only install apport
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libparted0
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  apport
1 upgraded, 0 newly installed, 0 to remove and 162 not upgraded.
Need to get 54.8kB of archives.
After this operation, 0B of additional disk space will be used.
**WARNING: The following packages cannot be authenticated!**
  apport
Install these packages without verification [y/N]? y
Get:1 [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid/main apport 1.13.3-0ubuntu2 [54.8kB]
Fetched 54.8kB in 0s (163kB/s)
Download complete and in download only mode

---

