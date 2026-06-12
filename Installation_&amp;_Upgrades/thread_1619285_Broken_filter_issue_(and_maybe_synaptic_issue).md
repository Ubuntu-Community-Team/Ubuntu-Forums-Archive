---
title: "Broken filter issue (and maybe synaptic issue?)"
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by aetherguy881 on 2010-11-11
I've had some broken packages for a while, I've gotten around to trying to fix the situation.

I didn't know how to find them, and found this thread [archived](http://ubuntuforums.org/showthread.php?t=247800).

That helped, however now when I try to mark an installation or removal, the synaptic crashes and closes.

If it helps any the broken packages are libc6-dev and libc6-i686.

Thanks.

---

### Post by sikander3786 on 2010-11-12
Please try

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

If errors are reported, post them here.

---

### Post by aetherguy881 on 2010-11-12
I got a segmentation fault on the first command... So the problem is still there.

By the way, that's the first time someone's said please try this when I'm asking for help. I wasn't expecting that.

Thanks.

---

### Post by sikander3786 on 2010-11-12
You need to post the exact output so we can see what happened actually.

Thanks for the compliments :-)

---

### Post by aetherguy881 on 2010-11-13
```
mobile1:~$ sudo apt-get install -f
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Segmentation fault
mobile1:~$ sudo dpkg --configure -a
mobile1:~$
```

---

### Post by sikander3786 on 2010-11-13
Try cleaning your apt-get cache.

```
sudo apt-get clean
```

And again,

```
sudo apt-get install -f
```

```
sudo apt-get update
```

Please post the output if errors persist.

---

### Post by aetherguy881 on 2010-11-13
```
mobile1:~$ sudo apt-get clean
mobile1:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Segmentation fault
mobile1:~$ sudo dpkg --configure -a
mobile1:~$ 
```

---

### Post by Quackers on 2010-11-13
If you open Synaptic Package Manager and look at the bottom left of the screen it'll say something like "33125 packages listed, 17105 installed, then it will give details of any broken packages. Are there any shown? If there are you can click on the EDIT menu and select "fix broken packages". See how that goes.

---

### Post by aetherguy881 on 2010-11-13
Once I tell it to fix the broken packages, the synaptic crashes as mentioned previously...

:-?

---

### Post by sikander3786 on 2010-11-13
Can you please post the output of

```
sudo apt-get update
```

The problem is there is no package name mentioned in this output.

> ```
mobile1:~$ sudo apt-get clean
mobile1:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Segmentation fault
mobile1:~$ sudo dpkg --configure -a
mobile1:~$
```

There must be some offending package and apt-get update might refer to it in the output. Thanks.

---

### Post by Quackers on 2010-11-13
Oh dear. I'm afraid you need more expert advice than I can give! Hopefully somebody will be along shortly who can help. Good luck to you :-)
Aha! sikander is back :-)

---

### Post by aetherguy881 on 2010-11-13
```
mobile1:~$ sudo apt-get update
Get:1 http://dl.google.com stable Release.gpg [189B]
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US   
Get:2 http://dl.google.com stable Release [1,338B]                             
Get:3 http://archive.canonical.com lucid Release.gpg [198B]                    
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
Get:4 http://security.ubuntu.com lucid-security Release.gpg [198B]     
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Get:5 http://dl.google.com stable/main Packages [613B]                         
Get:6 http://archive.canonical.com lucid Release [8,215B]                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Get:7 http://security.ubuntu.com lucid-security Release [38.5kB]             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US    
Get:8 http://us.archive.ubuntu.com lucid-updates Release.gpg [198B]            
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release                                 
Get:9 http://us.archive.ubuntu.com lucid-updates Release [44.7kB]              
Get:10 http://archive.canonical.com lucid/partner Packages [11.8kB]            
Get:11 http://security.ubuntu.com lucid-security/restricted Packages [14B]     
Get:12 http://archive.canonical.com lucid/partner Sources [5,079B]             
Get:13 http://security.ubuntu.com lucid-security/main Packages [98.5kB]
Hit http://us.archive.ubuntu.com lucid/main Packages    
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources     
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources  
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Get:14 http://us.archive.ubuntu.com lucid-updates/restricted Packages [3,240B]
Get:15 http://us.archive.ubuntu.com lucid-updates/main Packages [343kB]
Get:16 http://security.ubuntu.com lucid-security/multiverse Packages [2,013B]  
Get:17 http://security.ubuntu.com lucid-security/universe Packages [47.5kB]    
Get:18 http://us.archive.ubuntu.com lucid-updates/multiverse Packages [7,373B] 
Get:19 http://us.archive.ubuntu.com lucid-updates/universe Packages [146kB]
Fetched 759kB in 2s (364kB/s)                           
Reading package lists... Done
mobile1:~$
```

---

### Post by sikander3786 on 2010-11-13
Nothing wrong with apt-get update output there.

Is Synaptic still crashing? Are these commands successful?

```
sudo apt-get upgrade
```

```
sudo apt-get install --reinstall libc6-dev libc6-i686
```

---

### Post by aetherguy881 on 2010-11-13
Thank you sikander, that worked.

---

