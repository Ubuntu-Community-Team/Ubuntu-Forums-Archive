---
title: "installing remastersys gives mkisofs dependecy problem"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by teutonicknight77 on 2008-02-02
Hi 

Am planning to create a custom version of Ubuntu 7.10 with mp3 drivers, skype, etc. I want to use remastersys. However when I run apt-get install remastersys, I get the following 
error 

 remastersys: Depends: mkisofs (>= 0.0-0) but it is not installable
E: Broken packages

Any help would be much appreciated

Teutonicknight77

---

### Post by zvacet on 2008-02-02
**system>admin>sortware sources>chek all boxes under Ubuntu software tab and under updates tab**.Reload.Under programs>accessories>terminal type

```
sudo apt-get install mkisofs
```

and after that 

```
sudo apt-get install remastersys
```

---

### Post by alexj.powell on 2008-04-25
Sorry to bring up an old thread, but I'm having the same problem.

If I do what is said above, I get the following:

```
oni@oni-org:~$ sudo apt-get install mkisofs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting genisoimage for regex ‘mkisofs’
genisoimage is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
oni@oni-org:~$ sudo apt-get install remastersys
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
  remastersys: Depends: mkisofs (>= 0.0-0)
E: Broken packages
oni@oni-org:~$ 

```

I am using 8.04 server edition with ubuntu-desktop i386

---

### Post by bryanl on 2008-04-25
what is interesting is that this problem cropped up in the beta and was fixed for a while and is now present again in the 8.04 release.

since it is a rather straightforward shell script, I'll have to see if I can install it manually and see what happens.

---

### Post by Fragadelic on 2008-04-29
This is very interesting.  I'll have to look into it.  My 8.04 ubuntu remaster worked fine including the only ubiquity boot option that I put in specifically for 8.04 and up.

I don't always check the forum here so a post on the official remastersys thread would get looked at almost immediately by me though.

---

### Post by jfrice on 2008-04-30
I was having the same issue. comment out the romeo repository an then add the remastersys one below. This worked for me with Ubuntu 8.08

# deb [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) romeo/
# Remastersys
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/

---

