---
title: "Ubuntu 14 PYSFTP Installation"
date: 2015-09-28
forum: Installation &amp; Upgrades
---

### Post by Brad_Ridgeway on 2015-09-28
I am trying to install a Odoo 8 Automatic Backup addon which requires pysftp.  

When i enter "sudo pip install pysftp" it returns:

sudo: unable to resolve host ip-172-30-0-253
Requirement already satisfied (use --upgrade to upgrade): pysftp in /usr/local/lib/python2.7/dist-packages
Requirement already satisfied (use --upgrade to upgrade): paramiko>=1.7.7 in /usr/local/lib/python2.7/dist-packages (from pysftp)
Cleaning up...

It seems like pysftp is installed but Odoo does not see it and if I try sudo apt-get install pysftp it returns:

sudo: unable to resolve host ip-172-30-0-253
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package pysftp

Not sure what's going on?

Brad

---

### Post by Brad_Ridgeway on 2015-09-29
I can't seem to get pysftp installed on my Ubuntu 14.04.3 LTS (GNU/Linux 3.13.0-48-generic x86_64), please help.  

```
$ sudo apt-cache policy pysftp 

N: Unable to locate package pysftp

$ sudo apt-get update  - Result below 

$ sudo apt-get install pysftp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package pysftp

$ sudo apt-get update

ubuntu@ip-172-30-0-253:~$ sudo apt-get update
sudo: unable to resolve host ip-172-30-0-253
Ign [http://us-east-1.ec2.archive.ubuntu.com](http://us-east-1.ec2.archive.ubuntu.com) trusty InRelease
Ign [http://us-east-1.ec2.archive.ubuntu.com](http://us-east-1.ec2.archive.ubuntu.com) trusty-updates InRelease    
Hit [http://us-east-1.ec2.archive.ubuntu.com](http://us-east-1.ec2.archive.ubuntu.com) trusty Release.gpg          
Get:1 [http://us-east-1.ec2.archive.ubuntu.com](http://us-east-1.ec2.archive.ubuntu.com) trusty-updates Release.gpg [933 B]
Hit [http://us-east-1.ec2.archive.ubuntu.com](http://us-east-1.ec2.archive.ubuntu.com) trusty Release                     
Get:2 [http://us-east-1.ec2.archive.ubuntu.com](http://us-east-1.ec2.archive.ubuntu.com) trusty-updates Release [63.5 kB] 
Hit [http://us-east-1.ec2.archive.ubuntu.com](http://us-east-1.ec2.archive.ubuntu.com) trusty/main Sources                
Hit [http://us-east-1.ec2.archive.ubuntu.com](http://us-east-1.ec2.archive.ubuntu.com) trusty/universe Sources            
Hit [http://us-east-1.ec2.archive.ubuntu.com](http://us-east-1.ec2.archive.ubuntu.com) trusty/main amd64 Packages         
Hit [http://us-east-1.ec2.archive.ubuntu.com](http://us-east-1.ec2.archive.ubuntu.com) trusty/universe amd64 Packages     
Hit [http://us-east-1.ec2.archive.ubuntu.com](http://us-east-1.ec2.archive.ubuntu.com) trusty/main Translation-en         
Hit [http://us-east-1.ec2.archive.ubuntu.com](http://us-east-1.ec2.archive.ubuntu.com) trusty/universe Translation-en     
Get:3 [http://us-east-1.ec2.archive.ubuntu.com](http://us-east-1.ec2.archive.ubuntu.com) trusty-updates/main Sources [236 kB]
Get:4 [http://us-east-1.ec2.archive.ubuntu.com](http://us-east-1.ec2.archive.ubuntu.com) trusty-updates/universe Sources [138 kB]
Get:5 [http://us-east-1.ec2.archive.ubuntu.com](http://us-east-1.ec2.archive.ubuntu.com) trusty-updates/main amd64 Packages [627 kB]
Get:6 [http://us-east-1.ec2.archive.ubuntu.com](http://us-east-1.ec2.archive.ubuntu.com) trusty-updates/universe amd64 Packages [319 kB]
Get:7 [http://us-east-1.ec2.archive.ubuntu.com](http://us-east-1.ec2.archive.ubuntu.com) trusty-updates/main Translation-en [304 kB]
Get:8 [http://us-east-1.ec2.archive.ubuntu.com](http://us-east-1.ec2.archive.ubuntu.com) trusty-updates/universe Translation-en [168 kB]
Ign [http://us-east-1.ec2.archive.ubuntu.com](http://us-east-1.ec2.archive.ubuntu.com) trusty/main Translation-en_US      
Ign [http://us-east-1.ec2.archive.ubuntu.com](http://us-east-1.ec2.archive.ubuntu.com) trusty/universe Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://nightly.odoo.com](http://nightly.odoo.com) ./ InRelease                                       
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]
Hit [http://nightly.odoo.com](http://nightly.odoo.com) ./ Release.gpg                                     
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [63.5 kB]            
Hit [http://nightly.odoo.com](http://nightly.odoo.com) ./ Release                                         
Hit [http://nightly.odoo.com](http://nightly.odoo.com) ./ Packages                                        
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [96.2 kB]       
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [31.1 kB]   
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [350 kB] 
Ign [http://nightly.odoo.com](http://nightly.odoo.com) ./ Translation-en_US                               
Ign [http://nightly.odoo.com](http://nightly.odoo.com) ./ Translation-en                                  
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [117 kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [191 kB] 
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en [68.2 kB]
Fetched 2,773 kB in 2s (1,104 kB/s)                                            
Reading package lists... Done
```

