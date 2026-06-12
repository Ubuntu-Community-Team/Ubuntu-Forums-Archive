---
title: "Bug notice when on &quot;Updating Manager&quot;"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by F8M on 2008-09-11
Can someone instruct me as to how to remove this bug. The following is the notice I received:
Traceback (most recent call last):

  File "/usr/bin/update-manager", line 91, in <module>
    controler.prepare()

  File "/usr/lib/python2.5/site-packages/DistUpgrade/DistUpgradeController.py", line 352, in prepare
    self.openCache()

  File "/usr/lib/python2.5/site-packages/DistUpgrade/DistUpgradeController.py", line 215, in openCache
    self._view.getOpCacheProgress())

  File "/usr/lib/python2.5/site-packages/DistUpgrade/DistUpgradeCache.py", line 51, in __init__
    raise CacheExceptionDpkgInterrupted, e

CacheExceptionDpkgInterrupted: E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
 
Just an extra note here, I have a dual-partition windows/Ubuntu with a Edubuntu add on.
ANY HELP WOULD BE VERY APPRECIATED - THANK YOU

---

### Post by Pumalite on 2008-09-11
sudo dpkg --configure -a

---

### Post by F8M on 2008-09-12
When I typed in "sudo dpkg --configure -a" in the terminal, it came up with 

dpkg: parse error, in file `/var/lib/dpkg/updates/0006' near line 1:
 newline in field name `more.'

Can anybody help me as to how to proceed. Thanks.

---

### Post by Pumalite on 2008-09-12
Try:
sudo apt-get -f install

---

### Post by F8M on 2008-09-12
I tried typing in "sudo apt-get update", and as a result I got the following

Ign cdrom://Edubuntu 8.04 _Hardy Heron_ - Release i386 Binary-1 (20080422) hardy/main Translation-en_US
Ign cdrom://Edubuntu 8.04 _Hardy Heron_ - Release i386 Binary-1 (20080422) hardy/restricted Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release    
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release [58.5kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages [311kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages [6636B]      
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages [91.4kB]       
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages [20.1kB]     
Fetched 487kB in 10s (44.4kB/s)                                                
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
 
And then I typed in "sudo apt-get -f install" as you mentioned. And as a result I got the following message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

So, it seems that I need to Manually run the "dpkg -- configure -a" from which I don't know how to do. I hope this INFO. is helpful in trying to get help to resolve my problem here. THANKS

---

