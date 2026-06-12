---
title: "From Ubuntu 6.06 to 6.10"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by Hoffmann on 2006-10-28
Hello,

I just upgraded to Ubuntu 6.10 (from Ubuntu 6.06). Everything seems to be perfect. I added extra repositories by following:

[http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

However, when I run:

wget [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg) -O- | sudo apt-key add -

I got the error:

Resolving packages.freecontrib.org... failed: Temporary failure in name resolution.
gpg: no valid OpenPGP data found.

Moreover, when I run: sudo apt-get update

I got: 

Errhttp://packages.freecontrib.org edgy-plf Release.gpg                        
  Temporary failure resolving ‘packages.freecontrib.org’
Errhttp://packages.freecontrib.org edgy-plf/free Translation-en_US             
  Temporary failure resolving ‘packages.freecontrib.org’
Errhttp://packages.freecontrib.org edgy-plf/non-free Translation-en_US         
  Temporary failure resolving ‘packages.freecontrib.org’
Fetched 6B in 8s (1B/s)                                                        
Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy-plf/Release.gpg](http://packages.freecontrib.org/plf/dists/edgy-plf/Release.gpg)  Temporary failure resolving ‘packages.freecontrib.org’
Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy-plf/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/plf/dists/edgy-plf/free/i18n/Translation-en_US.bz2)  Temporary failure resolving ‘packages.freecontrib.org’
Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy-plf/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/plf/dists/edgy-plf/non-free/i18n/Translation-en_US.bz2)  Temporary failure resolving ‘packages.freecontrib.org’
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

Could anyone, please, help me to solve this problem?

Thanks!

---

### Post by gvgerman on 2006-10-28
search forums ...

the following seems to be most prevalent:

- DDoS problems, servers are down
- easyubuntu staff resigned (and servers are down)

at any regard, there have been problems w/ freecontrib for many users for a couple days now

---

### Post by taurus on 2006-10-28
So instead of using easyubuntu, try Automatix then...

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by glotz on 2006-10-28
Sounds like a DNS error to me. Try again in a little while. If you can come up with the IP you could insert it to your HOSTS file.

---

### Post by gvgerman on 2006-10-28
[http://www.ubuntuforums.org/showthread.php?t=286176]("http://www.ubuntuforums.org/showthread.php?t=286176")
[http://www.ubuntuforums.org/showpost.php?p=1680656&postcount=225]("http://www.ubuntuforums.org/showpost.php?p=1680656&postcount=225")

[http://xname.org/]("http://xname.org/") says:
> 
XName currently DOWN

XName is temporarily closed since 08:00PM CEST Thursday 26. evening. We were experiencing the largest DDoS we ever had on both ns0 and ns1 IP addresses, forcing our upstream providers to cut off XName servers in order to preserve their other customers.

We're working hard in order to have at least one DNS server answering ASAP, and we already negociated with a premium transit provider to host one of our DNS servers shortly.

Update: Sat. 28. 12:00 - ns0 is up and running, serving all zones correctly

---

### Post by taurus on 2006-10-28
> **glotz said:**
> Sounds like a DNS error to me. Try again in a little while. If you can come up with the IP you could insert it to your HOSTS file.
I just checked and the site is down right now.  Who knows when it will come back up so if you are in a hurry and can't wait, use Automatix2 to install those extra apps then.

---

### Post by Hoffmann on 2006-10-29
I tried to install Automix2, but I got the error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package automatix2

Any hint?

Thanks!

---

### Post by taurus on 2006-10-29
Did you remember to run

```
sudo aptitude update
```
first???

---

### Post by Hoffmann on 2006-10-29
My procedure was:

(1) sudo aptitude update

(2) Acquire GPG key: 

wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -


(3)Run the following commands to install Automatix:

sudo apt-get install automatix2

And I got:

E: Couldn't find package automatix2

---

### Post by taurus on 2006-10-29
You NEED to run the update first before you install automatix2!!!

```
sudo aptitude update
sudo aptitude install automatix2
```

---

### Post by Hoffmann on 2006-10-29
By following your suggestion, now I got:

Couldn't find any package whose name or description matched "automatix2"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


Could I hear from you again?

Once again, many thanks!

---

### Post by taurus on 2006-10-29
Can you post your /etc/apt/sources.list here?

```
more /etc/apt/sources.list
```

---

### Post by Hoffmann on 2006-10-29
> **taurus said:**
> Can you post your /etc/apt/sources.list here?

```
more /etc/apt/sources.list
```

It is shown below:

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free                                               
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

---

### Post by taurus on 2006-10-29
> **Hoffmann said:**
> It is shown below:

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free                                               
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main
Hey, you forgot to add 

```
deb http://www.getautomatix.com/apt edgy main
```
to your /etc/apt/sources.list as described in here, [http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)!!!

Therefore, add that line to your /etc/apt/sources.list and run those two commands again...

```
sudo aptitude update
sudo aptitude install automatix2
```

---

### Post by Hoffmann on 2006-10-29
> **taurus said:**
> Hey, you forgot to add 

```
deb http://www.getautomatix.com/apt edgy main
```
to your /etc/apt/sources.list as described in here, [http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)!!!

Therefore, add that line to your /etc/apt/sources.list and run those two commands again...

```
sudo aptitude update
sudo aptitude install automatix2
```


Hi taurus:

I succeeded in installing Automatix now.

Thanks a lot!
:-)

---

### Post by taurus on 2006-10-29
> **Hoffmann said:**
> Hi taurus:

I succeeded in installing Automatix now.

Thanks a lot!
:-)
:cool:

---

### Post by azids on 2006-10-29
azids@azids-desktop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?
azids@azids-desktop:~$ 
azids@azids-desktop:~$ 

I get this error... is there something wrong? Am trying to install automatix. Pls help](*,)

---

