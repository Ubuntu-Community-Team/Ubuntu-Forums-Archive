---
title: "Held broken packages/unmet dependencies for git and git-man"
date: 2013-07-03
forum: Installation &amp; Upgrades
---

### Post by poxyhead on 2013-07-03
A partial upgrade uninstalled git on my laptop, and upon attempts to reinstall it I have the following output:

```

$ sudo apt-get install git                     
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 git : Depends: git-man (< 1:1.8.1.2-.) but 1:1.8.3.2-0ubuntu1~raring1 is to be installed
E: Unable to correct problems, you have held broken packages.

```

I've been following [this thread]("http://ubuntuforums.org/showthread.php?t=947124") to try and fix things, but nothing's worked so far. Could anyone please help?

---

### Post by Frogs Hair on 2013-07-03
Hello and Welcome 

I just successfully installed the git  package on 13.04 . Post the output of the following,  ```
sudo apt-get update
``` There may be command recommendations in the output.

---

### Post by poxyhead on 2013-07-03
Thanks for the quick reply!

Here is the output of apt-get update:

```

$ sudo apt-get update
Get:1 http://au.archive.ubuntu.com raring Release.gpg [933 B]
Get:2 http://dl.google.com stable Release.gpg [198 B]                               
Get:3 http://au.archive.ubuntu.com raring-updates Release.gpg [933 B]               
Get:4 http://au.archive.ubuntu.com raring-backports Release.gpg [933 B]             
Hit http://au.archive.ubuntu.com raring Release                                     
Hit http://dl.google.com stable Release                                             
Hit http://au.archive.ubuntu.com raring-updates Release                             
Hit http://au.archive.ubuntu.com raring-backports Release                           
Get:5 http://security.ubuntu.com raring-security Release.gpg [933 B]                
Hit http://dl.google.com stable/main amd64 Packages                                 
Hit http://au.archive.ubuntu.com raring/main Sources                                
Get:6 http://archive.canonical.com quantal Release.gpg [933 B]                      
Get:7 http://extras.ubuntu.com raring Release.gpg [72 B]                            
Hit http://ppa.launchpad.net raring Release.gpg                                     
Hit http://au.archive.ubuntu.com raring/restricted Sources                          
Hit http://dl.google.com stable/main i386 Packages                                  
Get:8 http://security.ubuntu.com raring-security Release [40.8 kB]                  
Hit http://au.archive.ubuntu.com raring/universe Sources                            
Hit http://archive.canonical.com quantal Release                                    
Hit http://extras.ubuntu.com raring Release                                         
Hit http://ppa.launchpad.net raring Release.gpg                                     
Hit http://au.archive.ubuntu.com raring/multiverse Sources                          
Hit http://archive.canonical.com quantal/partner Sources                            
Hit http://extras.ubuntu.com raring/main Sources                                    
Hit http://ppa.launchpad.net raring Release.gpg                                     
Hit http://au.archive.ubuntu.com raring/main amd64 Packages                         
Hit http://archive.canonical.com quantal/partner amd64 Packages                     
Hit http://au.archive.ubuntu.com raring/restricted amd64 Packages                   
Hit http://extras.ubuntu.com raring/main amd64 Packages                             
Hit http://ppa.launchpad.net raring Release                                         
Hit http://security.ubuntu.com raring-security/main Sources                         
Hit http://au.archive.ubuntu.com raring/universe amd64 Packages                     
Hit http://archive.canonical.com quantal/partner i386 Packages                      
Hit http://extras.ubuntu.com raring/main i386 Packages                              
Hit http://au.archive.ubuntu.com raring/multiverse amd64 Packages                   
Hit http://ppa.launchpad.net raring Release                                         
Hit http://au.archive.ubuntu.com raring/main i386 Packages                          
Hit http://security.ubuntu.com raring-security/restricted Sources                   
Hit http://au.archive.ubuntu.com raring/restricted i386 Packages                    
Hit http://ppa.launchpad.net raring Release                                         
Hit http://au.archive.ubuntu.com raring/universe i386 Packages                      
Hit http://security.ubuntu.com raring-security/universe Sources                     
Hit http://au.archive.ubuntu.com raring/multiverse i386 Packages                    
Hit http://au.archive.ubuntu.com raring/main Translation-en_AU                      
Hit http://security.ubuntu.com raring-security/multiverse Sources                   
Hit http://ppa.launchpad.net raring/main amd64 Packages                             
Hit http://au.archive.ubuntu.com raring/main Translation-en                         
Hit http://au.archive.ubuntu.com raring/multiverse Translation-en_AU                
Ign http://dl.google.com stable/main Translation-en_AU                              
Hit http://au.archive.ubuntu.com raring/multiverse Translation-en                   
Hit http://au.archive.ubuntu.com raring/restricted Translation-en_AU                
Hit http://au.archive.ubuntu.com raring/restricted Translation-en                   
Hit http://security.ubuntu.com raring-security/main amd64 Packages                  
Ign http://dl.google.com stable/main Translation-en                                 
Hit http://ppa.launchpad.net raring/main i386 Packages                              
Hit http://au.archive.ubuntu.com raring/universe Translation-en                     
Hit http://au.archive.ubuntu.com raring-updates/main Sources                        
Hit http://au.archive.ubuntu.com raring-updates/restricted Sources                  
Hit http://au.archive.ubuntu.com raring-updates/universe Sources                    
Hit http://au.archive.ubuntu.com raring-updates/multiverse Sources                  
Hit http://security.ubuntu.com raring-security/restricted amd64 Packages            
Hit http://au.archive.ubuntu.com raring-updates/main amd64 Packages                 
Hit http://au.archive.ubuntu.com raring-updates/restricted amd64 Packages           
Hit http://au.archive.ubuntu.com raring-updates/universe amd64 Packages             
Hit http://au.archive.ubuntu.com raring-updates/multiverse amd64 Packages           
Hit http://au.archive.ubuntu.com raring-updates/main i386 Packages                  
Hit http://security.ubuntu.com raring-security/universe amd64 Packages              
Hit http://au.archive.ubuntu.com raring-updates/restricted i386 Packages            
Hit http://security.ubuntu.com raring-security/multiverse amd64 Packages            
Hit http://ppa.launchpad.net raring/main Sources                                    
Hit http://security.ubuntu.com raring-security/main i386 Packages                   
Hit http://security.ubuntu.com raring-security/restricted i386 Packages             
Hit http://ppa.launchpad.net raring/main amd64 Packages                             
Hit http://security.ubuntu.com raring-security/universe i386 Packages               
Hit http://ppa.launchpad.net raring/main i386 Packages                              
Ign http://archive.canonical.com quantal/partner Translation-en_AU                  
Hit http://security.ubuntu.com raring-security/multiverse i386 Packages             
Ign http://extras.ubuntu.com raring/main Translation-en_AU                          
Ign http://archive.canonical.com quantal/partner Translation-en                     
Ign http://extras.ubuntu.com raring/main Translation-en                             
Hit http://security.ubuntu.com raring-security/main Translation-en                  
Hit http://ppa.launchpad.net raring/main Sources                                    
Hit http://au.archive.ubuntu.com raring-updates/universe i386 Packages              
Hit http://au.archive.ubuntu.com raring-updates/multiverse i386 Packages            
Hit http://security.ubuntu.com raring-security/multiverse Translation-en            
Hit http://ppa.launchpad.net raring/main amd64 Packages                             
Hit http://au.archive.ubuntu.com raring-updates/main Translation-en                 
Hit http://au.archive.ubuntu.com raring-updates/multiverse Translation-en           
Hit http://au.archive.ubuntu.com raring-updates/restricted Translation-en           
Hit http://ppa.launchpad.net raring/main i386 Packages                              
Hit http://au.archive.ubuntu.com raring-updates/universe Translation-en             
Hit http://au.archive.ubuntu.com raring-backports/main Sources                      
Hit http://au.archive.ubuntu.com raring-backports/restricted Sources                
Hit http://security.ubuntu.com raring-security/restricted Translation-en            
Hit http://au.archive.ubuntu.com raring-backports/universe Sources                  
Hit http://au.archive.ubuntu.com raring-backports/multiverse Sources                
Hit http://au.archive.ubuntu.com raring-backports/main amd64 Packages               
Hit http://au.archive.ubuntu.com raring-backports/restricted amd64 Packages         
Hit http://au.archive.ubuntu.com raring-backports/universe amd64 Packages           
Hit http://au.archive.ubuntu.com raring-backports/multiverse amd64 Packages         
Hit http://au.archive.ubuntu.com raring-backports/main i386 Packages                
Hit http://au.archive.ubuntu.com raring-backports/restricted i386 Packages          
Hit http://au.archive.ubuntu.com raring-backports/universe i386 Packages            
Hit http://security.ubuntu.com raring-security/universe Translation-en              
Hit http://au.archive.ubuntu.com raring-backports/multiverse i386 Packages          
Hit http://au.archive.ubuntu.com raring-backports/main Translation-en               
Hit http://au.archive.ubuntu.com raring-backports/multiverse Translation-en         
Hit http://au.archive.ubuntu.com raring-backports/restricted Translation-en         
Hit http://au.archive.ubuntu.com raring-backports/universe Translation-en           
Ign http://au.archive.ubuntu.com raring/universe Translation-en_AU                  
Ign http://au.archive.ubuntu.com raring-updates/main Translation-en_AU
Ign http://au.archive.ubuntu.com raring-updates/multiverse Translation-en_AU
Ign http://au.archive.ubuntu.com raring-updates/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com raring-updates/universe Translation-en_AU
Ign http://au.archive.ubuntu.com raring-backports/main Translation-en_AU
Ign http://au.archive.ubuntu.com raring-backports/multiverse Translation-en_AU
Ign http://au.archive.ubuntu.com raring-backports/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com raring-backports/universe Translation-en_AU
Ign http://security.ubuntu.com raring-security/main Translation-en_AU
Ign http://security.ubuntu.com raring-security/multiverse Translation-en_AU
Ign http://security.ubuntu.com raring-security/restricted Translation-en_AU
Ign http://security.ubuntu.com raring-security/universe Translation-en_AU
Ign http://ppa.launchpad.net raring/main Translation-en_AU
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://ppa.launchpad.net raring/main Translation-en_AU
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://ppa.launchpad.net raring/main Translation-en_AU
Ign http://ppa.launchpad.net raring/main Translation-en
Fetched 45.7 kB in 19s (2,308 B/s)
Reading package lists... Done

```

