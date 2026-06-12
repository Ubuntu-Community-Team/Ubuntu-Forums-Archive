---
title: "Subversion on Kubuntu"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by rdnublx on 2011-12-13
The objective of my project is to install Subversion on Kubuntu (10.04 64-bit) locally for evaluation. My understanding is that I need client only installation, no server is needed in this case. Please comment here if my understanding is incorrect.

The Apache Subversion site points me to [Ubuntu Packages page]("http://packages.ubuntu.com/search?keywords=subversion&exact=1") 

Questions:
1. What specific package(s) should I get from this site for Kubuntu 10.04 64-bit system?
2. What are the installation / initial setup instructions?
3. Is version 1.7 available on Kubuntu? According to the SVN site it's been released already.

Thank you

---

### Post by oldos2er on 2011-12-13
Can't you just run ```
sudo apt-get install subversion
``` ?

---

### Post by rdnublx on 2011-12-13
Of course I could, if I only knew :D

My Linux experience is fragmented. For example, I am not familiar with Debian packages at all, and I guess that's how Ubuntu handles these types of installations. I don't mind reading as I prefer systematic, non-fragmented knowledge, just need some pointers and time to navigate here.

Where can I read a complete description on package installation on Ubuntu, not using GUI? GUI is nice, but it does not fit with my objective for using Linux.

Thank you

---

### Post by rdnublx on 2011-12-13
Sorry P.S.

I guess my Q.1 is not answered.

Are you saying that when apt-get is run the system determines and extracts and appropriate package from the Ubuntu server? Thus I don't need to worry about what package to get?

Thank you

---

### Post by oldos2er on 2011-12-13
All you need to know is the name of the package you want to install, apt-get (or aptitude, if you prefer) will handle installing any dependencies.

**man apt-get** will show you a lot of documentation. 

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by rdnublx on 2011-12-14
Thank you

---

### Post by oldos2er on 2011-12-14
You're welcome.

---

### Post by sheijmann on 2012-02-16
KDESVN is a nice client...

It still crashes sometimes but if you handle it gently it works perfectly...

---

