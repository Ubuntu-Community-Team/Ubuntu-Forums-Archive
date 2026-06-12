---
title: "Unable to install any software on Ubuntu 10.04"
date: 2011-06-08
forum: Installation &amp; Upgrades
---

### Post by samvedan on 2011-06-08
I am beginner in Ubuntu. I am unable to install any software. For example, whenever i try to use Ubuntu software center to install VLC media player, it shows following notice:


[I]Failed to download repository information

check your internet connection[/I] 


I searched on google about installing softwares on Ubuntu and tried to use the command i found for installing VLC media player on terminal. 
First i typed  command*     sudo apt-get update*

and i get this on my terminal -----

[I]Ign [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_IN
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Translation-en_IN
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid Release 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN             
Ign [http://189500348a1e1358e8130157eed6f0842392e18a.inspiron.dell.archive.canonical.com](http://189500348a1e1358e8130157eed6f0842392e18a.inspiron.dell.archive.canonical.com) lucid-dell Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IN
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid Release 
Ign [http://189500348a1e1358e8130157eed6f0842392e18a.inspiron.dell.archive.canonical.com/updates/](http://189500348a1e1358e8130157eed6f0842392e18a.inspiron.dell.archive.canonical.com/updates/) lucid-dell/public Translation-en_IN
Ign [http://189500348a1e1358e8130157eed6f0842392e18a.inspiron.dell.archive.canonical.com](http://189500348a1e1358e8130157eed6f0842392e18a.inspiron.dell.archive.canonical.com) lucid-dell Release
Ign [http://189500348a1e1358e8130157eed6f0842392e18a.inspiron.dell.archive.canonical.com](http://189500348a1e1358e8130157eed6f0842392e18a.inspiron.dell.archive.canonical.com) lucid-dell/public Packages
Ign [http://189500348a1e1358e8130157eed6f0842392e18a.inspiron.dell.archive.canonical.com](http://189500348a1e1358e8130157eed6f0842392e18a.inspiron.dell.archive.canonical.com) lucid-dell/public Packages
Err [http://189500348a1e1358e8130157eed6f0842392e18a.inspiron.dell.archive.canonical.com](http://189500348a1e1358e8130157eed6f0842392e18a.inspiron.dell.archive.canonical.com) lucid-dell/public Packages
  407  Proxy Authentication Required
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_IN  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg                   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Err [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
  407  Proxy Authentication Required
Err [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources
  407  Proxy Authentication Required
Err [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                   
  407  Proxy Authentication Required
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
  407  Proxy Authentication Required
W: Failed to fetch [http://189500348a1e1358e8130157eed6f0842392e18a.inspiron.dell.archive.canonical.com/updates/dists/lucid-dell/public/binary-i386/Packages.gz](http://189500348a1e1358e8130157eed6f0842392e18a.inspiron.dell.archive.canonical.com/updates/dists/lucid-dell/public/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/lucid/partner/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.canonical.com/dists/lucid/partner/binary-i386/Packages.gz](http://archive.canonical.com/dists/lucid/partner/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)  407  Proxy Authentication Required

E: Some index files failed to download, they have been ignored, or old ones used instead.


[/I]Then i typed the following command to install VLC :
[I]
sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc

[/I]Then i get the following information on terminal: 
[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vlc

[/I]Please suggest some solution.

---

### Post by marohds on 2011-06-08
Are you sure you have a working internet connection?

In that case, maybe you should try with a different repository location:

Try to change with System -> Administration -> Software Sources

then change the repository server and try another one.

---

### Post by dFlyer on 2011-06-08
Will synaptic start. If so enter vlc in the filter and try that for a download.

---

### Post by samvedan on 2011-06-08
*> **dFlyer said:**
> Will synaptic start. If so enter vlc in the filter and try that for a download.*


I tried to use synaptic, but it shows only installed softwares. Whenever i try to search anything which is not already installed there like VLC, it doesnot show any results.

---

### Post by samvedan on 2011-06-08
> **marohds said:**
> Are you sure you have a working internet connection?

In that case, maybe you should try with a different repository location:

Try to change with System -> Administration -> Software Sources

then change the repository server and try another one.


Yes, i do have a working internet connection, i have already tried your suggestion, but this didnot solve the problem.

---

### Post by samvedan on 2011-06-08
> **samvedan said:**
> Yes, i do have a working internet connection, i have already tried your suggestion, but this didnot solve the problem.
I tried to find best server from Software sources, but after all the tests the reply was unable to find serve and check your internet connection.

But i am using the internet connection and i am able to visit various websites.

Is there a different way for software sources, synaptic package manager and Ubuntu software center to connect to the internet?

---

### Post by sidzen on 2011-06-08
Double-click on this deb and after download to add to repositories 
[http://hacktolive.org/files/Super_OS_10.04_repo_v0.3.1_all.deb](http://hacktolive.org/files/Super_OS_10.04_repo_v0.3.1_all.deb)
try going to terminal and entering the standard commands
[PHP]sudo apt-get update && sudo apt-get upgrade[/PHP]Tell us what happens

---

### Post by mike_f on 2011-06-09
> **samvedan said:**
> Yes, i do have a working internet connection, i have already tried your suggestion, but this didnot solve the problem.

**Your initial post seems to show a network config problem related to an unnecessary proxy.**

Go to System > Preferences > Network Proxy and verify that your connection is set to Direct Internet. If not, change it!

Go to System > Administration > Network Tools > Devices and report the IPv4 address for the ethernet device (usually eth0).

What brand of firewall/gateway are you using? 

TIA!

---

### Post by samvedan on 2011-06-09
> **mike_f said:**
> **Your initial post seems to show a network config problem related to an unnecessary proxy.**

Go to System > Preferences > Network Proxy and verify that your connection is set to Direct Internet. If not, change it!

Go to System > Administration > Network Tools > Devices and report the IPv4 address for the ethernet device (usually eth0).

What brand of firewall/gateway are you using? 

TIA!
I tried to do what you said, and every  time the download would reach to 95% and then the note comes that "failed to download repository sources   check your internet connection"   

I dont know much about firewall/gateway, but i think it is not activated on my Dell mini inspiron.

---

### Post by samvedan on 2011-06-09
> **mike_f said:**
> **Your initial post seems to show a network config problem related to an unnecessary proxy.**

Go to System > Preferences > Network Proxy and verify that your connection is set to Direct Internet. If not, change it!

Go to System > Administration > Network Tools > Devices and report the IPv4 address for the ethernet device (usually eth0).

What brand of firewall/gateway are you using? 

TIA!
When i type sudo apt-get install vlc in terminal, it is giving the following message:

[I]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[/I]

---

### Post by marohds on 2011-06-09
> **samvedan said:**
> When i type sudo apt-get install vlc in terminal, it is giving the following message:

[I]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[/I]

This may be because apt is used in another session or terminal. If not, rebooting is the easiest way to start over again...

---

### Post by mike_f on 2011-06-10
> **samvedan said:**
> I tried to do what you said, and every  time the download would reach to 95% and then the note comes that "failed to download repository sources   check your internet connection"

**samvedan**, please take a deep breath, put down the coffee and **reread my post**. Before you download or install Anything you need to check the settings requested and report back what they are. TIA!

Go to System > Preferences > Network Proxy 
means
Click System, then move cursor over Preferences, then click Network Proxy
etc

---

### Post by wildmanne39 on 2011-06-10
> **samvedan said:**
> When i type sudo apt-get install vlc in terminal, it is giving the following message:

[I]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[/I]Hi, this last error is because you have another instance of the installer running as the other poster said, either the terminal and synaptic or software center, and as mentioned in the previous post it looks like your proxy settings are incorrect.

---

### Post by samvedan on 2011-06-13
thanks everybody, my problem is solved now. There was some problem in network proxy settings. This is solved now. i am able to install softwares now.

---

