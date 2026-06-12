---
title: "main/binary-i396 error on software update"
date: 2015-10-31
forum: Installation &amp; Upgrades
---

### Post by ck234 on 2015-10-31
Hello,
  I recently tried to install Skype on Ubuntu Desktop 15.04 Vivid.  In doing so I accidentally tried to add some i386 packages to a 64 bit machine.  I have now found that I cannot update (or upgrade) packages, as when I run *sudo apt-get update* I get:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/vivid/InRelease](http://archive.ubuntu.com/ubuntu/dists/vivid/InRelease)  Unable to find expected entry 'main/binary-i396/Packages' in Release file (Wrong sources.list entry or malformed file)           

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/vivid-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/vivid-updates/InRelease)  Unable to find expected entry 'main/binary-i396/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/vivid-backports/InRelease](http://archive.ubuntu.com/ubuntu/dists/vivid-backports/InRelease)  Unable to find expected entry 'main/binary-i396/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/vivid-security/InRelease](http://archive.ubuntu.com/ubuntu/dists/vivid-security/InRelease)  Unable to find expected entry 'main/binary-i396/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/vivid/main/source/Sources](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/vivid/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/vivid/main/binary-amd64/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/vivid/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/vivid/main/binary-i396/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/vivid/main/binary-i396/Packages)  404  Not Found

I have tried to purge the ppa, remove all references to skype and my */etc/apt/sources.list.d* folder is empty.

Is there a solution to this?  NB it is similar to other problems listed on the forum, but none of those solutions (listed above) seemed to work.  I suspect the solution is in correcting my spelling mistake from "i396" to "i386", or removing those packages altogether, but I am not sure how this is done.  Thanks.

---

### Post by oldos2er on 2015-10-31
Please post the contents of your sources.list: ```
cat /etc/apt/sources.list
```

---

### Post by deadflowr on 2015-10-31
Try
```
sudo dpkg --remove-architecture i396
```
then rerun the update command

---

### Post by ck234 on 2015-10-31
Thank you for your replies.  deadflowr - your solution was correct.  I had tried that, but stupidly put in i386 instead of i396!

I still got the following error:

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/vivid/main/source/Sources](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/vivid/main/source/Sources)  404  Not Found

But I deleted this ppa in */etc/apt/sources.list.d* with *sudo rm -r /etc/apt/sources.list.d/**

This fixed the final error.  But note - this will delete all files in */etc/apt/sources.list.d* directory

---

### Post by grahammechanical on 2015-10-31
We can disable a PPA from System Settings>Software & Updates>Other Software tab. That will remove those kind of errors and still let us keep the application we used the PPA to install. In your case you are getting that error because there is not an active tualatrix PPA for vivid.

[http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/)

To restore the sources.list.d file try

```
sudo apt-get update
sudo apt-get upgrade
```

Regards

---

### Post by deadflowr on 2015-10-31
> **ck234 said:**
> Thank you for your replies.  deadflowr - your solution was correct.  I had tried that, but stupidly put in i386 instead of i396!

I still got the following error:

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/vivid/main/source/Sources](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/vivid/main/source/Sources)  404  Not Found

But I deleted this ppa in */etc/apt/sources.list.d* with *sudo rm -r /etc/apt/sources.list.d/**

This fixed the final error.  But note - this will delete all files in */etc/apt/sources.list.d* directory

If you added the ppa with add-apt-repository command, you only needed to add an -r and the ppa would have been removed.
add a ppa
```
sudo add-apt-repository ppa:some-ppa
```
remove it
```
sudo add-apt-repository -r ppa:some-ppa
```

I know, monday morning quarterbacking...

---

