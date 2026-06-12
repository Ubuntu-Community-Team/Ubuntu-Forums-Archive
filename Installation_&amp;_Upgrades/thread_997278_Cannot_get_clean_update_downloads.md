---
title: "Cannot get clean update downloads"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by Mykewl on 2008-11-29
Hi,
Every time I download updates I get some type or 
error/errors. These have included cannot fetch repository,
script errors, corrupted files. Some i cannot fix.
I also get periodic download speeds of around 
30 kB/s.
I have replaced both memory and hard drive.
What can I do to eliminate this problem.

---

### Post by falcon61102 on 2008-11-29
You could attempt to download either the 8.10 Desktop ISO or the Alternate CD ISO and either do a fresh install with the Desktop CD or Upgrade using the Alternate CD.  Seeing that you're having problems with the Upgrade already, you may want to go with the fresh install.

---

### Post by dimre01 on 2008-12-20
Hey,


I'm having the same problem. When downloading updates or new programs in Ubuntu 8.10, I'm lucky if I can get a download speed of 30 kb/s. Firefox works great, normal speed on downloading and browsing. I am using a wired interet connection on my machine.

Any way to improve download speeds for downloading programs/installing updates?

Thanks in advance

---

### Post by Partyboi2 on 2008-12-20
> **dimre01 said:**
> Hey,


I'm having the same problem. When downloading updates or new programs in Ubuntu 8.10, I'm lucky if I can get a download speed of 30 kb/s. Firefox works great, normal speed on downloading and browsing. I am using a wired interet connection on my machine.

Any way to improve download speeds for downloading programs/installing updates?

Thanks in advance
Try changing your download server in Software Sources (System>Admin>Software Sources>first tab)

---

### Post by Mykewl on 2009-01-03
Done a fresh install. After doing an apt-get update I get:

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages [4542kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources [1981kB]             
72% [1 Packages bzip2 4943872] [2 Sources 211506/1981kB 10%]        120kB/s 14s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages                       
  Sub-process bzip2 returned an error code (2)
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages [199kB]           
97% [2 Sources bzip2 0] [3 Packages 0/199kB 0%]                      208kB/s 0s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources                        
  Sub-process bzip2 returned an error code (2)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Sources             
Fetched 6722kB in 34s (196kB/s)                                                
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

Have tried many repository servers.

---

### Post by Mykewl on 2009-01-04
Bump

---

