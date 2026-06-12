---
title: "Can't start synaptic package manager and/or system update"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by bmcsorley on 2008-08-12
Hi,

I'm unable to run either the synaptic package manager or system update and get the below error for both. I know I have updates to install as have the little orange notification in the task bar but unable to see what they are.


E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ftp.heanet.ie_pub_ubuntu_dists_gutsy_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Thanks,
BMc

---

### Post by iaculallad on 2008-08-12
On your terminal, try:

```
sudo dpkg --clear-avail
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by bmcsorley on 2008-08-13
Hi,

Thanks for replying. I've tried what you suggested and results below - looks like the same error? Just tried the package manager again and same thing.

desktop:~$ sudo dpkg --clear-avail
[sudo] password :
desktop:~$ sudo apt-get update && sudo apt-get upgrade
Get:1 [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy Release.gpg [191B]
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/main Translation-en_IE
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/restricted Translation-en_IE
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/universe Translation-en_IE
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/multiverse Translation-en_IE
Get:2 [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates Release.gpg [189B]
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates/main Translation-en_IE
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates/restricted Translation-en_IE
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates/universe Translation-en_IE
Get:3 [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security Release.gpg [189B]
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/main Translation-en_IE
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/restricted Translation-en_IE
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/universe Translation-en_IE
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/multiverse Translation-en_IE
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy Release
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates Release
Get:4 [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security Release [58.5kB]
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/main Packages        
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/restricted Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/main Sources
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/restricted Sources
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/universe Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/universe Sources
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/multiverse Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/multiverse Sources
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates/main Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates/restricted Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates/main Sources
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates/restricted Sources
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates/universe Packages
Get:5 [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/main Packages [107kB]
Get:6 [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/restricted Packages [5280B]
Get:7 [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/main Sources [20.6kB]
Get:8 [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/restricted Sources [944B]
Get:9 [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/universe Packages [76.4kB]
Get:10 [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/universe Sources [11.6kB]
Get:11 [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/multiverse Packages [5774B]
Get:12 [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/multiverse Sources [812B]
Fetched 287kB in 3s (77.7kB/s)                   
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ftp.heanet.ie_pub_ubuntu_dists_gutsy_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by iaculallad on 2008-08-13
On your terminal:

```
sudo apt-get update -o APT::Cache-Limit=25165824
```

then

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by rohas on 2008-08-13
Hello everyone,
well i have the same problem with different output error
My error is 

dpkg: parse error, in file '/var/lib/dpkg/updates/0175' near line 4: missing package name

i believe that the trick is to "clear" everything that was downloaded and start all over the update process again...but i don't know how i can do this !!! any ideas for achieving this ?

---

### Post by bmcsorley on 2008-08-13
No go I'm afraid - still same error with above commands.....

desktop:~$ sudo apt-get update -o APT::Cache-Limit=25165824
[sudo] password :
Get:1 [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy Release.gpg [191B]
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/main Translation-en_IE
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/restricted Translation-en_IE
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/universe Translation-en_IE
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/multiverse Translation-en_IE
Get:2 [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates Release.gpg [189B]
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates/main Translation-en_IE
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates/restricted Translation-en_IE
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates/universe Translation-en_IE
Get:3 [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security Release.gpg [189B]
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/main Translation-en_IE
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/restricted Translation-en_IE
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/universe Translation-en_IE
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/multiverse Translation-en_IE
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy Release
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates Release
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security Release
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/main Packages  
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/restricted Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/main Sources
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/restricted Sources
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/universe Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/universe Sources
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/multiverse Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/multiverse Sources
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates/main Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates/restricted Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates/main Sources
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates/restricted Sources
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates/universe Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/main Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/restricted Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/main Sources
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/restricted Sources
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/universe Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/universe Sources
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/multiverse Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/multiverse Sources
Fetched 3B in 2s (1B/s)                         
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ftp.heanet.ie_pub_ubuntu_dists_gutsy_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
desktop:~$ sudo apt-get update && sudo apt-get upgrade
Get:1 [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy Release.gpg [191B]
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/main Translation-en_IE
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/restricted Translation-en_IE
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/universe Translation-en_IE
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/multiverse Translation-en_IE
Get:2 [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates Release.gpg [189B]
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates/main Translation-en_IE
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates/restricted Translation-en_IE
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates/universe Translation-en_IE
Get:3 [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security Release.gpg [189B]
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/main Translation-en_IE
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/restricted Translation-en_IE
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/universe Translation-en_IE
Ign [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/multiverse Translation-en_IE
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy Release
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates Release
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security Release
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/main Packages  
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/restricted Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/main Sources
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/restricted Sources
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/universe Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/universe Sources
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/multiverse Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy/multiverse Sources
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates/main Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates/restricted Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates/main Sources
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates/restricted Sources
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-updates/universe Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/main Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/restricted Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/main Sources
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/restricted Sources
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/universe Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/universe Sources
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/multiverse Packages
Hit [http://ftp.heanet.ie](http://ftp.heanet.ie) gutsy-security/multiverse Sources
Fetched 3B in 1s (2B/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ftp.heanet.ie_pub_ubuntu_dists_gutsy_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
desktop:~$

---

### Post by bmcsorley on 2008-08-17
Hi,

So is the best way of sorting this to install Synaptic package manager and reinstall? If so then any ideas how to do this?

Bit of a newbie to Ubuntu hence the questions.... :)

BMc

---

### Post by bmcsorley on 2008-08-29
Hi,

Any other ideas? Really stuck with this and want to install new versions of Firefox etc.

Cheers,
B

---

### Post by GTgem on 2009-02-13
> **bmcsorley said:**
> Hi,

I'm unable to run either the synaptic package manager or system update and get the below error for both. I know I have updates to install as have the little orange notification in the task bar but unable to see what they are.


E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ftp.heanet.ie_pub_ubuntu_dists_gutsy_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Thanks,
BMc

Exact same problem here, anyone have any ideas?

---

### Post by gabo.cr on 2009-02-13
You can try this in terminal:

sudo dpkg  --configure  -a


I hope it helps

---

### Post by Taemojitsu on 2009-02-13
I know I got something about _cache=>open when I put the wrong line into sources.list that it couldn't parse... but this is saying something about a specific repository isn't it?

If your Ubuntu is pointing at a repository that's broken, would it give this error? Might this be that a repository is configured wrong, and if so how would you escalate the problem so it could be fixed..?

---

### Post by GTgem on 2009-02-14
> **gabo.cr said:**
> You can try this in terminal:

sudo dpkg  --configure  -a


I hope it helps

I've just tried that and may have found the source of my problem, which was probably a crash during installation, but this is what your code has given me:
dpkg: parse error, in file `/var/lib/dpkg/status' near line 25573:
 field name `' must be followed by colon

How can I fix that or how can I put in place that colon?

---

### Post by gabo.cr on 2009-02-14
!

This should work:

sudo dpkg --clear-avail
sudo apt-get update

---

