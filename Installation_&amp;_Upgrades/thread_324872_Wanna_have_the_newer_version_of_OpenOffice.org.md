---
title: "Wanna have the newer version of OpenOffice.org?"
date: 2006-12-24
forum: Installation &amp; Upgrades
---

### Post by towsonu2003 on 2006-12-24
For those who would like to install OOo 2.1 (or any newer release), this link / tutorial is very helpful:
[http://www.oooforum.org/forum/viewtopic.phtml?t=26173&highlight=](http://www.oooforum.org/forum/viewtopic.phtml?t=26173&highlight=)
I use **procedure #3** to install as root system-wide (without installing **any** debs). it needs a bit of tweaking (all openoffice) shortcuts, but it's worth the effort... 

You might also want to tell the developers that you would prefer the installer format changed:
[http://www.openoffice.org/issues/show_bug.cgi?id=72921](http://www.openoffice.org/issues/show_bug.cgi?id=72921)

OOo is currently being distributed as RPM packages. The above installation technique allows for local, non-root installation without touching dpkg / apt / your system.

---

### Post by 5-HT on 2006-12-24
Thanks!

---

### Post by saygin on 2006-12-27
Thanks for the topic. First I must say, I am totally newbie! I read the information in the first link but, i couldn't understand what exactly I should do. 
********
Procedure: installing system-wide as root #2
To convert from .RPM to your native package format, try alien or rpm2tgz. 
********
I have changed the RPMs to DEBs by using alien. But I still don't know what should I do.  I have lots of DEBs now and I don't know which one should I open first. Does it matter? or should I open all of them one by one? 
And when I open one, it says 
"An older version is available in a software channel

Generally you are recommended to install the version from the software channel, since it is usually better supported."

What should I do? should I remove it via synaptic and install all DEBs one by one? or should I wait till ubuntu upgrades it itself? please help...

---

### Post by towsonu2003 on 2006-12-27
> **saygin said:**
> Thanks for the topic. First I must say, I am totally newbie! I read the information in the first link but, i couldn't understand what exactly I should do. 
********
Procedure: installing system-wide as root #2
To convert from .RPM to your native package format, try alien or rpm2tgz. 
********
I have changed the RPMs to DEBs by using alien. But I still don't know what should I do.  I have lots of DEBs now and I don't know which one should I open first. Does it matter? or should I open all of them one by one? 
And when I open one, it says 
"An older version is available in a software channel

Generally you are recommended to install the version from the software channel, since it is usually better supported."

What should I do? should I remove it via synaptic and install all DEBs one by one? or should I wait till ubuntu upgrades it itself? please help...

sorry, I never used debs to install OOo. I always use procedure #3 (without installing any debs). It's cleaner, doesn't touch apt, but requires a bit of effort...

---

### Post by frrobert on 2006-12-28
I like the idea will have to try it tonight.  
One question what about the existing installation of open office?  Does it need to be removed first before you install a new version?

---

### Post by Hagar Delest on 2006-12-28
Personaly, I've always followed this process without any problem :

- Download the RPMs from OOo site.
- Remove the OOo version installed by default in Ubuntu out of the box if still installed (all green packages with 'openoffice.org2 in Synaptic). No need if you've already upgraded once before.
- Then in the console :
```
cd rep_install_OOo/RPMS
sudo alien -d *.rpm
```
Sometimes, there is a warning from *alien* that says it encountered errors with scripts. If so, you have to run again *alien* on this very package with the *--scripts* option :
```
sudo alien -d openoffice.org-coreXX_2.0.4-6_i386.deb --scripts (XX is the RPM concerned)
sudo dpkg -i *.deb
```
- Then update the Gnome menu:
```
cd desktop-integration
sudo dpkg -i openoffice.org-debian-menus_2.0.4-2_all.deb
```
NB: if alien is not installed, then:
```
sudo apt-get install alien
```

---

### Post by towsonu2003 on 2006-12-28
> **frrobert said:**
> 
One question what about the existing installation of open office?  Does it need to be removed first before you install a new version?
Using *procedure #3* (without installing **any** debs), no, you don't touch your own openoffice or apt... for instance:
```

~$ ls /opt/
openoffice-**2.1**  openoffice-**2.0.4**

~$ apt-cache policy openoffice.org
openoffice.org:
  Installed: **2.0.2**-2ubuntu12.1
  Candidate: 2.0.2-2ubuntu12.1
  Version table:
 *** 2.0.2-2ubuntu12.1 0
        500 http://security.ubuntu.com dapper-security/main Packages
        100 /var/lib/dpkg/status
     2.0.2-2ubuntu12 0
        500 http://archive.ubuntu.com dapper/main Packages

```

as you see, apt doesn't know about the later versions I installed (2.1 and 2.0.4). 

once you install (or, to better articulate, copy the uncompressed archive to its place), you go there and launch it via the terminal: 
```

~$ cd /opt/openoffice-[b]2.1[b]/programs/
./soffice -writer

```

---

### Post by frrobert on 2006-12-29
I used the method towsonu2003 recommended and it worked fine.  
You do have to create menu items but it was not that big of a deal.  
What was great about it, since it doesn't effect the old version of openoffice you don't have to worry about breaking anything in ubuntu

---

