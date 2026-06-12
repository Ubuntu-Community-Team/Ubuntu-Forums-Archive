---
title: "Ubuntu Update Server Connection FAILED"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by ntnwwnet on 2006-08-22
I just installed 6.06 server, and tried sudo apt-get update, I get the following error.

```
nil@guardian:~$ sudo apt-get update
Err http://security.ubuntu.com dapper-security Release.gpg                     
  Connection failed
Ign http://security.ubuntu.com dapper-security Release                         
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://security.ubuntu.com dapper-security/main Sources                    
Ign http://security.ubuntu.com dapper-security/restricted Sources              
Err http://us.archive.ubuntu.com dapper Release.gpg                            
  Connection failed
Ign http://security.ubuntu.com dapper-security/universe Packages               
Err http://us.archive.ubuntu.com dapper-updates Release.gpg                    
  Connection failed
Ign http://security.ubuntu.com dapper-security/universe Sources                
Err http://security.ubuntu.com dapper-security/main Packages                   
  Connection failed
Ign http://us.archive.ubuntu.com dapper Release                                
Err http://security.ubuntu.com dapper-security/restricted Packages             
  Connection failed
Ign http://us.archive.ubuntu.com dapper-updates Release                        
Err http://security.ubuntu.com dapper-security/main Sources                    
  Connection failed
Err http://security.ubuntu.com dapper-security/restricted Sources              
  Connection failed
Err http://security.ubuntu.com dapper-security/universe Packages               
  Connection failed
Err http://security.ubuntu.com dapper-security/universe Sources                
  Connection failed
Ign http://us.archive.ubuntu.com dapper/main Packages                          
Ign http://us.archive.ubuntu.com dapper/restricted Packages
Ign http://us.archive.ubuntu.com dapper/main Sources  
Ign http://us.archive.ubuntu.com dapper/restricted Sources
Ign http://us.archive.ubuntu.com dapper/universe Packages
Ign http://us.archive.ubuntu.com dapper/universe Sources
Ign http://us.archive.ubuntu.com dapper-updates/main Packages
Ign http://us.archive.ubuntu.com dapper-updates/restricted Packages
Ign http://us.archive.ubuntu.com dapper-updates/main Sources
Ign http://us.archive.ubuntu.com dapper-updates/restricted Sources
Err http://us.archive.ubuntu.com dapper/main Packages 
  Connection failed
Err http://us.archive.ubuntu.com dapper/restricted Packages
  Connection failed
Err http://us.archive.ubuntu.com dapper/main Sources  
  Connection failed
Err http://us.archive.ubuntu.com dapper/restricted Sources
  Connection failed
Err http://us.archive.ubuntu.com dapper/universe Packages
  Connection failed
Err http://us.archive.ubuntu.com dapper/universe Sources
  Connection failed
Err http://us.archive.ubuntu.com dapper-updates/main Packages
  Connection failed
Err http://us.archive.ubuntu.com dapper-updates/restricted Packages
  Connection failed
Err http://us.archive.ubuntu.com dapper-updates/main Sources
  Connection failed
Err http://us.archive.ubuntu.com dapper-updates/restricted Sources
  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz  Connection failed
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
nil@guardian:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nil@guardian:~$ 
```

This has happened with any alternate mirrors I try.

PLEASE help!

---

### Post by ntnwwnet on 2006-08-22
```

nil@guardian:~$ sudo apt-get update
Err http://mirror.cs.umn.edu dapper Release.gpg       
  Connection failed
Err http://mirror.cs.umn.edu dapper-updates Release.gpg
  Connection failed
Err http://mirror.cs.umn.edu dapper-security Release.gpg
  Connection failed
Ign http://mirror.cs.umn.edu dapper Release           
Ign http://mirror.cs.umn.edu dapper-updates Release   
Ign http://mirror.cs.umn.edu dapper-security Release  
Ign http://mirror.cs.umn.edu dapper/main Packages     
Ign http://mirror.cs.umn.edu dapper/restricted Packages
Ign http://mirror.cs.umn.edu dapper/universe Packages  
Ign http://mirror.cs.umn.edu dapper/multiverse Packages
Ign http://mirror.cs.umn.edu dapper-updates/main Packages
Ign http://mirror.cs.umn.edu dapper-updates/restricted Packages
Ign http://mirror.cs.umn.edu dapper-updates/universe Packages
Ign http://mirror.cs.umn.edu dapper-updates/multiverse Packages
Ign http://mirror.cs.umn.edu dapper-security/main Packages
Ign http://mirror.cs.umn.edu dapper-security/restricted Packages
Ign http://mirror.cs.umn.edu dapper-security/universe Packages
Ign http://mirror.cs.umn.edu dapper-security/multiverse Packages
Err http://mirror.cs.umn.edu dapper/main Packages      
  Connection failed
Err http://mirror.cs.umn.edu dapper/restricted Packages
  Connection failed
Err http://mirror.cs.umn.edu dapper/universe Packages  
  Connection failed
Err http://mirror.cs.umn.edu dapper/multiverse Packages
  Connection failed
Err http://mirror.cs.umn.edu dapper-updates/main Packages
  Connection failed
Err http://mirror.cs.umn.edu dapper-updates/restricted Packages
  Connection failed
Err http://mirror.cs.umn.edu dapper-updates/universe Packages
  Connection failed
Err http://mirror.cs.umn.edu dapper-updates/multiverse Packages
  Connection failed
Err http://mirror.cs.umn.edu dapper-security/main Packages
  Connection failed
Err http://mirror.cs.umn.edu dapper-security/restricted Packages
  Connection failed
Err http://mirror.cs.umn.edu dapper-security/universe Packages
  Connection failed
Err http://mirror.cs.umn.edu dapper-security/multiverse Packages
  Connection failed
Failed to fetch http://mirror.cs.umn.edu/ubuntu/dists/dapper/Release.gpg  Connection failed
Failed to fetch http://mirror.cs.umn.edu/ubuntu/dists/dapper-updates/Release.gpg  Connection failed
Failed to fetch http://mirror.cs.umn.edu/ubuntu/dists/dapper-security/Release.gpg  Connection failed
Failed to fetch http://mirror.cs.umn.edu/ubuntu/dists/dapper/main/binary-i386/Packages.gz  Connection failed
Failed to fetch http://mirror.cs.umn.edu/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  Connection failed
Failed to fetch http://mirror.cs.umn.edu/ubuntu/dists/dapper/universe/binary-i386/Packages.gz  Connection failed
Failed to fetch http://mirror.cs.umn.edu/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz  Connection failed
Failed to fetch http://mirror.cs.umn.edu/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  Connection failed
Failed to fetch http://mirror.cs.umn.edu/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz  Connection failed
Failed to fetch http://mirror.cs.umn.edu/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz  Connection failed
Failed to fetch http://mirror.cs.umn.edu/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz  Connection failed
Failed to fetch http://mirror.cs.umn.edu/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz  Connection failed
Failed to fetch http://mirror.cs.umn.edu/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz  Connection failed
Failed to fetch http://mirror.cs.umn.edu/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz  Connection failed
Failed to fetch http://mirror.cs.umn.edu/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz  Connection failed
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
nil@guardian:~$ 


```

