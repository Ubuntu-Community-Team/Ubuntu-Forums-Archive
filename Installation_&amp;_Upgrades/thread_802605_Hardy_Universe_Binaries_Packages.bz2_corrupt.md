---
title: "Hardy Universe Binaries Packages.bz2 corrupt?"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by voidstar on 2008-05-21
Hey Everyone, I'm using Ubuntu 8.04 on a vmware instance and I'm getting the following error when I attempt to do an apt-get update:

```

sudo apt-get update
Hit http://ca.archive.ubuntu.com hardy Release.gpg
Ign http://ca.archive.ubuntu.com hardy/main Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy/restricted Translation-en_CA
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://ca.archive.ubuntu.com hardy/universe Translation-en_CA
Ign http://security.ubuntu.com hardy-security/main Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com hardy-updates Release.gpg
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy-updates/main Translation-en_CA
Ign http://security.ubuntu.com hardy-security/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy-updates/restricted Translation-en_CA
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy-updates/universe Translation-en_CA
Hit http://security.ubuntu.com hardy-security Release
Ign http://ca.archive.ubuntu.com hardy-updates/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com hardy Release
Hit http://security.ubuntu.com hardy-security/main Packages         
Hit http://ca.archive.ubuntu.com hardy-updates Release
Hit http://security.ubuntu.com hardy-security/restricted Packages   
Hit http://ca.archive.ubuntu.com hardy/main Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://ca.archive.ubuntu.com hardy/restricted Packages
Hit http://ca.archive.ubuntu.com hardy/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://ca.archive.ubuntu.com hardy/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Get:1 http://ca.archive.ubuntu.com hardy/universe Packages [4297kB]
Get:2 http://ca.archive.ubuntu.com hardy/universe Packages [4297kB]            
Hit http://ca.archive.ubuntu.com hardy/universe Sources                        
Hit http://ca.archive.ubuntu.com hardy/multiverse Packages                     
Hit http://ca.archive.ubuntu.com hardy/multiverse Sources                      
Hit http://ca.archive.ubuntu.com hardy-updates/main Packages                   
Hit http://ca.archive.ubuntu.com hardy-updates/restricted Packages             
Hit http://ca.archive.ubuntu.com hardy-updates/main Sources                    
Hit http://ca.archive.ubuntu.com hardy-updates/restricted Sources              
Hit http://ca.archive.ubuntu.com hardy-updates/universe Packages               
Hit http://ca.archive.ubuntu.com hardy-updates/universe Sources                
Hit http://ca.archive.ubuntu.com hardy-updates/multiverse Packages             
Hit http://ca.archive.ubuntu.com hardy-updates/multiverse Sources              
99% [2 Packages bzip2 17099776]                                     38.5kB/s 0s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://ca.archive.ubuntu.com hardy/universe Packages                       
  Sub-process bzip2 returned an error code (2)
Fetched 78.2kB in 57s (1361B/s)                                                
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

So I do a wget on [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2) and bzip2 -d Package.bz2 and get the following result:

```

 bzip2 -d Packages.bz2 

bzip2: Data integrity error when decompressing.
	Input file = Packages.bz2, output file = Packages

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

bzip2: Deleting output file Packages, if it exists.


```

I haven't touched my sources.list file since the base install or used synaptic or whatever the GUI thing is called.  I'm trying to install tomcat5.5 using apt-get and its failing to find it I'm guessing because of this.  Is there anything I can do to sort this out?

---

### Post by TheLions on 2008-05-21
i have similar problem too...

from my nearest server(in Croatia) sometimes it can't get data so i temporarly change the server.

you should try it too!

(System->Administration->Software repository)

---

### Post by voidstar on 2008-05-22
I've run all updates for ubuntu thinking it might have been a problem on my side but its still throwing the error this morning, I'll attempt to contact the whoever maintains the ca.archive.ubuntu.com and investigate further.  Is there a way to change which mirror I use from the command line?

---

### Post by voidstar on 2008-05-22
I've attempted to change to the main archive and tried several others and I've been getting similar errors:

```

