---
title: "[SOLVED] There was an error committing changes"
date: 2008-03-28
forum: Installation &amp; Upgrades
---

### Post by Monkeybells on 2008-03-28
Hi,

I can't seem to install Kaffeine or Amarok on a day old Feisty to Gutsy upgraded Kubuntu system.

I've read many forum posts with similar issues and whilst many have be helpful I still have a few problems.

Originally the problem was a stalled upgrade from Feisty to Gutsy. I managed to push the upgrade through using commands in console mode. Then once Gutsy was up and running I experienced an adept updater that announced but wouldn't update Kaffeine and several other packages. I made the announcement disappear with 'sudo /etc/init.d/acpid stop sudo dpkg --configure acpid sudo dpkg --configure -a' and and then by doing a series of 'sudo aptitude full-upgrade'.

Now Gutsy seems to be running pretty well yet I have no Amarok or Kaffeine and whenever I try to install them it says BREAK (install), which if ignored and changes are applied brings the message "There was an error committing changes. Possible reasons include problems downloading some of the packages or that the commit would break other packages.".

I've noticed often that more often than not "Could you please post your sources.list?" is one of the first questions asked of someone in my predicament, so here's me jumping the gun a little:

```
guy@Guy-desktop:~$ cat /etc/apt/sources.list
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy multiverse

deb [http://debian.cn99.com/ubuntu](http://debian.cn99.com/ubuntu) gutsy-backports main

```

I'm grateful for any help received.

---

### Post by PmDematagoda on 2008-03-28
Did you try running:-
```
sudo apt-get install -f
```
and
```
sudo dpkg --configure -a
```
before trying to install Amarok or Kaffeine?

---

### Post by Monkeybells on 2008-03-28
Tried both of those:
```
guy@Guy-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
guy@Guy-desktop:~$ sudo dpkg --configure -a
guy@Guy-desktop:~$                      
```

Then tried:
```
guy@Guy-desktop:~$ sudo apt-get install kaffeine
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  kaffeine: Depends: libxine1 (>= 1.1.8) but it is not going to be installed
E: Broken packages
guy@Guy-desktop:~$        
```

---

### Post by PmDematagoda on 2008-03-28
Please try and install the dependency manually if you can:-
```
sudo apt-get install libxine1
```

Post any errors you receive in trying to install it.

---

### Post by Monkeybells on 2008-03-28
Tried that, got this:
```

guy@Guy-desktop:~$ sudo apt-get install libxine1
[sudo] password for guy:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libxine1: Depends: libxine1-console (= 1.1.10-1~gutsy1) but it is not going to be installed
E: Broken packages
guy@Guy-desktop:~$      
```

---

### Post by PmDematagoda on 2008-03-28
Did you try running:-
```
sudo dpkg --configure -a
```
if so, please post any errors you got.

---

### Post by Monkeybells on 2008-03-28
Yes, got this:

```
guy@Guy-desktop:~$ sudo dpkg --configure -a
[sudo] password for guy:
guy@Guy-desktop:~$           
```

---

### Post by PmDematagoda on 2008-03-28
This looks very strange, can you please check in Software Sources to see if all the repositories in the Ubuntu Software tab are selected except for the CD-ROM.

If they are all selected please run:-
```
sudo apt-get update
```

---

### Post by Monkeybells on 2008-03-28
I looked in the  Software Sources and found only one source and it is selected, here it is:
[http://debian.cn99.com/ubuntu](http://debian.cn99.com/ubuntu) gutsy-backports main

I really appreciate you time and patience.

And this was the result of my subsequent apt-get update:

g```
uy@Guy-desktop:~$ sudo apt-get update
Get: 1 http://debian.cn99.com gutsy-backports Release.gpg [191B]
Ign http://debian.cn99.com gutsy-backports/main Translation-en_GB
Hit http://debian.cn99.com gutsy-backports Release
Hit http://debian.cn99.com gutsy-backports/main Packages
Get: 2 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_GB
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_GB
Get: 3 http://archive.ubuntu.com gutsy Release.gpg [191B]
Hit http://archive.ubuntu.com gutsy/main Translation-en_GB
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_GB
Hit http://security.ubuntu.com gutsy-security Release
Hit http://archive.ubuntu.com gutsy/restricted Translation-en_GB
Hit http://archive.ubuntu.com gutsy/universe Translation-en_GB
Hit http://archive.ubuntu.com gutsy/multiverse Translation-en_GB
Get: 4 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_GB
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-en_GB
Hit http://security.ubuntu.com gutsy-security/main Packages
Hit http://archive.ubuntu.com gutsy Release
Hit http://archive.ubuntu.com gutsy-updates Release
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://archive.ubuntu.com gutsy/main Packages
Hit http://archive.ubuntu.com gutsy/restricted Packages
Hit http://archive.ubuntu.com gutsy/main Sources
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://archive.ubuntu.com gutsy/restricted Sources
Hit http://archive.ubuntu.com gutsy/universe Packages
Hit http://archive.ubuntu.com gutsy/universe Sources
Hit http://archive.ubuntu.com gutsy/multiverse Packages
Hit http://archive.ubuntu.com gutsy/multiverse Sources
Hit http://archive.ubuntu.com gutsy-updates/main Packages
Hit http://archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://archive.ubuntu.com gutsy-updates/main Sources
Hit http://archive.ubuntu.com gutsy-updates/restricted Sources
Fetched 4B in 2s (2B/s)
Reading package lists... Done
guy@Guy-desktop:~$
```

---

### Post by PmDematagoda on 2008-03-28
> **Monkeybells said:**
> I looked in the  Software Sources and found only one source and it is selected, here it is:
[http://debian.cn99.com/ubuntu](http://debian.cn99.com/ubuntu) gutsy-backports main


I am sorry, but I don't really follow you, could you please post a screenshot of the Ubuntu Software tab in Software Sources.

---

### Post by Monkeybells on 2008-03-28
I'm sorry I am running Kubuntu. I'm went to Adept Manager, Manage Repositories and copied what was under the tab Third-Party Software into my last message.

Could you please tell me where to look? If you give me a hint at what I should find that might help me get there too.

Many thanks.

---

### Post by PmDematagoda on 2008-03-28
It isn't Third-Part Software, look in something like the Kubuntu Software tab(I am not sure if it even exists).

About the repository in question, I think it is best if you disable that temporarily along with other third-party repositories until this problem is solved.

---

### Post by Monkeybells on 2008-03-28
OK, I've disabled the Third-Party Software.
Attached is a screenshot of Kubuntu Software window.

---

### Post by PmDematagoda on 2008-03-28
Well, it looks all right.

For a last ditch attempt, run:-
```
sudo apt-get update
```
and try installing Kaffeine again.

This problem is really perplexing and unfortunately if the last ditch attempt does not work then you may have to do a clean install of Kubuntu, but you may wait for someone else to come around and give you a solution.

---

### Post by Monkeybells on 2008-03-28
EURIKA (sp?)!!!

I changed the setting for where to "Download from:" to 'Server for the United Kingdom' from 'Main' and have been able to install Kaffeine and Amarok with ease.

Thanks for your help getting me to use my head. Some vague memory of doing something similar in the past, changing the server, was what did it.

Many thanks again.

---

