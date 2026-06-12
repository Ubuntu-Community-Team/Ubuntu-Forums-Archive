---
title: "Error authenticating some packages dueing upgrade from 14.04 LTS to 15"
date: 2016-01-23
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2016-01-23
As there is no alternate release any longer and I need to configure my installation with RAID, I installed the 14.04 LTS server edition.

I then installed the ubuntu-desktop and everything went as expected.

When I try to upgrade to 15, I get an error regarding package authentication (see attached).

I´ve tried different servers but the result is always the same.

There are a number of suggested work arounds. but they all involve the disabling of the check, which doens'sound like the right thing to do.

---

### Post by Vladlenin5000 on 2016-01-24
Before trying the release upgrade make sure you have _everything_ updated:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by lister171254 on 2016-01-24
Done.

The outcome is the same

---

### Post by MangledLinux on 2016-01-24
I'm having the same issue as well. I've attempted the update and upgrade commands and that did not fix my issue either. Any help would be appreciated. I'll continue to try fixing it also and if I come up with a solution I'll post here.

---

### Post by siepo on 2016-01-25
14.04 to 15? That is not a supported upgrade path. 14.04 => 14.10 => 15.04 [=> 15.10] is.

---

### Post by kansasnoob on 2016-01-25
> **siepo said:**
> 14.04 to 15? That is not a supported upgrade path. 14.04 => 14.10 => 15.04 [=> 15.10] is.

They changed that:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1497024](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1497024)

[ATTACH=CONFIG]266946[/ATTACH]

But the process is known to fail:

[https://bugs.launchpad.net/ubuntu/trusty/+source/apt/+bug/1497688](https://bugs.launchpad.net/ubuntu/trusty/+source/apt/+bug/1497688)

Regardless of that, there is a good reason that the update manager is set by default to upgrade from LTS to LTS rather than LTS to any release. For instance 15.04 (Vivid) will be EOL in just a few days:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

So even if you manage to get this worked out you'll need to upgrade again the 4th of February. It really is best to not change default settings until you've found out what the results of doing so might be.

---

### Post by Bashing-om on 2016-01-25
@kansasnoob; :)

Good to know info ! Glad you said.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]all in this together
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lister171254 on 2016-02-05
Thanks for the replies. 

My point/question  around the fact that I use the Software updater (see attached) and it determines the upgrade.

Given one of the previous replies, how do I go from 14.04 to 14.10, to 15...

Thanks

---

### Post by Bashing-om on 2016-02-05
lister171254; Well;

The hard way:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
make sure the system is fully updated;
Make sure that all proprietary software is reverted to that of our software repo;
3rd party sources are disabled ;
screensaver is turned off .

The process does work
[INDENT][INDENT]not much that luck has to do with it
[/INDENT][/INDENT]

---

### Post by kansasnoob on 2016-02-05
> **lister171254 said:**
> Thanks for the replies. 

My point/question  around the fact that I use the Software updater (see attached) and it determines the upgrade.

Given one of the previous replies, how do I go from 14.04 to 14.10, to 15...

Thanks

If you took time to look at my post following that advice you'd see it's no longer accurate advice. I posted more this AM:

[http://ubuntuforums.org/showthread.php?t=2312528](http://ubuntuforums.org/showthread.php?t=2312528)

I'm very curious though, why would you want to upgrade from Trusty which is supported until April 2019 to Wily which is only supported until this July?

I guess we'd need more details regarding exactly which packages fail authentication. Have you possibly borked your software sources?

---

### Post by kansasnoob on 2016-02-05
> **Bashing-om said:**
> lister171254; Well;

The hard way:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
make sure the system is fully updated;
Make sure that all proprietary software is reverted to that of our software repo;
3rd party sources are disabled ;
screensaver is turned off .

The process does work
[INDENT][INDENT]not much that luck has to do with it
[/INDENT][/INDENT]

Why in the world would you recommend the EOL upgrade process for a 14.04.* to 15.10 upgrade?

---

### Post by Bashing-om on 2016-02-05
> **kansasnoob said:**
> Why in the world would you recommend the EOL upgrade process for a 14.04.* to 15.10 upgrade?

I do not " recommend"  .. I do concur with your advise, but just answering the OP's request .

Be careful what you ask for
[INDENT][INDENT][INDENT]just may get it ( ??)
[/INDENT][/INDENT][/INDENT]

---

### Post by lister171254 on 2016-02-05
This particular computer is one of my home computers, so I want to have some of the tools/features/etc. I use on the latest version.

Also keep in mind, that the only reason I'm on the LTS is that the standard desktop doesn't support the partition configurations I want (i.e Raid)

In general, I've always upgraded to the latest version on my home computers around a months after they became available and never had any issues with this approach (apart from Nvidia graphics issues)

The screenshot shows which packages are causing issues. Maybe its got something to do with first installing the server version and then the desktop

---

### Post by kansasnoob on 2016-02-05
Well then let's look at the output of a few commnds to see if there are any errors.

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

```
sudo apt-get -f install
```

Then this one installs 'ubuntu-desktop' using tasksel which does a more complete job of adding all depends/recommends as I assume you're using the Unity DE. Is that correct? If not skip this and tell us what DE you are using:

```
sudo apt-get install ubuntu-desktop^
```

The output from that last command will probably be too long to copy-n-paste here so you can create an output text file of any of the above using "> anyname.txt", eg;

```
lance@lance-desktop:~$ sudo apt-get moo
                 (__) 
                 (oo) 
           /------\/ 
          / |    ||   
         *  /\---/\ 
            ~~   ~~   
..."Have you mooed today?"...
lance@lance-desktop:~$ sudo apt-get moo > moo.txt
lance@lance-desktop:~$ ls
Desktop    Downloads  **[COLOR="#FF0000"]moo.txt[/COLOR]**  Pictures  Templates
Documents  lshw.txt   Music    Public    Videos

```

See the moo.txt in home?

[ATTACH=CONFIG]267141[/ATTACH]

Please do copy-n-paste the errors or full text here [using code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168") as it makes it infinitely easier for us to read and try to figure out what's up.

---

### Post by lister171254 on 2016-02-05
Results follow. 

```
llist@LeosLinux:~$ sudo apt-get update

Ign http://au.archive.ubuntu.com trusty InRelease
Get:1 http://au.archive.ubuntu.com trusty-updates InRelease [64.4 kB]          
Get:2 http://au.archive.ubuntu.com trusty-backports InRelease [64.5 kB]        
Hit http://security.ubuntu.com trusty-security InRelease                       
Hit http://au.archive.ubuntu.com trusty Release.gpg                            
Get:3 http://au.archive.ubuntu.com trusty-updates/main Sources [250 kB]        
Hit http://security.ubuntu.com trusty-security/main Sources                    
Get:4 http://au.archive.ubuntu.com trusty-updates/restricted Sources [5,359 B] 
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Get:5 http://au.archive.ubuntu.com trusty-updates/universe Sources [148 kB]    
Hit http://www.bchemnet.com debian InRelease                                 
Get:6 http://au.archive.ubuntu.com trusty-updates/multiverse Sources [5,151 B] 
Get:7 http://au.archive.ubuntu.com trusty-updates/main amd64 Packages [695 kB] 
Hit http://security.ubuntu.com trusty-security/universe Sources               
Hit http://www.bchemnet.com debian/extra amd64 Packages                        
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://www.bchemnet.com debian/extra i386 Packages                         
Get:8 http://au.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Get:9 http://au.archive.ubuntu.com trusty-updates/universe amd64 Packages [336 kB]
Hit http://www.bchemnet.com debian/extra Translation-en_AU                     
Get:10 http://au.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13.0 kB]
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Get:11 http://au.archive.ubuntu.com trusty-updates/main i386 Packages [670 kB] 
Hit http://www.bchemnet.com debian/extra Translation-en                        
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages   
Hit http://security.ubuntu.com trusty-security/main i386 Packages           
Get:12 http://au.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Get:13 http://au.archive.ubuntu.com trusty-updates/universe i386 Packages [337 kB]
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Get:14 http://au.archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.2 kB]
Get:15 http://au.archive.ubuntu.com trusty-updates/main Translation-en [352 kB]
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Get:16 http://au.archive.ubuntu.com trusty-updates/multiverse Translation-en [6,832 B]
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Get:17 http://au.archive.ubuntu.com trusty-updates/restricted Translation-en [3,699 B]
Get:18 http://au.archive.ubuntu.com trusty-updates/universe Translation-en [179 kB]
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Get:19 http://au.archive.ubuntu.com trusty-backports/main Sources [8,232 B]    
Get:20 http://au.archive.ubuntu.com trusty-backports/restricted Sources [28 B]
Hit http://security.ubuntu.com trusty-security/universe Translation-en 
Get:21 http://au.archive.ubuntu.com trusty-backports/universe Sources [33.2 kB]
Get:22 http://au.archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B]
Get:23 http://au.archive.ubuntu.com trusty-backports/main amd64 Packages [9,402 B]
Get:24 http://au.archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Get:25 http://au.archive.ubuntu.com trusty-backports/universe amd64 Packages [39.8 kB]
Get:26 http://au.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1,571 B]
Get:27 http://au.archive.ubuntu.com trusty-backports/main i386 Packages [9,426 B]
Get:28 http://au.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:29 http://au.archive.ubuntu.com trusty-backports/universe i386 Packages [39.8 kB]
Get:30 http://au.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,552 B]
Get:31 http://au.archive.ubuntu.com trusty-backports/main Translation-en [5,561 B]
Get:32 http://au.archive.ubuntu.com trusty-backports/multiverse Translation-en [1,215 B]
Get:33 http://au.archive.ubuntu.com trusty-backports/restricted Translation-en [14 B]
Get:34 http://au.archive.ubuntu.com trusty-backports/universe Translation-en [34.6 kB]
Hit http://au.archive.ubuntu.com trusty Release         
Hit http://au.archive.ubuntu.com trusty/main Sources
Hit http://au.archive.ubuntu.com trusty/restricted Sources
Hit http://au.archive.ubuntu.com trusty/universe Sources
Hit http://au.archive.ubuntu.com trusty/multiverse Sources
Hit http://au.archive.ubuntu.com trusty/main amd64 Packages
Hit http://au.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://au.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://au.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://au.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://au.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://au.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://au.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://au.archive.ubuntu.com trusty/main Translation-en_AU                 
Hit http://au.archive.ubuntu.com trusty/main Translation-en                    
Hit http://au.archive.ubuntu.com trusty/multiverse Translation-en_AU           
Hit http://au.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://au.archive.ubuntu.com trusty/restricted Translation-en_AU           
Hit http://au.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://au.archive.ubuntu.com trusty/universe Translation-en_AU             
Hit http://au.archive.ubuntu.com trusty/universe Translation-en                
Fetched 3,360 kB in 8s (397 kB/s)                                              
Reading package lists... Done

```
```
llist@LeosLinux:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-image-3.19.0-25-generic linux-image-extra-3.19.0-25-generic
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

```
llist@LeosLinux:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-image-3.19.0-25-generic linux-image-extra-3.19.0-25-generic
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```


```
llist@LeosLinux:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-image-3.19.0-25-generic linux-image-extra-3.19.0-25-generic
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

```
llist@LeosLinux:~$ sudo apt-get moo
                 (__) 
                 (oo) 
           /------\/ 
          / |    ||   
         *  /\---/\ 
            ~~   ~~   
..."Have you mooed today?"...
```

---

### Post by kansasnoob on 2016-02-06
That all looks perfectly fine to me. I think I'd try using the terminal to upgrade:

```
sudo do-release-upgrade
```

I ran a quick test just to show you what to expect. Notice at the very end you can either give the go ahead (y), quit (n), or request details (d) so if anything looks funky at all just copy-n-paste the results here so we can try to figure it out:

```
lance@lance-AMD-desktop:~$ sudo do-release-upgrade
[sudo] password for lance: 
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [198 B]                                           
Get:2 Upgrade tool [1,229 kB]                                                  
Fetched 1,229 kB in 0s (0 B/s)                                                 
authenticate 'wily.tar.gz' against 'wily.tar.gz.gpg' 
extracting 'wily.tar.gz'

Reading cache

Checking package manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Hit http://security.ubuntu.com trusty-security InRelease                       
Ign http://us.archive.ubuntu.com trusty InRelease                              
Get:1 http://us.archive.ubuntu.com trusty-updates InRelease [64.4 kB]          
Get:2 http://archive.ubuntu.com trusty-proposed InRelease [212 kB]             
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://extras.ubuntu.com trusty Release.gpg                                
Get:3 http://us.archive.ubuntu.com trusty-backports InRelease [64.5 kB]        
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://security.ubuntu.com trusty-security/universe Sources                
Get:4 http://us.archive.ubuntu.com trusty-updates/main Sources [250 kB]        
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Get:5 http://archive.ubuntu.com trusty-proposed/main amd64 Packages [150 kB]   
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Err http://extras.ubuntu.com trusty/main Translation-en_US                     
                                                                               
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Err http://extras.ubuntu.com trusty/main Translation-en                        
                                                                               
Get:6 http://us.archive.ubuntu.com trusty-updates/restricted Sources [5,359 B] 
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Get:7 http://us.archive.ubuntu.com trusty-updates/universe Sources [148 kB]    
Err http://extras.ubuntu.com trusty/main Translation-en_US                     
                                                                               
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Err http://extras.ubuntu.com trusty/main Translation-en                        
                                                                               
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Get:8 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,151 B] 
Err http://extras.ubuntu.com trusty/main Translation-en_US                     
                                                                               
Get:9 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [695 kB] 
Err http://extras.ubuntu.com trusty/main Translation-en                        
                                                                               
Err http://extras.ubuntu.com trusty/main Translation-en_US                     
                                                                               
Err http://extras.ubuntu.com trusty/main Translation-en                        
                                                                               
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Get:10 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:11 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [336 kB]
Get:12 http://archive.ubuntu.com trusty-proposed/restricted amd64 Packages [3,655 B]
Get:13 http://archive.ubuntu.com trusty-proposed/universe amd64 Packages [21.1 kB]
Get:14 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13.0 kB]
Get:15 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [670 kB] 
Get:16 http://archive.ubuntu.com trusty-proposed/main i386 Packages [145 kB]   
Get:17 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Get:18 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [337 kB]
Get:19 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.2 kB]
Get:20 http://us.archive.ubuntu.com trusty-updates/main Translation-en [352 kB]
Get:21 http://archive.ubuntu.com trusty-proposed/restricted i386 Packages [3,661 B]
Get:22 http://archive.ubuntu.com trusty-proposed/universe i386 Packages [21.3 kB]
Get:23 http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en [6,832 B]
Get:24 http://us.archive.ubuntu.com trusty-updates/restricted Translation-en [3,699 B]
Get:25 http://archive.ubuntu.com trusty-proposed/main Translation-en [58.8 kB] 
Get:26 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [179 kB]
Get:27 http://us.archive.ubuntu.com trusty-backports/main Sources [8,232 B]    
Get:28 http://us.archive.ubuntu.com trusty-backports/restricted Sources [28 B] 
Get:29 http://archive.ubuntu.com trusty-proposed/restricted Translation-en [746 B]
Get:30 http://us.archive.ubuntu.com trusty-backports/universe Sources [33.2 kB]
Get:31 http://us.archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B]
Get:32 http://archive.ubuntu.com trusty-proposed/universe Translation-en [17.7 kB]
Get:33 http://us.archive.ubuntu.com trusty-backports/main amd64 Packages [9,402 B]
Get:34 http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Get:35 http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages [39.8 kB]
Get:36 http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1,571 B]
Get:37 http://us.archive.ubuntu.com trusty-backports/main i386 Packages [9,426 B]
Get:38 http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:39 http://us.archive.ubuntu.com trusty-backports/universe i386 Packages [39.8 kB]
Get:40 http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,552 B]
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Err http://us.archive.ubuntu.com trusty/main Translation-en_US                 
                                                                               
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Err http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
                                                                               
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Err http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
                                                                               
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Err http://us.archive.ubuntu.com trusty/universe Translation-en_US             
                                                                               
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Err http://us.archive.ubuntu.com trusty/main Translation-en_US                 
                                                                               
Err http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
                                                                               
Err http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
                                                                               
Err http://us.archive.ubuntu.com trusty/universe Translation-en_US             
                                                                               
Err http://us.archive.ubuntu.com trusty/main Translation-en_US                 
                                                                               
Err http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
                                                                               
Err http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
                                                                               
Err http://us.archive.ubuntu.com trusty/universe Translation-en_US             
                                                                               
Err http://us.archive.ubuntu.com trusty/main Translation-en_US                 
                                                                               
Err http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
                                                                               
Err http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
                                                                               
Err http://us.archive.ubuntu.com trusty/universe Translation-en_US             
                                                                               
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 3,953 kB in 6s (22.9 MB/s)                                             
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Updating repository information
Get:1 http://us.archive.ubuntu.com wily InRelease [218 kB]                     
Get:2 http://security.ubuntu.com wily-security InRelease [64.4 kB]             
Get:3 http://archive.ubuntu.com wily-proposed InRelease [218 kB]               
Get:4 http://us.archive.ubuntu.com wily-updates InRelease [64.4 kB]            
Get:5 http://us.archive.ubuntu.com wily-backports InRelease [64.5 kB]          
Get:6 http://us.archive.ubuntu.com wily/main Sources [1,118 kB]                
Get:7 http://security.ubuntu.com wily-security/main Sources [28.3 kB]          
Get:8 http://security.ubuntu.com wily-security/restricted Sources [2,854 B]    
Get:9 http://archive.ubuntu.com wily-proposed/main amd64 Packages [36.7 kB]    
Get:10 http://security.ubuntu.com wily-security/universe Sources [7,420 B]     
Get:11 http://security.ubuntu.com wily-security/multiverse Sources [1,923 B]   
Get:12 http://archive.ubuntu.com wily-proposed/restricted amd64 Packages [28 B]
Get:13 http://us.archive.ubuntu.com wily/restricted Sources [7,181 B]          
Get:14 http://security.ubuntu.com wily-security/main amd64 Packages [90.1 kB]  
Get:15 http://archive.ubuntu.com wily-proposed/universe amd64 Packages [30.4 kB]
Get:16 http://us.archive.ubuntu.com wily/universe Sources [7,238 kB]           
Get:17 http://archive.ubuntu.com wily-proposed/main i386 Packages [36.0 kB]    
Get:18 http://archive.ubuntu.com wily-proposed/restricted i386 Packages [28 B] 
Get:19 http://archive.ubuntu.com wily-proposed/universe i386 Packages [29.7 kB]
Get:20 http://archive.ubuntu.com wily-proposed/main Translation-en [18.0 kB]   
Get:21 http://security.ubuntu.com wily-security/restricted amd64 Packages [10.9 kB]
Get:22 http://archive.ubuntu.com wily-proposed/restricted Translation-en [28 B]
Get:23 http://security.ubuntu.com wily-security/universe amd64 Packages [37.1 kB]
Get:24 http://archive.ubuntu.com wily-proposed/universe Translation-en [15.2 kB]
Get:25 http://security.ubuntu.com wily-security/multiverse amd64 Packages [5,903 B]
Get:26 http://security.ubuntu.com wily-security/main i386 Packages [88.4 kB]   
Get:27 http://security.ubuntu.com wily-security/restricted i386 Packages [10.8 kB]
Get:28 http://security.ubuntu.com wily-security/universe i386 Packages [37.1 kB]
Get:29 http://security.ubuntu.com wily-security/multiverse i386 Packages [6,076 B]
Get:30 http://security.ubuntu.com wily-security/main Translation-en [45.4 kB]  
Get:31 http://security.ubuntu.com wily-security/multiverse Translation-en [2,536 B]
Get:32 http://security.ubuntu.com wily-security/restricted Translation-en [2,666 B]
Get:33 http://security.ubuntu.com wily-security/universe Translation-en [24.8 kB]
Get:34 http://us.archive.ubuntu.com wily/multiverse Sources [178 kB]           
Get:35 http://us.archive.ubuntu.com wily/main amd64 Packages [1,420 kB]        
Get:36 http://us.archive.ubuntu.com wily/restricted amd64 Packages [15.6 kB]   
Get:37 http://us.archive.ubuntu.com wily/universe amd64 Packages [6,704 kB]    
Get:38 http://us.archive.ubuntu.com wily/multiverse amd64 Packages [138 kB]    
Get:39 http://us.archive.ubuntu.com wily/main i386 Packages [1,416 kB]         
Get:40 http://us.archive.ubuntu.com wily/restricted i386 Packages [16.0 kB]    
Get:41 http://us.archive.ubuntu.com wily/universe i386 Packages [6,701 kB]     
Get:42 http://us.archive.ubuntu.com wily/multiverse i386 Packages [139 kB]     
Get:43 http://us.archive.ubuntu.com wily/main Translation-en [839 kB]          
Get:44 http://us.archive.ubuntu.com wily/multiverse Translation-en [107 kB]    
Get:45 http://us.archive.ubuntu.com wily/restricted Translation-en [4,296 B]   
Get:46 http://us.archive.ubuntu.com wily/universe Translation-en [4,579 kB]    
Get:47 http://us.archive.ubuntu.com wily-updates/main Sources [47.1 kB]        
Get:48 http://us.archive.ubuntu.com wily-updates/restricted Sources [3,741 B]  
Get:49 http://us.archive.ubuntu.com wily-updates/universe Sources [12.8 kB]    
Get:50 http://us.archive.ubuntu.com wily-updates/multiverse Sources [1,923 B]  
Get:51 http://us.archive.ubuntu.com wily-updates/main amd64 Packages [127 kB]  
Get:52 http://us.archive.ubuntu.com wily-updates/restricted amd64 Packages [13.3 kB]
Get:53 http://us.archive.ubuntu.com wily-updates/universe amd64 Packages [54.7 kB]
Get:54 http://us.archive.ubuntu.com wily-updates/multiverse amd64 Packages [5,903 B]
Get:55 http://us.archive.ubuntu.com wily-updates/main i386 Packages [125 kB]   
Get:56 http://us.archive.ubuntu.com wily-updates/restricted i386 Packages [13.4 kB]
Get:57 http://us.archive.ubuntu.com wily-updates/universe i386 Packages [52.4 kB]
Get:58 http://us.archive.ubuntu.com wily-updates/multiverse i386 Packages [6,076 B]
Get:59 http://us.archive.ubuntu.com wily-updates/main Translation-en [61.8 kB] 
Get:60 http://us.archive.ubuntu.com wily-updates/multiverse Translation-en [2,536 B]
Get:61 http://us.archive.ubuntu.com wily-updates/restricted Translation-en [3,024 B]
Get:62 http://us.archive.ubuntu.com wily-updates/universe Translation-en [34.9 kB]
Get:63 http://us.archive.ubuntu.com wily-backports/main Sources [754 B]        
Get:64 http://us.archive.ubuntu.com wily-backports/restricted Sources [28 B]   
Get:65 http://us.archive.ubuntu.com wily-backports/universe Sources [1,808 B]  
Get:66 http://us.archive.ubuntu.com wily-backports/multiverse Sources [28 B]   
Get:67 http://us.archive.ubuntu.com wily-backports/main amd64 Packages [618 B] 
Get:68 http://us.archive.ubuntu.com wily-backports/restricted amd64 Packages [28 B]
Get:69 http://us.archive.ubuntu.com wily-backports/universe amd64 Packages [1,685 B]
Get:70 http://us.archive.ubuntu.com wily-backports/multiverse amd64 Packages [28 B]
Get:71 http://us.archive.ubuntu.com wily-backports/main i386 Packages [618 B]  
Get:72 http://us.archive.ubuntu.com wily-backports/restricted i386 Packages [28 B]
Get:73 http://us.archive.ubuntu.com wily-backports/universe i386 Packages [1,680 B]
Get:74 http://us.archive.ubuntu.com wily-backports/multiverse i386 Packages [28 B]
Get:75 http://us.archive.ubuntu.com wily-backports/main Translation-en [496 B] 
Get:76 http://us.archive.ubuntu.com wily-backports/multiverse Translation-en [28 B]
Get:77 http://us.archive.ubuntu.com wily-backports/restricted Translation-en [28 B]
Get:78 http://us.archive.ubuntu.com wily-backports/universe Translation-en [1,245 B]
Fetched 32.4 MB in 6s (597 kB/s)                                               

Checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Calculating the changes

Calculating the changes

Do you want to start the upgrade? 


44 packages are going to be removed. 383 new packages are going to be 
installed. 1343 packages are going to be upgraded. 

You have to download a total of 831 M. This download will take about 
12 minutes with your connection. 

Installing the upgrade can take several hours. Once the download has 
finished, the process cannot be canceled. 

 Continue [yN]  Details [d]n

Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 
lance@lance-AMD-desktop:~$ 

```

If you still get an authentication error I'd try the main server instead of "au", then run sudo apt-get update and try again.

---

### Post by lister171254 on 2016-02-06
Thanks. Will try this next weekend when after I get my new internet connection and will let you know

---

### Post by lister171254 on 2016-02-07
I can confirm that the following worked for me

```
sudo do-release-upgrade
```

Thanks for your help

---

