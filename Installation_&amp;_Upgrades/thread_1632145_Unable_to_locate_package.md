---
title: "Unable to locate package"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by janko68 on 2010-11-27
I just installed Ubuntu 10.10 Server and started playing with it. I would like to install some additional packages using apt-get, but every time I am confronted with "E: Unable to locate package xyz". What's wrong?

---

### Post by efflandt on 2010-11-27
Are you doing **sudo apt-get install xyz**?  It may depend which repository those packages are in and whether those repositories are enabled.  I am no expert on apt-get, but if you list which packages you are looking for, someone may be able to help.

---

### Post by janko68 on 2010-11-27
> **efflandt said:**
> Are you doing **sudo apt-get install xyz**?  It may depend which repository those packages are in and whether those repositories are enabled.  I am no expert on apt-get, but if you list which packages you are looking for, someone may be able to help.
Yes, I am doing sudo apt-get install xyz. I am trying to get any package, tried to install ethtool, apache2 and some others. Always get the same error.

---

### Post by Frogs Hair on 2010-11-27
Hi and Welcome 

That will happen if the package name is typed incorrectly , you can  double check package name in the software center or install from there. The terminal is case sensitive for some operations , use lower case for installing packages. sudo apt-get install name

---

### Post by janko68 on 2010-11-27
> **Frogs Hair said:**
> Hi and Welcome 

That will happen if the package name is typed incorrectly , you can  double check package name in the software center or install from there. The terminal is case sensitive for some operations , use lower case for installing packages. sudo apt-get install name
Thanks, but that is not the case. I am sure that I typed the package names correctly.

---

### Post by EMWolf on 2010-12-01
I just installed Ubuntu Server 10.10 as well and I'm having the exact same problem.
 
Is there anyone who can help with this issue out there?

---

### Post by sikander3786 on 2010-12-01
> **EMWolf said:**
> I just installed Ubuntu Server 10.10 as well and I'm having the exact same problem.
 
Is there anyone who can help with this issue out there?
Please list the package that you are trying to install so we might locate the correct repository for that and guide you how to enable it.

Also, post the output of this one.

```
cat /etc/apt/sources.list
```

---

### Post by EMWolf on 2010-12-02
I was trying to install ETHTOOL manually so I could configure my NIC; I did not choose the option during installation of UBUNTU. I became impatient and decided just to re-install and allow the setup/installation process do it for me, since I couldn't find a quick answer on the internet.
 
Could not install ethtool; "Unable to locate package ..."
Could not install apt-get; "Unable to locate package ..."
 
These prompts were both after the prompts (respectively);
"Reading package lists...Done
"Building dependency tree"
"Reading state information...Done"

---

### Post by sikander3786 on 2010-12-02
Try,

```
sudo apt-get update && sudo apt-get install ethtool
```

---

### Post by EMWolf on 2010-12-02
Ah, maybe I understand the problem now; it tries to download from a web server.
 
I did not configure my NIC (during installation) and I have it strictly 'stand-alone' and offline (no internet connectivity). 
 
I was 'assuming' that a standard tool like 'apt-get' and 'ethtool' would be available from the default installation files. (from the return prompts, I would say the answer is 'No')
 
Are these tools available from the CD or in the default installation files?
 
Thanks for your help btw! :D

---

### Post by sikander3786 on 2010-12-02
Not sure about their availability in the default installation media.

You can try this command to bring up your NIC for time being.

```
dhclient eth0
```

Where eth0 is your network interface.

---

### Post by sanco60 on 2010-12-11
"unable to locate package" i met the same problem.
and i tried the "apt-get update" 
then "apt-get install xxx" worked.
 
it seems u should update the apt-get at first.

---

### Post by [RIT]IVIr_Evil on 2010-12-12
Do you always need to run apt-get update prior to the install option moving forward or is it a one time thing? 

Thanks, 

-IVIr_Evil

---

### Post by xirochanh on 2010-12-29
> **sanco60 said:**
> "unable to locate package" i met the same problem.
and i tried the "apt-get update" 
then "apt-get install xxx" worked.
 
it seems u should update the apt-get at first.

I find the answer for my problem here, thanks, bro

---

### Post by hanishh on 2011-01-14
Thanks, this solved my problem, can anyone tell me on which screen we can configure the ethernet during installation since i could not find it during installation

---

### Post by Knatchwa on 2011-01-18
Great insight and reminded me of some of the command line options. Far as the Op mentioned, was seeing the same thing after a unetbootin install of ubuntu 10.10. 

Using dhclIent had me reconnected and once that was complete, was able to get all I needed. Also it seems any of the alternate versions found via cdimages.ubuntu.com are able to install what is needed w/o having a valid internet cinnection.

---

### Post by cvv on 2011-03-02
hi

I have the same problem, but I updated the packege repo, using *apt-get update* or *apt-get aptitude*. After updating successfully then you can install the packages.

I hope this will help you.....
cheers...
cvv

---

### Post by roeseler on 2011-04-29
> **sikander3786 said:**
> Try,

```
sudo apt-get update && sudo apt-get install ethtool
```

THANKS!! This worked for me!

---

### Post by louvonnie on 2011-08-06
I have been trying unsuccessfully for two days to install joomla 1.6.  I download all the files to my desktop as instructed on another site, and I manually pulled each file on the desktop into its own folder entitled "joomla".  

I went to the terminal and typed in :   sudo apt-get install joomla  ...and it tells me it can't find it!  I then put in sudo apt-get install desktop joomla and it tells me it still can't find it!  

Can anyone help me here?  I did download the LAMP, in preparation for installing the joomla, and I think that is installed??  I did get apache to verify "IT WORKS" on the net, but I can't seem to do the same for phpMyAdmin.....thats another one I can't seem to load or get installed.  

HELP PLEASE!! ... :) 

Belinda

---

### Post by mikelrysk on 2011-12-22
Using a pendrive of Ubuntu 11.10 (if this matters, let me know)

I have tried to use the sudo apt-get update command and then the sudo apt-get install belier.
I then tried the sudo apt-get update && sudo apt-get install belier command.

Neither worked.

here is my output from cat /etc/apt/sources.list
 
# /etc/apt/sources.list

deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

I first typed bel at the CLI, then the following appeared underneath that line
The program 'bel' is currently not installed.  You can install it by typing:
sudo apt-get install belier
You will have to enable the component called 'universe'

How do I enable 'universe'?

Does anyone have an answer to this?

---

### Post by guerau on 2012-10-26
> **mikelrysk said:**
> Using a pendrive of Ubuntu 11.10 (if this matters, let me know)

I have tried to use the sudo apt-get update command and then the sudo apt-get install belier.
I then tried the sudo apt-get update && sudo apt-get install belier command.

Neither worked.

here is my output from cat /etc/apt/sources.list
 
# /etc/apt/sources.list

deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

I first typed bel at the CLI, then the following appeared underneath that line
The program 'bel' is currently not installed.  You can install it by typing:
sudo apt-get install belier
You will have to enable the component called 'universe'

How do I enable 'universe'?

Does anyone have an answer to this?


Remove the first line pointing to the CDROM.
Add the words "universe" and "multiverse" after each deb line.

So for example:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric main restricted universe multiverse

---

