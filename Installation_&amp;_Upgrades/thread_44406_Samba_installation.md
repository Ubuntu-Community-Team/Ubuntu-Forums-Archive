---
title: "Samba installation"
date: 2005-06-26
forum: Installation &amp; Upgrades
---

### Post by Spleenie on 2005-06-26
Hello there, trying to install Samba on a Kubuntu Hoary desktop that has been updated and upgraded.

```
sudo apt-get install samba
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
  samba: Depends: samba-common (= 3.0.10-1ubuntu3) but 3.0.14a-3ubuntu3~5.04ubp1 is to be installed
E: Broken packages
``` 

As I read this, the samba installation is asking for a version of samba-common that is older than the one I have or is abailable in the repositories.

A quick look at my installed programs informs me I have samba-common 3.0.14a-3ubuntu3~5.04ubp1 installed already.

Has anyone else come across this problem or one similar to it? I tried the -f option but it reported the same problem.

Cheers, Spleenie

---

### Post by manicka on 2005-06-26
Sounds like your backports repos are out of whack. Check your settings with apt-get update, there were some problems with the servers yesterday.

---

### Post by Spleenie on 2005-06-26
[QUOTE=manicka]Sounds like your backports repos are out of whack. Check your settings with apt-get update, there were some problems with the servers yesterday.[/QUOTE]

I am using the planetmirror backports repositry.

Is there a way to get samba to install even though it wants an older version of samba-common? Or downgrade samba-common?

---

### Post by c0rderr0y on 2005-08-23
thanks for answering my question (even though i didnt ask it in this post)

---

### Post by hangon418 on 2005-08-23
have the exact same problem. no idea what to do lol all i want to do is print from my windows xp print server damnit.

if anyone knows how to fix this that would be amazing

---

