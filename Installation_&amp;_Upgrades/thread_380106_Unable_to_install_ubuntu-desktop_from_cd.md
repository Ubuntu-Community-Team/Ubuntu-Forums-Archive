---
title: "Unable to install ubuntu-desktop from cd"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by gilbertr on 2007-03-09
Hi,

I have a UBUNTU Dapper 6.06 server setup and am now trying to install the ubuntu-desktop on this system.
The issue is that I would like to get the package from the ubuntu 6.06 Desktop CD.
However, after I have apt-cdrom'd the CD to add it to the sources list, apt-get still tries to download the package, which is what I am trying to avoid.
After having removed the download URLs from the sources list but leaving the CD, running apt-get update and then 'apt-get install ubuntu-desktop', apt-get keeps on telling me : No candidate version found for ubuntu-desktop.

I have tried the same with the kubuntu desktop CD but with the same result

Can anyone help me ?

Thanks.

---

### Post by zvacet on 2007-03-09
Do you have alternate CD,cause if you don´t it means that you try to install something that is not there.In case that you have alternate Cd
```
sudo apt-cdrom add
```
```
sudo aptitude install ubuntu-desktop
```

---

### Post by gilbertr on 2007-03-13
Thanks,

I have added the alternative CD to the sources.list file, apt-get update'd.
I have tried your suggestion but get the same result as with the other CDs when perfroming the apt-get install :

<quote>
root@server: apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: python-epydoc but it is not going to be installed
                  Depends: python-gdbm but it is not going to be installed
                  Depends: python-unit but it is not going to be installed
                  Depends: smbclient but it is not going to be installed
E: Broken packages
</quote>

I feel like I am going to have to download it, which is exactly what I do not want to do.

---

### Post by gilbertr on 2007-03-13
My apologies, I just reread your reply.

I ran aptitude now instead of apt-get and ubuntu-desktop did get installed.

Which leads me to the question, what is the difference between apt-get and aptitude ?

---

### Post by zvacet on 2007-03-13
[http://www.psychocats.net/ubuntu/aptitude]("http://www.psychocats.net/ubuntu/aptitude")

---