sudo apt-get update
Get:1 http://archive.linux.duke.edu hardy Release.gpg [191B]
Ign http://archive.linux.duke.edu hardy/main Translation-en_CA
Ign http://archive.linux.duke.edu hardy/restricted Translation-en_CA
Ign http://archive.linux.duke.edu hardy/universe Translation-en_CA
Ign http://archive.linux.duke.edu hardy/multiverse Translation-en_CA
Get:2 http://archive.linux.duke.edu hardy-updates Release.gpg [191B]
Ign http://archive.linux.duke.edu hardy-updates/main Translation-en_CA
Ign http://archive.linux.duke.edu hardy-updates/restricted Translation-en_CA
Ign http://archive.linux.duke.edu hardy-updates/universe Translation-en_CA
Ign http://archive.linux.duke.edu hardy-updates/multiverse Translation-en_CA
Get:3 http://archive.linux.duke.edu hardy-security Release.gpg [191B]
Ign http://archive.linux.duke.edu hardy-security/main Translation-en_CA
Ign http://archive.linux.duke.edu hardy-security/restricted Translation-en_CA
Ign http://archive.linux.duke.edu hardy-security/universe Translation-en_CA
Ign http://archive.linux.duke.edu hardy-security/multiverse Translation-en_CA
Get:4 http://archive.linux.duke.edu hardy Release [65.9kB]                     
Get:5 http://archive.linux.duke.edu hardy-updates Release [51.2kB]             
Get:6 http://archive.linux.duke.edu hardy-security Release [44.0kB]            
Get:7 http://archive.linux.duke.edu hardy/main Packages [1178kB]               
Get:8 http://archive.linux.duke.edu hardy/restricted Packages [6986B]          
Get:9 http://archive.linux.duke.edu hardy/main Sources [338kB]                 
Get:10 http://archive.linux.duke.edu hardy/restricted Sources [1488B]          
Get:11 http://archive.linux.duke.edu hardy/universe Packages [4297kB]          
Get:12 http://archive.linux.duke.edu hardy/universe Packages [4297kB]          
Get:13 http://archive.linux.duke.edu hardy/universe Packages [4297kB]          
Get:14 http://archive.linux.duke.edu hardy/universe Packages [4297kB]          
Get:15 http://archive.linux.duke.edu hardy/universe Packages [4297kB]          
Get:16 http://archive.linux.duke.edu hardy/universe Packages [4297kB]          
Get:17 http://archive.linux.duke.edu hardy/universe Packages [4297kB]          
Get:18 http://archive.linux.duke.edu hardy/universe Packages [4297kB]          
Get:19 http://archive.linux.duke.edu hardy/universe Packages [4297kB]          
Get:20 http://archive.linux.duke.edu hardy/universe Packages [4297kB]        
Get:21 http://archive.linux.duke.edu hardy/universe Packages [4297kB]        
Get:22 http://archive.linux.duke.edu hardy/universe Packages [4297kB]        
50% [22 Packages 1314816/4297kB 30%]                535kB/s 49710d 6h28min11s


```

I've noticed that Translation-en_CA seems to be coming up so I'm going to change my language and see if this has any affect.

---

### Post by voidstar on 2008-05-22
Ok I've since attempted to change my language and change which mirror I'm using all to no avail.  I've also commented out every other repository except for the hardy universe one and its still not working.  This is my output here:

```

 sudo apt-get update
Get:1 http://ca.archive.ubuntu.com hardy Release.gpg [191B]
Ign http://ca.archive.ubuntu.com hardy/universe Translation-en_CA
Get:2 http://ca.archive.ubuntu.com hardy Release [65.9kB]
Get:3 http://ca.archive.ubuntu.com hardy/universe Packages [4297kB]
Get:4 http://ca.archive.ubuntu.com hardy/universe Packages [4297kB]            
99% [4 Packages bzip2 17554432]                                     28.3kB/s 0s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://ca.archive.ubuntu.com hardy/universe Packages                       
  Sub-process bzip2 returned an error code (2)
Fetched 142kB in 42s (3330B/s)                                                 
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I'm going to report this as a bug as I can't think of anything further to do.

---

### Post by voidstar on 2008-05-23
Ok I managed to get a workaround for this problem.  When looking at the http location of Packages.bz2 I saw there was a Packages.gz.  Grabbed this with wget and it wasn't corrupt.  I was than able to cp this file name into /var/lib/apt/lists/ as /ca.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages and it worked fine.  

I've just attempted it download the file again and it was still corrupt, at ca.archive.ubuntu.com and archive.ubuntu.com.

When downloading from both locations wget lost the connection at 98% and had to reconnect.

```

wget http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2
--09:02:43--  http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2
           => `Packages.bz2.1'
Resolving archive.ubuntu.com... 91.189.88.31, 91.189.88.45, 91.189.88.46
Connecting to archive.ubuntu.com|91.189.88.31|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,297,029 (4.1M) [text/plain]

98% [===============================================================================>  ] 4,220,842    112.38K/s    ETA 00:00

09:03:20 (132.37 KB/s) - Connection closed at byte 4220842. Retrying.

--09:03:21--  http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2
  (try: 2) => `Packages.bz2.1'
Connecting to archive.ubuntu.com|91.189.88.31|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 4,297,029 (4.1M), 76,187 (74K) remaining [text/plain]

100%[++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++=>] 4,297,029     --.--K/s             

09:03:22 (5.01 MB/s) - `Packages.bz2.1' saved [4297029/4297029]



```

---

### Post by voidstar on 2008-05-23
I've created a bug report for this:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/234324](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/234324)

---

