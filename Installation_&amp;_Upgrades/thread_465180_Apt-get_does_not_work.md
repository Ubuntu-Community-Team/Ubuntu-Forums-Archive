---
title: "Apt-get does not work"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by moustady on 2007-06-05
Hi,
the sudo apt-get update
and sudo apt-get upgrade

Do not work in my work place(Do not know the type of connection there?)
but thy do work in my home (using DSL connection)

is there a way to make it work in my work place?
if you need any information about the network I will gladly ask the IT department :)

---

### Post by taurus on 2007-06-05
Can you post the complete message when you run those two commands from a terminal?  Maybe there is a problem with proxy/firewall at your work place.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by GRETANIKOS on 2007-06-05
Hi all,

What is the latest updates since 2 days I have no update notification.
Is there anything wrong ?
sudo apt-get apdate returns me many messages but not un update.
Thank you

---

### Post by moustady on 2007-06-06
here is what come in the terminal

Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release.gpg
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US           
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US   
Err [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages             
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security Release.gpg 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/restricted Translation-en_US
Ign cdrom://Ubuntu Studio 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US        
Ign cdrom://Ubuntu Studio 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security Release     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Sources                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/main Packages                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/restricted Packages           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Sources                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/main Sources                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/multiverse Sources            
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources                 
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/universe Sources              
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages               
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/multiverse Packages           
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                     
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                          
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages               
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages       
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources        
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                           
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages                 
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources                     
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources                
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources          
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages                      
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources                      
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages       
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Sources   
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages         
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages                  
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Sources                  
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages            
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/multiverse Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

But the firefox is working with the same sitting of proxy, port,username, domain and password.

Dose it have to do with ISA server?

---

### Post by awaldram on 2007-06-06
Your behind a proxy that requires you to authenticate 

See your site administrator.

---

### Post by moustady on 2007-06-06
Hi,
I am the Network Admin, We have configured the proxy settings and the authentication user name and password. everything seems fine apart from the Update Service.

We even configured the network proxy... no luck.

can you help us setting the software update server with in the Lan. so we should not have the issues with the proxy. 

Thanks

---

### Post by jorno on 2007-09-10
I don't know if anyone still has this problem, but I found my solution in another post.

The steps mentioned here earlier are good and all, BUT if those of  you who's got this problem is in a Windows environment with a Microsoft ISA Proxy that need authentication, this is the solution that worked for me:

You need to install NTLMAPS.

[http://packages.ubuntu.com/feisty/web/ntlmaps](http://packages.ubuntu.com/feisty/web/ntlmaps)
* Go there, and download, either from within Firefox (if you manage to get Proxy working with Firefox - I did, but not apt-get or Synaptics or anything else).
* Download the package for ntlmaps (this is for Ubuntu Feisty)
* Start a terminal, find your downloaded package, and type:
*sudo dpkg -i ntlmaps_0.9.9.0.1-6_all.deb*
This should guide you trough the installation of the package...

BUT, my problems didn't stop there!
After, I had to edit /etc/ntlmaps/server.cfg manually.
( *sudo vim /etc /ntlmaps/server.cfg* )
Then I saw that the config-file was formatted with DOS (not UNIX), so I had to tell vim to convert it to UNIX-format. Do this in vim:
*:set fileformat=unix*
*:wq*
This should convert the file, and save it.
I also had to change some of the options:
Under the [CLIENT_HEADER] section, I had to comment out the first Accept and User-Agent part (Windows 98), and then uncomment the next part (Windows 2000 emulation).
Then I filled in "NT_HOSTNAME" (remembered what PC number this workstation had in Windows), and "NT_DOMAIN").

After those changes, restart ntlmaps:
*/etc/init.d/ntlmaps restart*

And point all your proxy-settings to: [http://127.0.0.1:5865](http://127.0.0.1:5865)

Make a file: */etc/apt/apt.conf*
Acquire::http::Proxy "http://127.0.0.1:5865";

And then try "*apt-get update*".

You could also insert this into:
System -> Preferences -> Network Proxy

And in Synaptics:
System -> Administration -> Synaptics -> Settings -> Preferences -> Network:
Manual proxy configuration:

127.0.0.1 port 5865 (no authentication)


This should do the trick! It did for me.. Please ask if there is something not clear yet, or if I should correct any of this. (Sorry, English is not my native tongue).

---

