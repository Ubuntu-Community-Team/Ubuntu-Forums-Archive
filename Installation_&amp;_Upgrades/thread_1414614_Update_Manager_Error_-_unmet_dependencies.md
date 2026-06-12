---
title: "Update Manager Error - unmet dependencies"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by Otto Mobeal on 2010-02-23
Ubuntu 9.10:  I am getting an error on the Update Manager and the Synaptic Package Manager.  Both stall.  I think it was after uploading "clamtk 4.15".  The error is shown as a screen shot in the attachment.  But it basically says:  

Could not initialize the package information

An Unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Read error - read (5:Input.output error), E: The package lists or status file could not be parsed or opened.'

This is locking my computer up - can anyone help?
Can I correct clamtk or get rid of it?

---

### Post by Otto Mobeal on 2010-03-01
HELP!:mad:
This is driving me crazy!
I ran:  '/etc/apt/sources.list'  and then 'sudo apt-get update'  Below are the results:

thekilians@thekilians-laptop:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
thekilians@thekilians-laptop:~$ sudo apt-get update
[sudo] password for thekilians: 
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Get:3 [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg [189B]
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US 
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg [189B] 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Get:5 [http://archive.canonical.com](http://archive.canonical.com) karmic Release [9,347B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/multiverse Translation-en_US
Get:7 [http://dl.google.com](http://dl.google.com) stable/main Packages [923B]                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                     
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release [44.1kB]  
Get:9 [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages [3,404B]            
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security Release [44.1kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages [184kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages [14B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources [54.4kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources [14B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages [108kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources [26.3kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages [6,930B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources [3,820B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main Packages [76.4kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/restricted Packages [14B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main Sources [22.7kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/restricted Sources [14B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/universe Packages [37.1kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/universe Sources [6,767B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/multiverse Packages [1,666B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/multiverse Sources [577B]
Fetched 634kB in 3s (196kB/s)                 
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.

---

