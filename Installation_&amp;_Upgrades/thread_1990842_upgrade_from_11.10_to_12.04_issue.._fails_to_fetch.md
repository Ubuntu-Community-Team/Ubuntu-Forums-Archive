---
title: "upgrade from 11.10 to 12.04 issue.. fails to fetch upgrade tool"
date: 2012-05-29
forum: Installation &amp; Upgrades
---

### Post by sodoscar on 2012-05-29
Hi there,

having a frustrating little problem which I know is got to be a simple fix but i'm buggered if I can make it happen.

When issuing the command: 
```
sudo do-release-upgrade -d
```I get the following error:

```
sod@theta:~$ sudo do-release-upgrade 
Checking for a new ubuntu release
Err Upgrade tool signature                                                                                              
  Connection failed                                                                                                     
Get:1 Upgrade tool [5612 kB]                                                                                            
Fetched 5612 kB in 0s (0 B/s)                                                                                           
WARNING:root:file 'precise.tar.gz.gpg' missing
Failed to fetch
Fetching the upgrade failed. There may be a network problem. 
```This is whats in my /var/lib/update-manager/meta-release for 12.04:
```
Dist: precise
Name: Precise Pangolin
Version: 12.04 LTS
Date: Thu, 26 Apr 2012 12:04:00 UTC
Supported: 1
Description: This is the 12.04 LTS release
Release-File: http://archive.ubuntu.com/ubuntu/dists/precise/Release
ReleaseNotes: http://archive.ubuntu.com/ubuntu/dists/precise/main/dist-upgrader-all/current/ReleaseAnnouncement
ReleaseNotesHtml: http://archive.ubuntu.com/ubuntu/dists/precise/main/dist-upgrader-all/current/ReleaseAnnouncement.html
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/precise/main/dist-upgrader-all/current/precise.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/precise/main/dist-upgrader-all/current/precise.tar.gz.gpg

```A few things to note:


[LIST=1]
[*]I have update-manager installed and current
[*]I  have followed an upgrade path from 9.10 (10.04,10.10,11.04,11.10) and  met this same problem every step of the way.  I got around it the last  few times by changing updating Prompt=lts to Prompt=normal in  /etc/update-manager/release-upgrades and adding the -d switch to the end  of the do-release-upgrade command.  I might have done other things but  my memory fails me here.
[*]I have run : sudo apt-get update && sudo apt-get upgrade
[*]There  is nothing wrong with my network.  Everything else works as it should,  this server is online and reads other repos without incident.
[/LIST]
It  has to be the upgrader tool address I'm thinking, but changing the  address to point to nz.archive.ubuntu  ...etc...  doesn't work either.

any ninja's out there know whats up?

---

### Post by sodoscar on 2012-05-30
?

---

### Post by sodoscar on 2012-06-01
Ok for those with similar issues heres what solved my problem:

I am based in NZ and use the NZ mirror site for most of my updates/upgrades/source.

by opening up my apt-sources list:

```
sudo vi /etc/apt/sources.list
```and changing it to point to the main ubuntu mirrors... i.e. dropping the country code prefix, in this case "nz." it now works fine.  

I will revert back to the NZ mirrors once the upgrade is completed, so this is just a temporary change, but alas a necessary one in this instance.

---

