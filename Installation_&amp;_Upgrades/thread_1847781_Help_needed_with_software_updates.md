---
title: "Help needed with software updates"
date: 2011-09-21
forum: Installation &amp; Upgrades
---

### Post by tomdkat on 2011-09-21
I'm having problems running updates of the latest kernel release and some other software.

When I run the update using the update manager, it reports a "package operation failed" message with these details:

> 
installArchives() failed: dpkg: warning: parsing file '/var/lib/dpkg/status' near line 55389 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_jaunty': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 55390 package 'virtualbox-3.0':
 error in Config-Version string '3.0.12-54655_Ubuntu_jaunty': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 58140 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_jaunty': invalid character in revision number
dpkg: unrecoverable fatal error, aborting:
 syntax error: unknown group 'cdemu' in statoverride file
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 55389 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_jaunty': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 55390 package 'virtualbox-3.0':
 error in Config-Version string '3.0.12-54655_Ubuntu_jaunty': invalid character in revision number

So, how can I correct these issues?

Thanks!

EDIT:  I'm running Ubuntu 11.04.

Peace...

---

### Post by sanderd17 on 2011-09-21
Are you running jaunty? Because if you do, it isn't supported anymore.

If you are not, can you give the output of
```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by tomdkat on 2011-09-21
> **sanderd17 said:**
> Are you running jaunty? Because if you do, it isn't supported anymore.

If you are not, can you give the output of
```

sudo apt-get update
sudo apt-get upgrade

```
Thanks for the reply and sorry for not including the version of Ubuntu I'm running. I'm a bit foggy this morning.  :)

I'm running 11.04 64-bit.

Here is the requested output:

```

tom@deathstar:~$ sudo apt-get update
[sudo] password for tom: 
Ign http://dl.google.com stable InRelease
Ign http://ppa.launchpad.net natty InRelease                                                                    
Ign http://ppa.launchpad.net natty InRelease                                                                    
Ign http://ppa.launchpad.net natty InRelease                                                                                           
Get:1 http://dl.google.com stable Release.gpg [198 B]                                                                                  
Ign http://security.ubuntu.com natty-security InRelease                                                                                
Ign http://extras.ubuntu.com natty InRelease                                                                     
Ign http://us.archive.ubuntu.com natty InRelease                                                                 
Ign http://us.archive.ubuntu.com natty-updates InRelease                                                         
Ign http://deb.opera.com stable InRelease                                                                        
Get:2 http://dl.google.com stable Release [1,347 B]                                                              
Hit http://ppa.launchpad.net natty Release.gpg                                                                                            
Hit http://security.ubuntu.com natty-security Release.gpg                                                                              
Get:3 http://extras.ubuntu.com natty Release.gpg [72 B]                                                                                
Hit http://us.archive.ubuntu.com natty Release.gpg                                                               
Hit http://deb.opera.com stable Release.gpg                                                                      
Get:4 http://dl.google.com stable/main amd64 Packages [1,178 B]                                                  
Hit http://security.ubuntu.com natty-security Release                                                                                        
Hit http://ppa.launchpad.net natty Release.gpg                                                                   
Hit http://extras.ubuntu.com natty Release                                                                                                           
Hit http://us.archive.ubuntu.com natty-updates Release.gpg                                                                                           
Hit http://deb.opera.com stable Release                                                                                                  
Hit http://ppa.launchpad.net natty Release.gpg                                                                                        
Hit http://us.archive.ubuntu.com natty Release                                                                                        
Hit http://security.ubuntu.com natty-security/main Sources                                                                                           
Hit http://extras.ubuntu.com natty/main amd64 Packages                                                                                               
Hit http://ppa.launchpad.net natty Release                                                                                             
Ign http://dl.google.com stable/main TranslationIndex                                                                                                
Hit http://us.archive.ubuntu.com natty-updates Release                                                                                               
Hit http://deb.opera.com stable/non-free amd64 Packages                                                                                              
Hit http://security.ubuntu.com natty-security/restricted Sources                                                                       
Hit http://security.ubuntu.com natty-security/universe Sources                                                   
Hit http://security.ubuntu.com natty-security/multiverse Sources                                                                       
Hit http://security.ubuntu.com natty-security/main amd64 Packages                                                                      
Hit http://security.ubuntu.com natty-security/restricted amd64 Packages                                                                
Ign http://extras.ubuntu.com natty/main TranslationIndex                                                                               
Hit http://ppa.launchpad.net natty Release                                                                                             
Hit http://us.archive.ubuntu.com natty/main Sources                                                                                                  
Hit http://us.archive.ubuntu.com natty/restricted Sources                                                                              
Hit http://us.archive.ubuntu.com natty/universe Sources                                                                                
Hit http://us.archive.ubuntu.com natty/multiverse Sources                                                                              
Hit http://us.archive.ubuntu.com natty/main amd64 Packages                                                                             
Hit http://security.ubuntu.com natty-security/universe amd64 Packages                                                                  
Hit http://security.ubuntu.com natty-security/multiverse amd64 Packages                                                                
Ign http://security.ubuntu.com natty-security/main TranslationIndex                                                                    
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex                                                              
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex                                                              
Ign http://security.ubuntu.com natty-security/universe TranslationIndex                                                                
Ign http://deb.opera.com stable/non-free TranslationIndex                                                                              
Hit http://ppa.launchpad.net natty Release                                                                       
Hit http://us.archive.ubuntu.com natty/restricted amd64 Packages                                                                                     
Hit http://us.archive.ubuntu.com natty/universe amd64 Packages                                                                         
Hit http://us.archive.ubuntu.com natty/multiverse amd64 Packages                                                                       
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                                                                           
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex                                                                     
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex                                                                     
Hit http://ppa.launchpad.net natty/main Sources                                                                                        
Hit http://ppa.launchpad.net natty/main amd64 Packages                                                                                 
Ign http://ppa.launchpad.net natty/main TranslationIndex                                                                               
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex                                                                       
Hit http://us.archive.ubuntu.com natty-updates/main Sources                                                                            
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources                                                                      
Hit http://us.archive.ubuntu.com natty-updates/universe Sources                                                                        
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources                                                                      
Hit http://us.archive.ubuntu.com natty-updates/main amd64 Packages                                                                     
Hit http://us.archive.ubuntu.com natty-updates/restricted amd64 Packages                                                               
Hit http://us.archive.ubuntu.com natty-updates/universe amd64 Packages                                                                 
Hit http://ppa.launchpad.net natty/main Sources                                                                                        
Hit http://ppa.launchpad.net natty/main amd64 Packages                                                                                 
Ign http://ppa.launchpad.net natty/main TranslationIndex                                                                               
Hit http://us.archive.ubuntu.com natty-updates/multiverse amd64 Packages                                                               
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex                                                                   
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex                                                             
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex                                                             
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex                                                               
Hit http://ppa.launchpad.net natty/main amd64 Packages                                                                                 
Ign http://ppa.launchpad.net natty/main TranslationIndex                                                                               
Ign http://extras.ubuntu.com natty/main Translation-en_US                                                                              
Ign http://extras.ubuntu.com natty/main Translation-en                                                                                 
Ign http://security.ubuntu.com natty-security/main Translation-en_US                                             
Ign http://security.ubuntu.com natty-security/main Translation-en                                                
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US                                       
Ign http://security.ubuntu.com natty-security/multiverse Translation-en                                          
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US                 
Ign http://deb.opera.com stable/non-free Translation-en_US                                 
Ign http://us.archive.ubuntu.com natty/main Translation-en_US                              
Ign http://us.archive.ubuntu.com natty/main Translation-en                                                       
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US                                              
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en                                                 
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US                                              
Ign http://us.archive.ubuntu.com natty/restricted Translation-en                                                 
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US                                                
Ign http://security.ubuntu.com natty-security/restricted Translation-en                                                                          
Ign http://security.ubuntu.com natty-security/universe Translation-en_US                                                                         
Ign http://security.ubuntu.com natty-security/universe Translation-en                                                                            
Ign http://deb.opera.com stable/non-free Translation-en                                                                                          
Ign http://us.archive.ubuntu.com natty/universe Translation-en                                                             
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US                                
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en                                   
Ign http://dl.google.com stable/main Translation-en_US               
Ign http://dl.google.com stable/main Translation-en                  
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Fetched 2,795 B in 3s (702 B/s)
Reading package lists... Done
tom@deathstar:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apport apport-gtk google-chrome-stable linux-headers-2.6.38-11 linux-headers-2.6.38-11-generic linux-image-2.6.38-11-generic linux-libc-dev
  python-apport python-problem-report
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/73.6 MB of archives.
After this operation, 20.5 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 55389 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_jaunty': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 55390 package 'virtualbox-3.0':
 error in Config-Version string '3.0.12-54655_Ubuntu_jaunty': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 58140 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_jaunty': invalid character in revision number
