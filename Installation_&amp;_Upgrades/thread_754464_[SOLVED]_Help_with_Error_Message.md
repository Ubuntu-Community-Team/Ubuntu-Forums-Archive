---
title: "[SOLVED] Help with Error Message"
date: 2008-04-13
forum: Installation &amp; Upgrades
---

### Post by zombrax on 2008-04-13
G'day,

 could someone please help me with this error msg i get when trying to upgrade to newer ver or just trying to install new components from the net?

System, Administration, Update Manager 
"Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '--19:44:05--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'

could someone please tell me how to get my updates and fixing this problem?

many thanks

---

### Post by Pumalite on 2008-04-13
Post:
cat /etc/apt/sources.list

---

### Post by zombrax on 2008-04-14
sorry i'm next to a newbie. i have no idea what to do with that post you posted. i punched that line in to the terminal and it gave me a list. so how can i get the update program to get to read this file so that i can get the updates happening? 

many thanks in advance

---

### Post by Partyboi2 on 2008-04-14
> **zombrax said:**
> sorry i'm next to a newbie. i have no idea what to do with that post you posted. i punched that line in to the terminal and it gave me a list. so how can i get the update program to get to read this file so that i can get the updates happening? 

many thanks in advance

Pumalite was asking you to type that command in a terminal like you have done, then copy and paste the list (file content) here so someone can help you.

---

### Post by zombrax on 2008-04-14
zombrax@ub-lap:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free

All there and thanks to partyboi2 for telling me what to do :) many thanks once again

---

### Post by mikewhatever on 2008-04-14
It looks like the error comes from the medibuntu list. What's the output of <cat /etc/apt/sources.list.d/medibuntu.list>?

---