---

### Post by ian-weisser on 2015-09-29
That's right, no such deb package.
Are you following instructions from someplace?

---

### Post by v3.xx on 2015-09-29
Not in my ubuntu sources, looks like it only available online.

[https://www.odoo.com/forum/help-1/question/how-to-install-pysftp-to-backup-data-87180](https://www.odoo.com/forum/help-1/question/how-to-install-pysftp-to-backup-data-87180)

---

### Post by Brad_Ridgeway on 2015-09-29
I need it for an Odoo 8 Automated backup module. After I download it to my home directory, what commands do I use to get it installed? 

I tried using "sudo pip install pysftp but Odoo does not see the pysftp that is installed so the module crashes the server.

Check my other post: [http://ubuntuforums.org/showthread.php?t=2296755&highlight=pysftp](http://ubuntuforums.org/showthread.php?t=2296755&highlight=pysftp)

Thanks,

Brad

---

### Post by v3.xx on 2015-09-29
I have no reason to install pysftp, but I tried anyhow.

```
cd ./pysftp-0.2.8/
setup.py install
```
Did not work.

So I tried making setup.py executable; that got me to setup.py needs setuptools and that is not installed on my box.  I don't think going any further on my setup will solve anything.  Perhaps someone with a better working knowledge will chime in.  Good luck :)

[https://pythonhosted.org/an_example_pypi_project/setuptools.html](https://pythonhosted.org/an_example_pypi_project/setuptools.html)

---

### Post by Brad_Ridgeway on 2015-09-29
Thanks for trying to help me out.  It looks like I need to find another solution.  Has anyone ever used autopostgresqlbackup to backup their Odoo database?

Thanks,

Brad

---

### Post by ian-weisser on 2015-09-29
Seems like a bug in the odoo addon.
Have you reported it to the addon developer?

---

### Post by howefield on 2015-09-29
Duplicate threads merged.

---

### Post by Brad_Ridgeway on 2015-09-30
Thanks to everyone for all your help! I downloaded pysftp-0.2.8 and installed it myself!

$sudo python setup.py install

Brad

---

### Post by v3.xx on 2015-09-30
Excellent :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by trevi-s on 2016-03-24
> **Brad_Ridgeway said:**
> Thanks to everyone for all your help! I downloaded pysftp-0.2.8 and installed it myself!

$sudo python setup.py install

Brad

Hi Brad
I'm desperately trying to install pysftp too and have the same problem as you did.
Can you please be more specific:
- did you download the pysftp-0.2.8.tar.gz?
- where did you move the file to?
- where did you find the setup.py file?

Thank you, trevi

---

### Post by oldos2er on 2016-03-24
Brad_Ridgeway hasn't visited the forum again since Sept. 2015. Please create a new thread for your questions; thanks.

Closed.

---

