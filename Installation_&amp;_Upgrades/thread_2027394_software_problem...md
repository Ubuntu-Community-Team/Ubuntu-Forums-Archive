---
title: "software problem.."
date: 2012-07-16
forum: Installation &amp; Upgrades
---

### Post by sbshaikh on 2012-07-16
Previously I have 10.04 ubuntu operating system on my laptop, then some of our office software provided to us installed by me and those were properly working..Thereafter I upgraded the operating systme with Ubuntu 12.04, and now those  our office software are not properly working.. which showing following problem:-
a) [FONT="Arial Black"][SIZE="4"]_[COLOR="Red"]java.sql.SQLException:Acess denied for user 'root'@'localhost' (using password:NO)....[/COLOR]_[/SIZE][/FONT] OK
Then I pressed 'ok' button then shown line as follows:-
b) [FONT="Arial Black"][COLOR="black"][COLOR="Red"]_ java.lang.NullPointerException....._[/COLOR][/COLOR][/FONT] OK

Thereupon pressing 'ok' button software opened but it appears blank..
[FONT="Impact"][SIZE="3"]_[COLOR="Sienna"] Please help me to solve this problem.. I will grateful to you..[/COLOR]_[/SIZE][/FONT]

---

### Post by dino99 on 2012-07-16
which java is used ? (genuine ubuntu ? oracle?)

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

    IMPORTANT choose the java you installed as default 

 $ sudo update-alternatives --config java

---

### Post by sbshaikh on 2012-07-18
[B]Sir, I have follow the commands supplied in link fo installing java7, then my terminal windows shown following problem.. so please guide me..
[U][I]my terminal window shown output as follows..
[/B][/I][/U]

ubuntu@ubuntu-linux:~/Desktop$ sudo add-apt-repository ppa:eugenesan/java
[sudo] password for ubuntu: 
You are about to add the following PPA to your system:
 
 More info: [https://launchpad.net/~eugenesan/+archive/java](https://launchpad.net/~eugenesan/+archive/java)
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.L4eM4C4X2p --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 4346FBB158F4022C896164EEE61380B28313A596
gpg: requesting key 8313A596 from hkp server keyserver.ubuntu.com
gpg: key 8313A596: "Launchpad synergy+" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
ubuntu@ubuntu-linux:~/Desktop$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates InRelease                        
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://archive.canonical.com](http://archive.canonical.com) [distro] InRelease                            
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg [198 B]                    
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg [198 B]            
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release [49.6 kB]                      
Ign [http://archive.canonical.com](http://archive.canonical.com) [distro] Release.gpg                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [20.8 kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release [49.6 kB]              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Ign [http://archive.canonical.com](http://archive.canonical.com) [distro] Release                              
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [78.6 kB] 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Ign [http://archive.canonical.com](http://archive.canonical.com) [distro]/partner TranslationIndex             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages [1,274 kB]         
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]                      
Err [http://archive.canonical.com](http://archive.canonical.com) [distro]/partner Sources                      
  404  Not Found [IP: 91.189.92.191 80]
Err [http://archive.canonical.com](http://archive.canonical.com) [distro]/partner i386 Packages                
  404  Not Found [IP: 91.189.92.191 80]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://archive.canonical.com](http://archive.canonical.com) [distro]/partner Translation-en_US            
Ign [http://archive.canonical.com](http://archive.canonical.com) [distro]/partner Translation-en               
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [73 B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [40.2 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [8,218 B]                 
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [5,136 B]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [14.2 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Get:18 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                         
Get:19 [http://dl.google.com](http://dl.google.com) stable Release                                     
Get:20 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [768 B]                  
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex                
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages [94.6 kB]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages [328 kB]   
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages [328 kB]   
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en         
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en [153 kB]  
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en [56.6 kB]
Fetched 7,033 kB in 4min 17s (27.3 kB/s)                                       
W: Failed to fetch [http://archive.canonical.com/dists/](http://archive.canonical.com/dists/)[distro]/partner/source/Sources  404  Not Found [IP: 91.189.92.191 80]

W: Failed to fetch [http://archive.canonical.com/dists/](http://archive.canonical.com/dists/)[distro]/partner/binary-i386/Packages  404  Not Found [IP: 91.189.92.191 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
ubuntu@ubuntu-linux:~/Desktop$ 
ubuntu@ubuntu-linux:~/Desktop$ sudo apt-get install oracle-java7-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
oracle-java7-installer is already the newest version.
The following package was automatically installed and is no longer required:
  icedtea-netx-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 380 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-07-18 20:09:53--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving download.oracle.com (download.oracle.com)... 115.112.0.37, 115.112.0.14
Connecting to download.oracle.com (download.oracle.com)|115.112.0.37|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz) [following]
--2012-07-18 20:09:54--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving edelivery.oracle.com (edelivery.oracle.com)... 23.57.126.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|23.57.126.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following]
--2012-07-18 20:09:55--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html)
Connecting to download.oracle.com (download.oracle.com)|115.112.0.37|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-i586.tar.gz'

     0K .....                                                 100% 1.79M=0.003s

2012-07-18 20:09:55 (1.79 MB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dino99 on 2012-07-18
remove that "eugenesan" ppa and use that one instaed:

[https://launchpad.net/~webupd8team/+archive/java](https://launchpad.net/~webupd8team/+archive/java)

---

### Post by sbshaikh on 2012-09-05
> **dino99 said:**
> remove that "eugenesan" ppa and use that one instaed:

[https://launchpad.net/~webupd8team/+archive/java](https://launchpad.net/~webupd8team/+archive/java)




Thank you, Sir.. As per your directions used the site..[https://launchpad.net/~webupd8team/+archive/java](https://launchpad.net/~webupd8team/+archive/java)[/QUOTE]   
and succeed to install Java7 in my laptop.. After follwing commands for installing java lastly terminal window of my laptop shown message as " oracl 7 JRE plugins installed".

Sir.. eventhough the softwares are yet to be worked?
Ok.. Thank you once again..

---

