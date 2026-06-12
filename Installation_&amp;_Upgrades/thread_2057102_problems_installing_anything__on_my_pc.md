---
title: "problems installing anything  on my pc"
date: 2012-09-13
forum: Installation &amp; Upgrades
---

### Post by jfluet on 2012-09-13
I cant seem to install anything I download, update manager always fails too. can't install or un-install on Ubuntu software centre. sudo apt-get install won't work either. not sure how to fix it. can anyone help! Thanks a bunch!
Jason

---

### Post by lisati on 2012-09-13
Are you getting an error message on your screen?

---

### Post by opensshd on 2012-09-13
Hi Jason,

Does it give any error messages when you try and use apt-get from the CLI (command line interface, or 'terminal')

---

### Post by jfluet on 2012-09-13
yah 
The disable|enable API is not stable and might change in the future.
dpkg: error processing nvidia-kernel-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encount

---

### Post by jfluet on 2012-09-13
I'm using lucid LTS if that make a difference, ever since I upgraded nothing seems to work right but firefox and transmission bit torrent.

---

### Post by opensshd on 2012-09-13
from [https://answers.launchpad.net/ubuntu/+source/nvidia-kernel-common/+question/118010](https://answers.launchpad.net/ubuntu/+source/nvidia-kernel-common/+question/118010) :

please try from terminal type:
```

cd /var/lib/dpkg/info
```

```
sudo cp nvidia-kernel-common.prerm nvidia-kernel-common.prerm.old
```

```
sudo echo -en "exit 0" | sudo tee nvidia-kernel-common.prerm
```

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

---

### Post by jfluet on 2012-09-13
it still gave me
 The disable|enable API is not stable and might change in the future.
dpkg: error processing nvidia-kernel-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 nvidia-kernel-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by jfluet on 2012-09-13
here's the whole thing 

jason@jason-desktop:~$ cd /var/lib/dpkg/info
jason@jason-desktop:/var/lib/dpkg/info$ 
jason@jason-desktop:/var/lib/dpkg/info$ 
jason@jason-desktop:/var/lib/dpkg/info$ sudo cp nvidia-kernel-common.prerm nvidia-kernel-common.prerm.old
[sudo] password for jason: 
jason@jason-desktop:/var/lib/dpkg/info$ sudo echo -en "exit 0" | sudo tee nvidia-kernel-common.prerm
exit 0jason@jason-desktop:/var/lib/dpkg/info$ sudo apt-get update
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Ign [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main Translation-en_CA        
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://dl.google.com](http://dl.google.com) stable/main Packages                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_CA       
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_CA   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_CA
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/happy-neko/ps3mediaserver/ubuntu/](http://ppa.launchpad.net/happy-neko/ps3mediaserver/ubuntu/) lucid/main Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_CA             
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_CA         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_CA       
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg [198B]               
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_CA 
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_CA     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [57.3kB]               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release                                    
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release [58.3kB]               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [135kB]      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources 
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages [277kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [441kB]        
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [5,353B]   
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [2,867B]   
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [42.0kB]     
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [130kB]          
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [2,321B]   
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [1,267B]   
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages [638kB]           
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages [11.5kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages [4,630B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources [103kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources [227kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources [5,821B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources [2,196B]
Fetched 2,145kB in 6s (320kB/s)                                                
Reading package lists... Done
jason@jason-desktop:/var/lib/dpkg/info$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up nvidia-kernel-common (20051028+1ubuntu7) ...
update-rc.d: warning: /etc/init.d/nvidia-kernel missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
       update-rc.d [-n] <basename> disable|enable [S|2|3|4|5]
		-n: not really
		-f: force

The disable|enable API is not stable and might change in the future.
dpkg: error processing nvidia-kernel-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 nvidia-kernel-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
jason@jason-desktop:/var/lib/dpkg/info$

---

### Post by opensshd on 2012-09-13
mmmkay, how bout this one?

[https://answers.launchpad.net/ubuntu/+source/apt/+question/118518](https://answers.launchpad.net/ubuntu/+source/apt/+question/118518)

btw, to undo the changes we made to the system in the last commands just do

```

cd /var/lib/dpkg/info

sudo cp nvidia-kernel-common.prerm.old nvidia-kernel-common.prerm
```

---

### Post by opensshd on 2012-09-13
I think the gist of it is 
```

sudo dpkg --force all --remove nvidia-kernel-common

```
then
sudo apt-get update

sudo apt-get upgrade

---

### Post by jfluet on 2012-09-13
now I got. but I think were almost there

The disable|enable API is not stable and might change in the future.
dpkg: error processing nvidia-kernel-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up tzdata-java (2012e-0ubuntu0.10.04) ...
Errors were encountered while processing:
 nvidia-kernel-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
jason@jason-desktop:/var/lib/dpkg/info$

---

### Post by opensshd on 2012-09-13
So trying this didn't work?

sudo dpkg --force all --remove nvidia-kernel-common

---

### Post by jfluet on 2012-09-13
no I still get 
jason@jason-desktop:/var/lib/dpkg/info$

---

### Post by opensshd on 2012-09-13
Hmm... what happens when you try to upgrade the distribution:

sudo apt-get dist-upgrade

?

---

### Post by jfluet on 2012-09-13
jason@jason-desktop:/var/lib/dpkg/info$ sudo apt-get dist-upgrade
[sudo] password for jason: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up nvidia-kernel-common (20051028+1ubuntu7) ...
update-rc.d: warning: /etc/init.d/nvidia-kernel missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
       update-rc.d [-n] <basename> disable|enable [S|2|3|4|5]
		-n: not really
		-f: force

The disable|enable API is not stable and might change in the future.
dpkg: error processing nvidia-kernel-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 nvidia-kernel-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
jason@jason-desktop:/var/lib/dpkg/info$

---

### Post by opensshd on 2012-09-13
try this solution?

[http://ubuntuforums.org/showthread.php?t=1482704&page=2](http://ubuntuforums.org/showthread.php?t=1482704&page=2)

---

### Post by jfluet on 2012-09-13
I'm back to
jason@jason-desktop:~$ 
thanks

---

### Post by opensshd on 2012-09-13
Ok, it worked? 

You can test by trying 

sudo apt-get update

Still giving the same error?

---

### Post by jfluet on 2012-09-13
no error this time thanks a bunch for the help!

---

### Post by opensshd on 2012-09-13
Nice!

---

