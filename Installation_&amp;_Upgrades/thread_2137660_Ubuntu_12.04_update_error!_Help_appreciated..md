---
title: "Ubuntu 12.04 update error! Help appreciated."
date: 2013-04-21
forum: Installation &amp; Upgrades
---

### Post by MaynardHSH on 2013-04-21
Hey guys, I've been trying to update ubuntu in the last week and it seems that every time it tries to, it gets a few errors, the thing is that I'm not sure what the problem is, after "updating" it seems fine, but then an icon appears in the task bar like this one: (I'm not sure if this is the best way to upload a pic, srry) 
[ATTACH=CONFIG]241624[/ATTACH]

and in Terminal I get a few of these:

> Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources 404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages 404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/unity-team/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/unity-team/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/unity-team/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/unity-team/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

So, thanks for any help in advance.

---

### Post by ibjsb4 on 2013-04-21
You need to either remove or just uncheck those PPAs in your sources list.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

### Post by kevdog on 2013-04-21
I'd comment out the offending lines in the /etc/apt/sources.list file with a # in front of the offending lines.

---

### Post by MaynardHSH on 2013-05-04
Ok, thanks for the advice, I did uncheck only, as I'm not sure or at least in the Preference menu doesn't say the same, I just unchecked the ones that don't look necessary :)

---

### Post by Bashing-om on 2013-05-04
MaynardHSH; Hi !

Did you see the "bad" PPAs line in either /etc/apt/sources.list OR the directory /etc/apt/sources.list.d (terminal use)and comment out or remove;
alternately as suggested, find and uncheck those PPAs in Software Sources (GUI) ?? //only those that are generating the "404 not found" errors//
Then run the terminal codes:
```
 sudo apt-get update
sudo apt-get upgrade
``` again and see what errors are now present.

If you require additional assistance, post the output of terminal codes:
```
cat /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
```[INDENT=2]
just try'n to help

[/INDENT]

---