### Post by zombrax on 2008-04-14
zombrax@ub-lap:~$ cat /etc/apt/sources.list.d/medibuntu.list
--19:44:05--  [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
           => `feisty.list'
Connecting to 198.168.1.1:3128... failed: Connection timed out.
Retrying.

--19:45:57--  [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
  (try: 4) => `feisty.list'
Connecting to 198.168.1.1:3128... failed: Connection timed out.
Retrying.

--19:49:10--  [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
  (try: 5) => `feisty.list'
Connecting to 198.168.1.1:3128... failed: Connection timed out.
Retrying.

--19:52:24--  [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
  (try: 6) => `feisty.list'
Connecting to 198.168.1.1:3128... failed: Connection timed out.
Retrying.

--19:55:39--  [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
  (try: 7) => `feisty.list'
Connecting to 198.168.1.1:3128... failed: Connection timed out.
Retrying.

--19:58:55--  [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
  (try: 8) => `feisty.list'
Connecting to 198.168.1.1:3128... failed: Connection timed out.
Retrying.

--20:02:12--  [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
  (try: 9) => `feisty.list'
Connecting to 198.168.1.1:3128... failed: Connection timed out.
Retrying.

--20:05:30--  [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
  (try:10) => `feisty.list'
Connecting to 198.168.1.1:3128... failed: Connection timed out.
Retrying.

--20:08:49--  [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
  (try:11) => `feisty.list'
Connecting to 198.168.1.1:3128... failed: Connection timed out.
Retrying.

--20:12:08--  [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
  (try:12) => `feisty.list'
Connecting to 198.168.1.1:3128... failed: Connection timed out.
Retrying.

--20:15:27--  [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
  (try:13) => `feisty.list'
Connecting to 198.168.1.1:3128... failed: Connection timed out.
Retrying.

--20:18:48--  [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
  (try:14) => `feisty.list'
Connecting to 198.168.1.1:3128... zombrax@ub-lap:~$ 

i have to go through the college's proxy server which obviously is 198.168.1.1 port 3128

my password and username is correct.. what else can i do please?

---

### Post by mikewhatever on 2008-04-15
Run this command <sudo rm /etc/apt/sources.list.d/medibuntu.list>, then follow the procedure for Feisty of adding medibuntu repository once again. 
[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)
Then <sudo apt-get update>.
To deal with the proxy, open Synaptic, go to System>Preferences>Network and configure as required.

---

### Post by zombrax on 2008-04-16
heya.. i ran what you asked me to do.. and this is all i get

zombrax@ub-lap:~$ sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list
--16:08:13--  [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Connecting to 198.168.1.1:3128... 

and it just hangs there. my proxy is set through System, Preferences, Network Proxy. 

what else can i do guys? thanks in advance

---

### Post by zombrax on 2008-04-16
--16:21:01--  [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
  (try: 5) => `/etc/apt/sources.list.d/medibuntu.list'
Connecting to 198.168.1.1:3128... failed: Connection timed out.
Retrying.

---

### Post by blueboy21 on 2008-04-16
dear fr&#305;ends,

I am new person who wanna learn ubuntu 6.0, but &#305; have lots of problems with ubuntu:(,for example:
1)  &#305; dont know how to get install, could you tell me  how to solve this problem and couldd you tell me as if I am crayz...??
2) &#305; dont watxh youtube because it needs adobe flash player but &#305; cant  &#305;nstall it,, how to &#305;nstall??
3) &#305; wanna compile c,c++ but also &#305; dont know how to get &#305;nstall?
4)when I open the synpticat manager, &#305;t wants to my password, altgouh my password is correcet, there occurs "wrong password",&#305; d&#305;d&#305;nt understand what is coming to my screen..

if you help me,&#305; w&#305;ll be glad..
see you and tkae care of you..bye..

---

### Post by zombrax on 2008-05-15
i'm an absolute idiot.. it was staring right in my face all this time... the network proxy is 192 and not 198 duh!! but i got new problems... what does this err mean guys? I get this when i try and run 
sudo apt-get update

zombrax@ub-lap:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_AU
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_AU
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg [189B]      
Get:2 [http://mirror.optus.net](http://mirror.optus.net) feisty Release.gpg [191B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_AU
Ign [http://mirror.optus.net](http://mirror.optus.net) feisty/main Translation-en_AU
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_AU
Get:3 [http://mirror.optus.net](http://mirror.optus.net) feisty-updates Release.gpg [191B]    
Ign [http://mirror.optus.net](http://mirror.optus.net) feisty-updates/main Translation-en_AU  
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release [5587B]                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release                               
Ign [http://mirror.optus.net](http://mirror.optus.net) feisty-updates/restricted Translation-en_AU        
Get:5 [http://mirror.optus.net](http://mirror.optus.net) feisty-security Release.gpg [191B]               
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages [6286B]               
Ign [http://mirror.optus.net](http://mirror.optus.net) feisty-security/main Translation-en_AU             
Ign [http://mirror.optus.net](http://mirror.optus.net) feisty-security/restricted Translation-en_AU       
Get:7 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages [3307B]           
Get:8 [http://mirror.optus.net](http://mirror.optus.net) feisty Release [57.2kB]                          
Get:9 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Sources [2150B]                
Get:10 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Sources [1592B]           
Get:11 [http://mirror.optus.net](http://mirror.optus.net) feisty-updates Release [50.9kB]                 
Get:12 [http://mirror.optus.net](http://mirror.optus.net) feisty-security Release [50.9kB]                
Get:13 [http://mirror.optus.net](http://mirror.optus.net) feisty/main Packages [1007kB]                   
Get:14 [http://mirror.optus.net](http://mirror.optus.net) feisty-updates/main Packages [200kB]            
Get:15 [http://mirror.optus.net](http://mirror.optus.net) feisty-updates/restricted Packages [6341B]                   
Get:16 [http://mirror.optus.net](http://mirror.optus.net) feisty-security/main Packages [127kB]                        
Get:17 [http://mirror.optus.net](http://mirror.optus.net) feisty-security/restricted Packages [6341B]                  
Fetched 1524kB in 4m31s (5613B/s)                                                           
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
zombrax@ub-lap:~$ sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vlc
zombrax@ub-lap:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_AU
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_AU
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg [189B]      
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_AU        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_AU    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_AU    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_AU  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release                   
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release                   
  
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release [5587B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_AU                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages                                      
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_AU                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Sources                                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_AU                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Sources                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_AU                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_AU                   
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_AU                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_AU                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_AU                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_AU                  
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release [57.2kB]                                     
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release [50.9kB]                             
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release [50.9kB]                            
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages [1007kB]                               
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages [3754kB]                          
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages [7628B]                         
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages [148kB]                         
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages [200kB]                       
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages [6341B]                 
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages [98.3kB]                  
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages [12.7kB]                
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages [127kB]                      
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages [6341B]                
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages [83.8kB]                 
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages [6099B]                
Fetched 5622kB in 10m4s (9306B/s)                                                           
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
zombrax@ub-lap:~$

---

### Post by zombrax on 2008-05-15
zombrax@ub-lap:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_AU
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_AU
Get:1 [http://packages.medibuntu.org]("http://packages.medibuntu.org/") feisty Release.gpg [189B]      
Get:2 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty Release.gpg [191B]
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty/main Translation-en_AU        
Ign [http://packages.medibuntu.org]("http://packages.medibuntu.org/") feisty/free Translation-en_AU    
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty/universe Translation-en_AU    
Ign [http://packages.medibuntu.org]("http://packages.medibuntu.org/") feisty/non-free Translation-en_AU
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty/restricted Translation-en_AU  
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") feisty Release                   
Err [http://packages.medibuntu.org]("http://packages.medibuntu.org/") feisty Release                   
  
Get:3 [http://packages.medibuntu.org]("http://packages.medibuntu.org/") feisty Release [5587B]
Ign [http://packages.medibuntu.org]("http://packages.medibuntu.org/") feisty Release
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty/multiverse Translation-en_AU                           
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") feisty/free Packages                                      
Get:4 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty-updates Release.gpg [191B]                           
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") feisty/non-free Packages                                  
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty-updates/main Translation-en_AU                         
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") feisty/free Sources                                       
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty-updates/restricted Translation-en_AU                   
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") feisty/non-free Sources                                   
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty-updates/universe Translation-en_AU                     
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty-updates/multiverse Translation-en_AU                   
Get:5 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty-security Release.gpg [191B]                          
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty-security/main Translation-en_AU                        
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty-security/restricted Translation-en_AU                  
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty-security/universe Translation-en_AU                    
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty-security/multiverse Translation-en_AU                  
Get:6 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty Release [57.2kB]                                     
Get:7 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty-updates Release [50.9kB]                             
Get:8 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty-security Release [50.9kB]                            
Get:9 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty/main Packages [1007kB]                               
Get:10 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty/universe Packages [3754kB]                          
Get:11 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty/restricted Packages [7628B]                         
Get:12 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty/multiverse Packages [148kB]                         
Get:13 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty-updates/main Packages [200kB]                       
Get:14 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty-updates/restricted Packages [6341B]                 
Get:15 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty-updates/universe Packages [98.3kB]                  
Get:16 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty-updates/multiverse Packages [12.7kB]                
Get:17 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty-security/main Packages [127kB]                      
Get:18 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty-security/restricted Packages [6341B]                
Get:19 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty-security/universe Packages [83.8kB]                 
Get:20 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") feisty-security/multiverse Packages [6099B]                
Fetched 5622kB in 10m4s (9306B/s)                                                           
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org]("http://packages.medibuntu.org/") feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
zombrax@ub-lap:~$

sorry only this part.. guys.. dont worry about the vlc part..

---

### Post by zombrax on 2008-05-15
also when trying to install vlc through Synpatic Manager; i get this error "Failed to download some of the files from the main server"

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/libd/libdvbpsi4/libdvbpsi4_0.1.5-2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libd/libdvbpsi4/libdvbpsi4_0.1.5-2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/libd/libdvdnav/libdvdnav4_0.1.10-0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libd/libdvdnav/libdvdnav4_0.1.10-0.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/f/faad2/libmp4v2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/faad2/libmp4v2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libg/libgsm/libgsm1_1.0.10-13_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libg/libgsm/libgsm1_1.0.10-13_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/libc/libcdio/libiso9660-4_0.76-1ubuntu2.7.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libc/libcdio/libiso9660-4_0.76-1ubuntu2.7.04.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/l/lame/liblame0_3.96.1-2ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/l/lame/liblame0_3.96.1-2ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libm/libmodplug/libmodplug0c2_0.7-5.2build1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libm/libmodplug/libmodplug0c2_0.7-5.2build1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libm/libmpcdec/libmpcdec3_1.2.2-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libm/libmpcdec/libmpcdec3_1.2.2-1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/sdl-image1.2/libsdl-image1.2_1.2.5-2ubuntu0.7.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/sdl-image1.2/libsdl-image1.2_1.2.5-2ubuntu0.7.04.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/libvlc0_0.8.6.release-0ubuntu4.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/libvlc0_0.8.6.release-0ubuntu4.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.6/libwxbase2.6-0_2.6.3.2.1.5ubuntu6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.6/libwxbase2.6-0_2.6.3.2.1.5ubuntu6_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.6/libwxgtk2.6-0_2.6.3.2.1.5ubuntu6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.6/libwxgtk2.6-0_2.6.3.2.1.5ubuntu6_i386.deb)
  407 Proxy Authentication Required

help please? :)

---

### Post by zombrax on 2008-05-18
> **zombrax said:**
> --16:21:01--  [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
  (try: 5) => `/etc/apt/sources.list.d/medibuntu.list'
Connecting to 198.168.1.1:3128... failed: Connection timed out.
Retrying.

after nearly 5 weeks of absolute frustration; figured it out myself! could one have an IP addy of 198......??? that was the problem; the proxy is 192.168.......

the funny thing is that i looked at it a zillion times and didnt even think twice and yes i did check the IP address a million times too and still it didnt register. stupid users; hehe.. anyways thanks for trying to help me..... :)

---

