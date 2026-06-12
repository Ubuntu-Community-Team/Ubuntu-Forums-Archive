---
title: "Java(JDK &amp; JRE) installation and Netbeans in x64"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by amitahire on 2010-02-18
Hey guys

I am fairly new to linux, well i need to install java(jdk & jre) in my system. but i have been able to install openjdk( netbeans doesnt detect it :( )

I all tried all the possible methods ( diff packet manager, downloading the jdk jre files myself - but still not able to do it - it gives some error) can anyone plz HELP?

```
amit@Amit-desktop:~$ sudo apt-get install -f sun-java6-demo sun-java6-source
Reading package lists... Done                                               
Building dependency tree                                                    
Reading state information... Done                                           
sun-java6-demo is already the newest version.                               
sun-java6-source is already the newest version.                             
You might want to run `apt-get -f install' to correct these:                
The following packages have unmet dependencies:                             
  sun-java6-demo: Depends: sun-java6-jre (= 6-15-1) but it is not going to be installed
                  Depends: sun-java6-jdk (= 6-15-1) but it is not going to be installed
  sun-java6-source: Depends: sun-java6-jdk (>= 6-15-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution). 
amit@Amit-desktop:~$ sudo apt-get install -f sun-java6-jre sun-java6-jdk
Reading package lists... Done                                           
Building dependency tree                                                
Reading state information... Done                                       
You might want to run `apt-get -f install' to correct these:            
The following packages have unmet dependencies:                         
  sun-java6-jdk: Depends: sun-java6-bin (= 6-15-1) but it is not going to be installed
  sun-java6-jre: Depends: sun-java6-bin (= 6-15-1) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-15-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).  
amit@Amit-desktop:~$ sudo apt-get install -f sun-java6-bin sun-java6-jre sun-java6-jdk       
Reading package lists... Done                                                                
Building dependency tree                                                                     
Reading state information... Done                                                            
The following packages were automatically installed and are no longer required:              
  realpath libecj-java-gcj linux-headers-2.6.31-14 libgcj10-awt javahelper                   
  linux-headers-2.6.31-14-generic python-scriptutil                                          
Use 'apt-get autoremove' to remove them.                                                     
Suggested packages:                                                                          
  sun-java6-plugin ia32-sun-java6-plugin sun-java6-fonts ttf-kochi-gothic                    
  ttf-sazanami-gothic ttf-kochi-mincho ttf-sazanami-mincho ttf-arphic-uming                  
The following NEW packages will be installed:                                                
  sun-java6-bin sun-java6-jdk sun-java6-jre                                                  
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.                               
2 not fully installed or removed.                                                            
Need to get 0B/52.5MB of archives.                                                           
After this operation, 155MB of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 321987 files and directories currently installed.)
Unpacking sun-java6-bin (from .../sun-java6-bin_6-15-1_amd64.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-bin_6-15-1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Unpacking sun-java6-jre (from .../sun-java6-jre_6-15-1_all.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-jre_6-15-1_all.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Unpacking sun-java6-jdk (from .../sun-java6-jdk_6-15-1_amd64.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-jdk_6-15-1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java6-bin_6-15-1_amd64.deb
 /var/cache/apt/archives/sun-java6-jre_6-15-1_all.deb
 /var/cache/apt/archives/sun-java6-jdk_6-15-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
amit@Amit-desktop:~$

```

Can anyone tell me what the problem and the possible solution?

---

### Post by darkod on 2010-02-18
Is thee any reason you don't wan to use sun-java6-jdk? I know for sure Netbeans detects it without any problem. Just install it from Synaptic before starting the Netbeans install.

---

### Post by amitahire on 2010-02-18
> **darkod said:**
> Is thee any reason you don't wan to use sun-java6-jdk? I know for sure Netbeans detects it without any problem. Just install it from Synaptic before starting the Netbeans install.

i did -- it gives me this error(s)

```
E: /var/cache/apt/archives/sun-java6-bin_6-15-1_amd64.deb: subprocess new pre-installation script returned error exit status 1
E: /var/cache/apt/archives/sun-java6-jre_6-15-1_all.deb: subprocess new pre-installation script returned error exit status 1
E: /var/cache/apt/archives/sun-java6-jdk_6-15-1_amd64.deb: subprocess new pre-installation script returned error exit status 1

```

---

### Post by amitahire on 2010-02-18
and for the record i also did these..but to no avail

```

sudo rm /var/lib/dpkg/lock


sudo dpkg --configure -a

```

---

### Post by amitahire on 2010-02-19
bounce....anyone?

---