I tried with another update server, same error.

YES, I have internet access. I can ping the default update server.

Here is a copy of the ping output.

```

root@guardian:/etc/apt# ping 146.137.96.7
PING 146.137.96.7 (146.137.96.7) 56(84) bytes of data.
64 bytes from 146.137.96.7: icmp_seq=1 ttl=50 time=85.8 ms
64 bytes from 146.137.96.7: icmp_seq=2 ttl=50 time=85.5 ms
64 bytes from 146.137.96.7: icmp_seq=3 ttl=50 time=85.9 ms
64 bytes from 146.137.96.7: icmp_seq=4 ttl=50 time=85.1 ms
64 bytes from 146.137.96.7: icmp_seq=5 ttl=50 time=85.1 ms
64 bytes from 146.137.96.7: icmp_seq=6 ttl=50 time=85.5 ms
64 bytes from 146.137.96.7: icmp_seq=7 ttl=50 time=85.8 ms
64 bytes from 146.137.96.7: icmp_seq=8 ttl=50 time=84.8 ms
64 bytes from 146.137.96.7: icmp_seq=9 ttl=50 time=85.3 ms
64 bytes from 146.137.96.7: icmp_seq=10 ttl=50 time=86.6 ms

--- 146.137.96.7 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9095ms
rtt min/avg/max/mdev = 84.863/85.591/86.642/0.622 ms

```

Here is a copy of my sources.list

```

# deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


#deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


```

---

### Post by stoush on 2006-08-26
Hi all,

I just noticed this the other day...

I had a fresh install of 6.06.1 on my computer, and did an repository refresh at a friend's place. apt-get happily did its thing no problems at all...

then i got home, and added some new stuff to my source.list file, and the connection failed msg happened exactly as you guys have decribed.

i think we can rule out the bad image, bad install etc.

the only difference between my internet and friends is that they are NOT using a separate router just the cable modem.

I am using Linksys WRT54, now under the security section there is an option "Fileter Internet NAT redirection" I disabled this and bang everything worked just fine!

So check if your router has this as a security feature and turn it off or you wont be able to secure a connection as your router simply wont let you :-)

hth:wink: 

stoush

---

### Post by Haydn on 2006-10-15
Hey,

I am experiencing problems similar to yours (at my best guess) and since there were no real responses to this with solutions, what may I ask did you do to resolve this issue?

What's happening for me is that I am receiving the notifications that updates are available fine. It will even list which updates are available. It stops short however of displaying the information in the changes tab - This is when I am using the built in software update tool. The main problem is presents when I select which updates to install and then try to 'install updates': the program will open up a 'downloading package files' window but will not ever progress in the downloads. What should I do? I only hope that somone will come across this post.

Thanks in advance,
Haydn

---

### Post by badboyz107 on 2006-10-18
I have had the same problems using the apt-get upgrade.  It retrieves the list of updates just fine but doesnt want to get the upgrades.  

I also think this is related to my router somehow (its a voip router) because if I go straight through the modem its fine.  I dont know that much about router workings though to finger this out on my own!!

](*,)

---

### Post by CypherHackz on 2008-06-07
I know this topic is old but Im facing the same problem right now. When I do the update using the Update Manager, I got all connection failed error message. I tried change the server, but still got the same error message. Does anyone know how to fix the problem?

Thank you.

-cypher.

---

