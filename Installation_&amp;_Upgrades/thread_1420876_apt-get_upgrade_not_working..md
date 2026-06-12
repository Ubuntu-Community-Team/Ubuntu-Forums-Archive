---
title: "apt-get upgrade not working."
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by SlickStretch on 2010-03-03
Sorry, typo in the title... So I try to run sudo apt-get update.  It doesn't seem to work.  I get a lot of 404 errors, and files that can't be found.  I'm brand new to this whole linux thing...  This is what came from the terminal:

```
stretch@dv7-ubuntu:~$ sudo apt-get update
Get:1 http://archive.ubuntu.com karmic Release.gpg [189B]           
Ign http://archive.ubuntu.com karmic/multiverse Translation-en_US   
Ign http://security.ubuntu.com edgy-security Release.gpg             
Ign http://security.ubuntu.com edgy-security/main Translation-en_US  
Ign http://us.archive.ubuntu.com edgy Release.gpg                    
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US         
Ign http://archive.ubuntu.com karmic/universe Translation-en_US      
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Get:2 http://archive.ubuntu.com karmic Release [65.9kB]              
Ign http://security.ubuntu.com edgy-security Release                     
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US       
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US
Ign http://us.archive.ubuntu.com edgy/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates Release.gpg
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy-backports Release.gpg
Ign http://us.archive.ubuntu.com edgy-backports/main Translation-en_US
Ign http://security.ubuntu.com edgy-security/main Packages               
Ign http://us.archive.ubuntu.com edgy-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com edgy-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com edgy Release                              
Ign http://us.archive.ubuntu.com edgy-updates Release                      
Ign http://us.archive.ubuntu.com edgy-backports Release                    
Ign http://security.ubuntu.com edgy-security/restricted Packages           
Ign http://security.ubuntu.com edgy-security/main Sources
Ign http://security.ubuntu.com edgy-security/restricted Sources             
Ign http://us.archive.ubuntu.com edgy/main Packages                         
Ign http://us.archive.ubuntu.com edgy/restricted Packages                   
Ign http://us.archive.ubuntu.com edgy/main Sources                          
Ign http://us.archive.ubuntu.com edgy/restricted Sources                    
Ign http://us.archive.ubuntu.com edgy/universe Packages                     
Ign http://us.archive.ubuntu.com edgy/universe Sources                      
Ign http://security.ubuntu.com edgy-security/universe Packages              
Ign http://security.ubuntu.com edgy-security/universe Sources               
Ign http://security.ubuntu.com edgy-security/main Packages                  
Ign http://security.ubuntu.com edgy-security/restricted Packages            
Ign http://us.archive.ubuntu.com edgy/multiverse Packages                   
Ign http://us.archive.ubuntu.com edgy/multiverse Sources                    
Ign http://us.archive.ubuntu.com edgy-updates/main Packages                 
Ign http://us.archive.ubuntu.com edgy-updates/restricted Packages           
Ign http://security.ubuntu.com edgy-security/main Sources                   
Ign http://security.ubuntu.com edgy-security/restricted Sources
Ign http://security.ubuntu.com edgy-security/universe Packages
Ign http://us.archive.ubuntu.com edgy-updates/main Sources            
Ign http://us.archive.ubuntu.com edgy-updates/restricted Sources      
Ign http://us.archive.ubuntu.com edgy-backports/main Packages         
Ign http://us.archive.ubuntu.com edgy-backports/restricted Packages   
Ign http://us.archive.ubuntu.com edgy-backports/universe Packages     
Ign http://us.archive.ubuntu.com edgy-backports/multiverse Packages   
Ign http://security.ubuntu.com edgy-security/universe Sources         
Err http://security.ubuntu.com edgy-security/main Packages
  404  Not Found [IP: 91.189.88.37 80]
Ign http://us.archive.ubuntu.com edgy-backports/main Sources         
Ign http://us.archive.ubuntu.com edgy-backports/restricted Sources   
Ign http://us.archive.ubuntu.com edgy-backports/universe Sources     
Ign http://us.archive.ubuntu.com edgy-backports/multiverse Sources   
Get:3 http://archive.ubuntu.com karmic/multiverse Packages [185kB]   
Err http://security.ubuntu.com edgy-security/restricted Packages          
  404  Not Found [IP: 91.189.88.37 80]
Err http://security.ubuntu.com edgy-security/main Sources                 
  404  Not Found [IP: 91.189.88.37 80]
Err http://security.ubuntu.com edgy-security/restricted Sources           
  404  Not Found [IP: 91.189.88.37 80]
Ign http://us.archive.ubuntu.com edgy/main Packages                         
Ign http://us.archive.ubuntu.com edgy/restricted Packages                   
Ign http://us.archive.ubuntu.com edgy/main Sources                          
Ign http://us.archive.ubuntu.com edgy/restricted Sources                    
Ign http://us.archive.ubuntu.com edgy/universe Packages                     
Ign http://us.archive.ubuntu.com edgy/universe Sources                      
Err http://security.ubuntu.com edgy-security/universe Packages              
  404  Not Found [IP: 91.189.88.37 80]
Err http://security.ubuntu.com edgy-security/universe Sources               
  404  Not Found [IP: 91.189.88.37 80]
Ign http://us.archive.ubuntu.com edgy/multiverse Packages                   
Ign http://us.archive.ubuntu.com edgy/multiverse Sources
Ign http://us.archive.ubuntu.com edgy-updates/main Packages
Ign http://us.archive.ubuntu.com edgy-updates/restricted Packages
Ign http://us.archive.ubuntu.com edgy-updates/main Sources
Ign http://us.archive.ubuntu.com edgy-updates/restricted Sources
Ign http://us.archive.ubuntu.com edgy-backports/main Packages
Ign http://us.archive.ubuntu.com edgy-backports/restricted Packages
Ign http://us.archive.ubuntu.com edgy-backports/universe Packages
Ign http://us.archive.ubuntu.com edgy-backports/multiverse Packages
Ign http://us.archive.ubuntu.com edgy-backports/main Sources        
Ign http://us.archive.ubuntu.com edgy-backports/restricted Sources  
Ign http://us.archive.ubuntu.com edgy-backports/universe Sources    
Ign http://us.archive.ubuntu.com edgy-backports/multiverse Sources  
Get:4 http://archive.ubuntu.com karmic/universe Packages [5,108kB]  
Err http://us.archive.ubuntu.com edgy/main Packages                            
  404  Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy/restricted Packages
  404  Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy/main Sources    
  404  Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy/restricted Sources
  404  Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy/universe Packages
  404  Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy/universe Sources
  404  Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy/multiverse Packages
  404  Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy/multiverse Sources
  404  Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy-updates/main Packages
  404  Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy-updates/restricted Packages
  404  Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy-updates/main Sources
  404  Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy-updates/restricted Sources
  404  Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy-backports/main Packages
  404  Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy-backports/restricted Packages
  404  Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy-backports/universe Packages
  404  Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy-backports/multiverse Packages
  404  Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy-backports/main Sources
  404  Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy-backports/restricted Sources
  404  Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy-backports/universe Sources
  404  Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy-backports/multiverse Sources
  404  Not Found [IP: 91.189.88.46 80]
Fetched 5,359kB in 10s (502kB/s)                                               
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.37 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.37 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz  404  Not Found [IP: 91.189.88.37 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz  404  Not Found [IP: 91.189.88.37 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.37 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz  404  Not Found [IP: 91.189.88.37 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/source/Sources.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/source/Sources.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.88.46 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by kansasnoob on 2010-03-03
Edgy is old, really old!

Support for Edgy ended in April 2008!

Where did you get an Edgy disc?

If you're new to this I recommend either Hardy or Jaunty:

[http://releases.ubuntu.com/releases/8.04/](http://releases.ubuntu.com/releases/8.04/)

[http://releases.ubuntu.com/releases/9.04/](http://releases.ubuntu.com/releases/9.04/)

---

### Post by kansasnoob on 2010-03-03
Upon closer look are you trying to upgrade from Edgy to Karmic?

I don't think that can be done.

---

### Post by SlickStretch on 2010-03-06
I thought I had installed ubuntu 9.10. "Karmic Koala"
I used the torrent download from the ubuntu site.
When I run System > About Ubuntu
It says: "You are using Ubuntu 9.10 - the *Karmic Koala* - released in October 2009 and supported until April 2011."

---

### Post by -kg- on 2010-03-06
That's the derned-est thing I ever did see!

I did see "Karmic" lines interspersed between the Edgy lines.  It looks like somehow you have the repos for Edgy instead of the ones for Karmic.

Open "system/administration/software sources," make sure all the boxes are checked under the first tab (except for "source code," unless you are interested), and that they say "karmic," of course, and check what is checked under the second tab.  It should all be Karmic, and if it isn't, I don't quite know what to say, since all of this should be pointed to the correct repos for the installation.

---

### Post by mkljun on 2011-11-23
To upgrade a really old releases, we first need to edit our sources.list and change all (xx.)archive.ubuntu.com to old-releases.ubuntu.com.

```
sudo emacs /etc/apt/sources.list
```

So your lines should instead of 

```
deb http://archive.ubuntu.com/ubuntu jaunty main restricted universe
```

look like 

```
deb http://old-releases.ubuntu.com/ubuntu jaunty main restricted universe
```

In this example I use jaunty release. But it works the same on other releases.

Now update the repos

```
sudo apt-get update
```

Install update-manager-core if it is not yet installed:

```
sudo apt-get install update-manager-core
```

And now upgrade your system. 

```
sudo do-release-upgrade
```

Note that you can just upgrade to the next release (in my example from 9.04 to 9.10 or from LTS 8.04 to 10.04).

Also note that if upgrading over the ssh session it is advised to run the upgrade in the screen. So if the ssh session drops, the upgrade will continue. Install screen first (if not yet installed)

```
sudo apt-get install screen
```

Now run screen

```
screen
```

And upgrade with 

```
sudo do-release-upgrade
```

How to return to the screen is beyond this post.

lp mk

---

### Post by dotku on 2012-03-28
I go the error
> 
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.166 80]
[http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.166 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.181 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.181 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.181 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.181 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.181 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.181 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.181 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.181 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.181 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.181 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.181 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.181 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.181 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.181 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.181 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.181 80]

---

### Post by mörgæs on 2012-03-28
Please don't post the same question in multiple threads. 

Besides, this thread is obsolete, so closed.

---

