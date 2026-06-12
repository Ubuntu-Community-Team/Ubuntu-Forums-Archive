---
title: "apt-get error: E:Dynamic MMap ran out of room"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by mpgarate on 2007-06-06
I get errors when I run sudo apt-get update in the terminal, and when I click to update my system (the little orange icon) I get this error:

> 'E:Dynamic MMap ran out of room, E:Error occurred while processing xpaint (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

cant upgrade or install anything! please help!

---

### Post by arkham on 2007-06-07
Looks like the cache is not large enough.  Try putting this in /etc/apt/apt.conf and the problem should go away:

```
APT::Cache-Limit 12582912;
```

If not (wow) then try a higher value like 33554432.

---

### Post by mpgarate on 2007-06-07
after searching around, i found people saying that. I tried a few bigger values with no luck. I just re-installed...

good thing I keep all my media on a seperate partition

---

### Post by uberg on 2007-06-16
i am getting this same error message now too.  Wonder if there are any other solutions to this rather that reinstall?  i do keep my /home files on a separate  partition but  a reinstall seems a bit radical.

---

### Post by aliov_85 on 2007-06-16
Hello every body, I'm getting the same error, i also tried instructions added to replies like:

"APT::Cache-Limit 12582912;"
But when I do "sudo apt-get update" i've problem:

"Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Translation-en_US          
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Translation-en_US                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Translation-en_US    
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Translation-en_US              
Get:4 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/multiverse Translation-en_US           
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/restricted Translation-en_US           
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release                         
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/universe Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Translation-en_US      
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Translation-en_US          
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/main Translation-en_US                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Translation-en_US      
Get:7 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates/multiverse Translation-en_US   
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates/restricted Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release                           
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates/universe Translation-en_US     
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release                         
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages             
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/multiverse Packages                    
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/restricted Packages                    
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/universe Packages                      
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/main Packages                          
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates/multiverse Packages            
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates/main Packages
99% [Connecting to packages.freecontrib.org (88.191.33.6)]"

and the terminal is blocked by the last line.

Thanks for any help

---

### Post by Bobba on 2007-06-17
Same error :(
Tried renaming status file 
$ sudo mv /var/lib/dpkg/status-old status
but that didnt work

$ sudo apt-get
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_GB             
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_GB        
Get: 3 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]         
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_GB        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Translation-en_GB                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Translation-en_GB           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release                                
Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_GB    
Get: 5 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]       
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_GB      
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages                      
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
Get: 6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_GB        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Sources                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Sources           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Sources           
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Ign [http://debian.slimdevices.com](http://debian.slimdevices.com) stable Release.gpg                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_GB  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_GB
Get: 7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_GB
Get: 8 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_GB
Ign [http://debian.slimdevices.com](http://debian.slimdevices.com) stable/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_GB
Get: 9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_GB
Hit [http://debian.slimdevices.com](http://debian.slimdevices.com) stable Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_GB
Get: 10 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_GB
Ign [http://debian.slimdevices.com](http://debian.slimdevices.com) stable/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_GB
Get: 11 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_GB
Hit [http://debian.slimdevices.com](http://debian.slimdevices.com) stable/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_GB
Get: 12 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_GB
Get: 13 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Fetched 13B in 3s (4B/s) 
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing ri1.9 (NewFileVer1)
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by xnszxdotnet on 2007-06-24
> **arkham said:**
> Looks like the cache is not large enough.  Try putting this in /etc/apt/apt.conf and the problem should go away:

```
APT::Cache-Limit 12582912;
```

If not (wow) then try a higher value like 33554432.

I tried the Cache-Limit 12582912 and the same error than I bumped it up to 33554432 and everything seems to be fine now.

---

### Post by Bobba on 2007-07-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/update-manager/+bug/120900](https://bugs.launchpad.net/update-manager/+bug/120900) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				33554432 did the trick :)
Note that I had to create /etc/apt/apt.conf as it did not previously exist

---

### Post by Exile29 on 2007-07-22
33554432 worked for me too.
Thanks!

---

### Post by crazy_j on 2007-08-16
After I place in the "fix" into my sources.list file, I get the following error after running the apt-get update command: 
E: Type 'APT::Cache-Limit' is not known on line 1 in source list /etc/apt/sources.list

Am I placing the command "APT::Cache-Limit 33554432;" at the wrong location?

---

### Post by forestpixie on 2007-08-16
> **arkham said:**
> Looks like the cache is not large enough.  Try putting this in [COLOR="Red"]/etc/apt/apt.conf [/COLOR]and the problem should go away:

```
APT::Cache-Limit 12582912;
```

If not (wow) then try a higher value like 33554432.

wrong file - remove it from your sources.list and put it in this one

---

### Post by rohit raj on 2007-09-25
i ubuntu 7.04 there is no apt.conf file rather a folder apt.conf.d , so where we do have to put this
apt cache thing

---

### Post by alanapost on 2007-10-01
> **arkham said:**
> Looks like the cache is not large enough.  Try putting this in /etc/apt/apt.conf and the problem should go away:

```
APT::Cache-Limit 12582912;
```

If not (wow) then try a higher value like 33554432.

i don't understand how to add lines to apt.conf. it is read-only via GUI and i do not know how to accomplish the edit via terminal.

---

### Post by forestpixie on 2007-10-01
if you need to edit a file,

do gksudo gedit

for instance to edit you sources list and save it

```
gksudo gedit /etc/apt/sources.list
```

you could of course put any file that you can edit in place of /etc/apt/sources.list

---

### Post by Starhawk99 on 2008-03-02
I'm getting the same error, but I a newbie and don't understand how to add this line 'APT::Cache-Limit 12582912'.  I can find /etc/apt/ but don't have a apf.conf in there. there is a apt.conf.d, but do i open this and type in command?

---

### Post by dhoskin on 2008-04-19
33554432 worked for me too.
Thanks!

---

### Post by netpumber on 2008-07-03
> **rohit raj said:**
> i ubuntu 7.04 there is no apt.conf file rather a folder apt.conf.d , so where we do have to put this
apt cache thing

Just do : 

```
nano apt.conf 
```

and add this :
```

APT::Cache-Limit 33554432;
```

This works for me .

---

