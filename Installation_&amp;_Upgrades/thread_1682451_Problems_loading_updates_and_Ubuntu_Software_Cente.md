---
title: "Problems loading updates and Ubuntu Software Center (new install 10.10)"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by secno76 on 2011-02-05
Greetings:

I have tried installing Ubuntu 10.10 from disk and DVD at home in VMware Player 3.1.3 with success. However, when I go to do updates, the Authenticator freezes and comes up with the following error:

```
 [I]Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_maverick_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'[/I] 
```

Ubuntu Software Center will not load (I was trying to load some tweaks in previous and current installs). I have read some other forums and have some code printouts for you.

```

root@ubuntu:~#** sudo dpkg --configure -a**
root@ubuntu:~#
root@ubuntu:~# **sudo apt-get install -f**
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_maverick_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
root@ubuntu:~#
root@ubuntu:~#** sudo apt-get update && sudo apt-get upgrade**
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg [198B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US [198B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
96% [2 Translation-en_US bzip2 0B] [Connecting to extras.ubuntu.com] [Connectinbzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US [198B]
65% [3 Translation-en_US bzip2 0B] [Waiting for headers] [Connecting to extras.bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources/DiffIndex               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources/DiffIndex         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources/DiffIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources/DiffIndex         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages/DiffIndex         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages/DiffIndex   
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages [39.8kB]    
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages [31.4kB]  
55% [4 Packages bzip2 0B] [5 Packages 0B/31.4kB 0%] [Connecting to extras.ubuntbzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages               
  Sub-process /bin/bzip2 returned an error code (2)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources/DiffIndex       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources/DiffIndex 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources/DiffIndex   
99% [5 Packages bzip2 0B] [Connecting to extras.ubuntu.com] [Connecting to secubzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages             
  Sub-process /bin/bzip2 returned an error code (2)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources/DiffIndex 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages/DiffIndex 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages/DiffIndex
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages/DiffIndex [5,791kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en           
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages/DiffIndex [183kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages     
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources [82.7kB]              
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources [778B]          
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources [29.9kB]         
2% [8 Sources lzma 0B] [10 Sources 1,234B/29.9kB 4%]/usr/bin/lzma: Decoder error
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources
  Sub-process /usr/bin/lzma returned an error code (1)
2% [9 Sources lzma 0B] [10 Sources 12.9kB/29.9kB 43%]/usr/bin/lzma: Decoder error
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
  Sub-process /usr/bin/lzma returned an error code (1)
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources [1,504B]       
2% [10 Sources lzma 0B] [11 Sources 0B/1,504B 0%]    629kB/s 49710d 6h 28min 7s/usr/bin/lzma: Decoder error
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages [226kB]        
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources                     
  Sub-process /usr/bin/lzma returned an error code (1)
3% [11 Sources lzma 0B] [12 Packages 7,008B/226kB 3%]/usr/bin/lzma: Decoder error
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
  Sub-process /usr/bin/lzma returned an error code (1)
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages [1,797B] 
6% [12 Packages lzma 0B] [13 Packages 0B/1,797B 0%]  629kB/s 49710d 6h 28min 7s/usr/bin/lzma: Decoder error
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages                   
  Sub-process /usr/bin/lzma returned an error code (1)
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources [95.5kB]     
6% [13 Packages lzma 0B] [14 Sources 747B/95.5kB 0%]/usr/bin/lzma: Decoder error
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages
  Sub-process /usr/bin/lzma returned an error code (1)
7% [14 Sources lzma 1B]                              629kB/s 49710d 6h 28min 7s/usr/bin/lzma: Decoder error
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources                 
  Sub-process /usr/bin/lzma returned an error code (1)
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources [2,836B]
7% [15 Sources lzma 119B]                            629kB/s 49710d 6h 28min 7s/usr/bin/lzma: Decoder error
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources           
  Sub-process /usr/bin/lzma returned an error code (1)
Fetched 6,487kB in 19s (331kB/s)                                               
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.lzma](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.lzma)  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.lzma](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.lzma)  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.lzma](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.lzma)  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.lzma](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.lzma)  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.lzma](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.lzma)  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.lzma](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.lzma)  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.lzma](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.lzma)  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.lzma](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.lzma)  Sub-process /usr/bin/lzma returned an error code (1)

E: Some index files failed to download, they have been ignored, or old ones used instead.
root@ubuntu:~#

```

I have tried to do what other posters have had trouble with, but nothing seems to work. This *does* work at my workplace in VM Player just fine with the same distro. The only difference I have at home is I just installed the BitDefender suite. I have allowed vmware player and I can surf to Web pages and ping DNS servers..... any ideas?

With Regards,
Shawn

---

### Post by secno76 on 2011-02-05
Had to get a smiley out from the E:Problem     :P

---

### Post by lisati on 2011-02-05
> **secno76 said:**
> I have no idea how the smiley got in my post...

Try wrapping listings in [noparse]```
 and 
```[/noparse] tags.

(BTW: why are you using **sudo** when you're already at the root prompt? [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) makes for interesting reading)

---

### Post by secno76 on 2011-02-05
I'm kinda new to the troubleshooting... just using copy and paste and/or type  :)

---

### Post by secno76 on 2011-02-05
This file does not exist, btw... what do I do?

```
 http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.lzma  
```

---

### Post by secno76 on 2011-02-06
Well, I reverted back to 10.04 and I am happy.

-Shawn

---

