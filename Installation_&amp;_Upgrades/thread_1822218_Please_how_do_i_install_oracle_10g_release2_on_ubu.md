---
title: "Please how do i install oracle 10g release2 on ubuntu 11.04"
date: 2011-08-10
forum: Installation &amp; Upgrades
---

### Post by ola4eva on 2011-08-10
Please am a new user of linux but i have basic knowledge of it.
i just installed ubuntu 11.04 which is updated version but now i want to install oracle 10g release2 on it. Please how do i go about it


Thank you for your prompt response

---

### Post by raja.genupula on 2011-08-10
man i had tried this long time ago but i hope this will works to you 
here is now an apt-get repository up on oss.oracle.com for XE. Just add:

deb [http://oss.oracle.com/debian](http://oss.oracle.com/debian) unstable main non-free

to /etc/apt/sources.list and then:

# wget [http://oss.oracle.com/el4/RPM-GPG-KEY-oracle](http://oss.oracle.com/el4/RPM-GPG-KEY-oracle)  -O- | sudo apt-key add - 
# apt-get update
# apt-get install oracle-xe

---

### Post by Mark Phelps on 2011-08-11
If you're talking about the Windows version, using Wine, you're out of luck.  It simply won't work that way.

See the link below to the WineHq site:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=7224]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=7224")

---