---

### Post by Frogs Hair on 2013-07-03
Try the installation again because I see nothing in the output to suggest broken packages.

---

### Post by poxyhead on 2013-07-03
I tried it again and I get the same error. :(

---

### Post by Frogs Hair on 2013-07-03
```
sudo apt-get remove --purge git
``` If this fails you may get a command recommendation in the terminal. If the command works try the following ```
sudo apt-get autoremove
``````
sudo apt-get update && sudo apt-get upgrade
``` ```
sudo apt-get install git 
``` You may have a conflicting package from another program.

---

### Post by poxyhead on 2013-07-03
No luck. The purge removed another package git*, but after the update/upgrade (which installed an upgrade to firefox) and install, it gave the same error.

If it is a conflicting package, is there an easy way to identify the packages in question?

---

### Post by steeldriver on 2013-07-03
You seem to have a mix of repos (raring / raring-backports / quantal) - is that normal? just asking, I'm still on 12.04 so I don't know - if not I wonder if that's the issue?

---

### Post by Frogs Hair on 2013-07-03
The synaptic package manager if installed lists conflicts in properties . ```
sudo apt-get install synaptic
``` I don't know why I can install the package and you can't other than a conflict. steeldriver is correct and the Quantal partner shouldn't be there . Was this an upgrade ?

---

### Post by poxyhead on 2013-07-03
@steeldriver: I have no idea, although it's interesting that I still have quantal in there. I tried commenting out the quantal repos in the /etc/apt/sources.list file to see if that might be the problem and running update/upgrade, but it doesn't seem to change anything.

@Frogs Hair: I haven't really used synaptic before, so I'm not really sure how to interpret the information in properties. Here is a screenshot (I included only the end because it was pretty long). Any ideas?

[ATTACH=CONFIG]244368[/ATTACH]

And no, I upgraded to raring a while ago and don't remember if I had any problems (except for when I got gnome 3.8 a little afterwards, but I don't think that has anything to do with the problem I'm having now).

Thanks everyone for the help and quick replies, I really appreciate it :)

---

### Post by Frogs Hair on 2013-07-03
```
sudo rm -rf /var/lib/apt/lists/* 
``````
sudo apt-get clean
``````
 sudo apt-get update
``` Post the output of the next command.


```
grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by poxyhead on 2013-07-03
Ok, so I played around with it a bit myself and I believe the problem was coming from the [voronov84/andreyv ppa]("https://launchpad.net/~voronov84/+archive/andreyv") I had added to use pgAdmin3 (I think this was the reason why the quantal partner was in there, too -- not sure).

After I removed the pgadmin3 package and ran
```

sudo ppa-purge ppa:voronov84/andreyv
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get clean
sudo apt-get update

```

I could then install git normally and it worked fine :)

Thank you everyone for all the help, I couldn't have done it without you! :) :) :)

---

### Post by Frogs Hair on 2013-07-04
Good Job ! To mark the thread solved go to first post > select edit > select go advanced > the prefix to solved and save.

---