dpkg: unrecoverable fatal error, aborting:
 syntax error: unknown group 'cdemu' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)
tom@deathstar:~$ 

```
Thanks!

Peace...

---

### Post by mörgæs on 2011-09-21
The computer has been upgraded at least four times. You should consider a fresh install of 11.04.

This will also give you the option of choosing ext4 and Grub2.

---

### Post by sanderd17 on 2011-09-21
The package list looks good, so it is indeed a pure dpkg error.

It's complaining about a missing group. Can you add the group with the command

```

sudo addgroup cdemu

```

Just trying. If my trying takes too long, you should follow mörgæs advise.

---

### Post by tomdkat on 2011-09-21
> **sanderd17 said:**
> The package list looks good, so it is indeed a pure dpkg error.

It's complaining about a missing group. Can you add the group with the command

```

sudo addgroup cdemu

```

Just trying. If my trying takes too long, you should follow mörgæs advise.
That seems to have done the trick!  Thanks!

Peace...

---

### Post by mörgæs on 2011-09-21
Good, please mark the thread 'solved'.

---

### Post by tomdkat on 2011-09-23
> **mörgæs said:**
> Good, please mark the thread 'solved'.Yep, I realized I had forgotten to do that and just did. :)

I did have one last question.  With regard to the other warnings I'm getting above, is there no way of cleaning up that outdated and/or erroneous version information from the dpkg files or is simply doing a fresh install the path of least resistance? :)

Thanks!

Peace...

---

### Post by sanderd17 on 2011-09-23
I don't know what caused it. Your sources seem ok. So it has to be a problem with dpkg itself.

Try reading the manual to see if you can fix this any way.

```

man dpkg

```

---

### Post by tomdkat on 2011-09-23
Cool  Thanks for everyone's help! :)

EDIT:  I ended up finding this question on Launchpad:

[https://answers.launchpad.net/ubuntu/+source/dpkg/+question/123165](https://answers.launchpad.net/ubuntu/+source/dpkg/+question/123165)

and I manually removed the references to the "virtualbox-3.0" package and the warnings have gone away.

Peace...

---

