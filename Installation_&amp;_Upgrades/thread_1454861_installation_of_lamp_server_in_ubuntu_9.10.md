---
title: "installation of lamp server in ubuntu 9.10"
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by yasokrish on 2010-04-15
Hi,
 iam using ubuntu 9.10.
I tried to install lamp server using the command
**sudo tasksel install lamp-server**
It shows this error:
**tasksel:aptitude failed(100)**

i tried to fix the problem by using the command

**sudo apt-get update **
 but it shows a list of cannnot fetch and many more.
example:
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-](http://in.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-)
i386/Packages.gz  404  Not Found [IP: 111.91.91.34 80]

Can anyone fix this problem.
Please explain the steps in detail.

Thanks a lot.
yasokrish.

---

### Post by cavh on 2010-04-15
Can you access any web sites? It sounds like your connection to the outside world may be down, in which case you will be unable to fetch packages.

---

### Post by yasokrish on 2010-04-15
ya. my net connection is perfect..

---

### Post by dominiquec on 2010-04-15
Perhaps the Indian repo is down?  That's what I gather from the error message.  Try choosing a different repository temporarily.

Also, do a 

```
sudo apt-get update
```

to refresh your repository list.

---

### Post by yasokrish on 2010-04-15
THIS IS THE ERROR mSG i get when i use the command:
sudo apt-get update

Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Translation-en_IN       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Translation-en_IN         
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Translation-en_IN       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates Release.gpg                
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Translation-en_IN  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic Release                             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates Release                     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Packages                       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Sources
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Packages
  404  Not Found [IP: 111.91.91.34 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Packages
  404  Not Found [IP: 111.91.91.34 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Sources
  404  Not Found [IP: 111.91.91.34 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Sources
  404  Not Found [IP: 111.91.91.34 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Packages
  404  Not Found [IP: 111.91.91.34 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Sources
  404  Not Found [IP: 111.91.91.34 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Packages
  404  Not Found [IP: 111.91.91.34 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Sources
  404  Not Found [IP: 111.91.91.34 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Packages
  404  Not Found [IP: 111.91.91.34 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Packages
  404  Not Found [IP: 111.91.91.34 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Sources
  404  Not Found [IP: 111.91.91.34 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Sources
  404  Not Found [IP: 111.91.91.34 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Packages
  404  Not Found [IP: 111.91.91.34 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Sources
  404  Not Found [IP: 111.91.91.34 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Packages
  404  Not Found [IP: 111.91.91.34 80]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Sources
  404  Not Found [IP: 111.91.91.34 80]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found [IP: 111.91.91.34 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 111.91.91.34 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz)  404  Not Found [IP: 111.91.91.34 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz)  404  Not Found [IP: 111.91.91.34 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz)  404  Not Found [IP: 111.91.91.34 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz)  404  Not Found [IP: 111.91.91.34 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 111.91.91.34 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz)  404  Not Found [IP: 111.91.91.34 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz)  404  Not Found [IP: 111.91.91.34 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 111.91.91.34 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz)  404  Not Found [IP: 111.91.91.34 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz)  404  Not Found [IP: 111.91.91.34 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz)  404  Not Found [IP: 111.91.91.34 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz)  404  Not Found [IP: 111.91.91.34 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 111.91.91.34 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz)  404  Not Found [IP: 111.91.91.34 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by yasokrish on 2010-04-15
Can anyone fix this??
what problem is my apt-get update is facing ?
how do i rectify it?


Thanks a lot,
yasokrish

---

### Post by dominiquec on 2010-04-15
As I said, most likely you cannot reach your repository.

Try pinging in.archive.ubuntu.com.  Is it reachable?

If not, consider using another repository temporarily.  Open Synaptic, then go to Settings->Repository. Choose another server.

(On another note, your in.archive.ubuntu.com resolves to 111.91.91.34, but in my case, it's 91.189.88.45.  It might be a DNS problem on your part.)

---

### Post by yasokrish on 2010-04-15
Hi,

Thanks a lot.I chose a different server and this was the output
i was able to download packages without previous "fetch problem"..

Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                       
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_IN         
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_IN
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_IN
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_IN
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Translation-en_IN
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Packages
Reading package lists... Done

then it asked for a mysql root password

after some progress it shows the same error.
tasksel: aptitude failed(100)

as for now ,the apt-get update problem is solved,
What else might be wrong??

What is that DNS problem and how do i solve it?

Thanks a lot,
yasokrish.

---

### Post by yasokrish on 2010-04-15
Hi,


I used the command

sudo apt-get update again which instructed me to use the command

sudo dpkg --configure -a

i did and it shows the following error msg..

Setting up ufw (0.29-4ubuntu1) ...
dpkg: error processing ufw (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ufw

what does this mean??
How can we fix this??

Thank you,
yasokrish.

---

### Post by cavh on 2010-04-15
This is the output of ```
man ufw
``` on my machine:  

NAME
       ufw - program for managing a netfilter firewall

DESCRIPTION
       This  program  is  for managing a Linux firewall and aims to provide an
       easy to use interface for the user.

I would think that ufw is installed as part of the Apache install. Try installing it manually then running *tasksel* again:

```
sudo apt-get install ufw
```

---

### Post by dominiquec on 2010-04-15
ufw is a firewall.  If you're just doing local development (as I suppose you are), you don't need it for now.

The simplest way to get a LAMP server running, in my experience is

```
sudo apt-get install apache2 php5 php5-mysql mysql-server
```

Your Apache root directory is in /var/www.

---

### Post by yasokrish on 2010-04-16
Hi,
i tried the command as suggested.
**sudo apt-get install ufw**

My output...
 How do i proceede???

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ufw is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 252 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ufw (0.29-4ubuntu1) ...
dpkg: error processing ufw (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ufw
E: Sub-process /usr/bin/dpkg returned an error code (1)

Thank you,
yasokrish

---

### Post by yasokrish on 2010-04-16
Hi,

As suggested i tried the command

sudo apt-get install apache2 php5 php5-mysql mysql-server
And my output is  :

Reading package lists... Done
Building dependency tree       
Reading state information... Done
apache2 is already the newest version.
php5-mysql is already the newest version.
mysql-server is already the newest version.
The following NEW packages will be installed:
  php5
0 upgraded, 1 newly installed, 0 to remove and 252 not upgraded.
1 not fully installed or removed.
Need to get 1,124B of archives.
After this operation, 20.5kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main php5 5.2.10.dfsg.1-2ubuntu6.4 [1,124B]
Fetched 1,124B in 0s (1,988B/s)
Selecting previously deselected package php5.
(Reading database ... 116182 files and directories currently installed.)
Unpacking php5 (from .../php5_5.2.10.dfsg.1-2ubuntu6.4_all.deb) ...
Setting up ufw (0.29-4ubuntu1) ...
dpkg: error processing ufw (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up php5 (5.2.10.dfsg.1-2ubuntu6.4) ...
Errors were encountered while processing:
 ufw
E: Sub-process /usr/bin/dpkg returned an error code (1)

Whats the problem?? how to rectify it??

Thank you,
yasokrish.

---

### Post by dominiquec on 2010-04-16
You seem to have a problem with ufw, the firewall.  If you just want to get started on LAMP development, you don't need it.

---

