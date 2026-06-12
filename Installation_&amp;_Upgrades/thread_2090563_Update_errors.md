---
title: "Update errors"
date: 2012-12-02
forum: Installation &amp; Upgrades
---

### Post by Kols on 2012-12-02
Hi, all!

I have a problem regarding updating my Lubuntu 12.04.

When I do a

sudo apt-get update

I get these errors at the bottom of the output

W: Failed to fetch [http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

I'm not sure what these are, and how to "rebuild" my repository-list with the correct adresses.

Also, I sometimes get error-messages of the same sort when I use the GUI updater.

Lastly, how do I check that I indeed have the latest version of OpenJDK? 
Output of 

sudo apt-get install openjdk-7-jre

tells me I have the latest version, but I'm not sure.

Any help would be greatly appreciated!=)

Best regards,

Ole-Jørgen

---

### Post by ibjsb4 on 2012-12-03
This PPA looks dead, last update 66 weeks ago.  Not even offered for 12o4.

[https://launchpad.net/~gnomenu-team/+archive/ppa](https://launchpad.net/~gnomenu-team/+archive/ppa)

Remove it from your software sources.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

### Post by Bucky Ball on 2012-12-03
> **Kols said:**
> 
Lastly, how do I check that I indeed have the latest version of OpenJDK? 
Output of 

sudo apt-get install openjdk-7-jre

tells me I have the latest version, but I'm not sure.



If that's what it tells you, you can be sure ... that it is the latest version available in the repositories for your release. That appears to be the latest available anyway. Look here at the instructions from their own page. That is the version they are installing:

[http://openjdk.java.net/install/](http://openjdk.java.net/install/)

What makes you unsure?

---

