---
title: "Can't update/install packages after initial install"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by weslowsk on 2010-05-04
Hi,

I'm running Ubuntu 10.04 64 bit as a VirtualBox (3.1.6) guest.
Every time I try to run apt-get update, I get the following:


====================================================================
sudo apt-get update
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) lucid Release.gpg
Ign [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) lucid/multiverse Translation-en_CA
Hit [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) lucid/restricted Translation-en_CA
Hit [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) lucid/main Translation-en_CA
Hit [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) lucid/universe Translation-en_CA
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) lucid-updates Release.gpg
Ign [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) lucid-updates/multiverse Translation-en_CA
Ign [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) lucid-updates/restricted Translation-en_CA
Ign [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) lucid-updates/main Translation-en_CA
Ign [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) lucid-updates/universe Translation-en_CA
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) lucid-security Release.gpg
Ign [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) lucid-security/multiverse Translation-en_CA
Ign [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) lucid-security/restricted Translation-en_CA
Ign [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) lucid-security/main Translation-en_CA
Ign [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) lucid-security/universe Translation-en_CA
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) lucid Release          
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) lucid-updates Release  
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) lucid-security Release              
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) lucid/multiverse Packages           
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) lucid/restricted Packages
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) lucid/main Packages
Get:1 [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) lucid/universe Packages [5,430kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg     
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) lucid-updates/multiverse Packages             
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) lucid-updates/restricted Packages             
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) lucid-updates/main Packages                   
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) lucid-updates/universe Packages               
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) lucid-security/multiverse Packages            
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) lucid-security/restricted Packages            
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) lucid-security/main Packages                  
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) lucid-security/universe Packages              
99% [1 Packages bzip2 0B]                                            565kB/s 0s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) lucid/universe Packages                       
  Sub-process /bin/bzip2 returned an error code (2)
Fetched 5,430kB in 10s (534kB/s)                                               
W: Failed to fetch [http://mirrors.us.kernel.org/ubuntu/dists/lucid/universe/binary-amd64/Packages.bz2](http://mirrors.us.kernel.org/ubuntu/dists/lucid/universe/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)


E: Some index files failed to download, they have been ignored, or old ones used instead.
====================================================================




I tried an apt-get clean and that didn't help either...
I tried manually downloading the bz2 file that seems to be giving me problems and I could open it with the archive manager but couldn't get at any files inside of it...

any ideas?

---

### Post by weslowsk on 2010-05-06
So, I tried bzip2recover and that broke up the "corrupt" packages file into about 30 smaller ones. Now what do I do with those separate bz2 files? How do I get apt-get to use those instead of the corrupt one that I get from every mirror out there?
Why does it seem no one else has this issue with the corrupt Packages.bz2? And why only this (or a couple of files)? Does this possible have something to do with Ubuntu running in VirtualBox?

---

### Post by weslowsk on 2010-05-07
I installed to a fresh VM instance and that one works fine now...I never figured out why the old one didn't work.
Oh well...

Closing thread...

---

### Post by weslowsk on 2010-05-07
correction...it still doesn't work (I thought I had it but I was mistaken).

However, I changed the network device from Intel Pro to AMD PCNET-FAST and then it works fine...

I think I'll report it as a bug...

---

