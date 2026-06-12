---
title: "apt-get &quot;couldn't find package&quot;"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by tr0910 on 2006-09-12
I have the following problems with installing a number of commands via apt-get.  I've successfully installed samba and rdiff-backup so simetimes it works.  What should I do next?

root@UbuntuLinux:/home/trad# apt-get install rsnapshot
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package rsnapshot

thanks.....

---

### Post by Jussi Kukkonen on 2006-09-12
rsnapshot is in universe. Try installing again after a succesful *apt-get update*. If that doesn't work post contents of /etc/apt/sources.list here please.

---

### Post by tr0910 on 2006-09-12
I had to uncomment the lines pointing to universe in the sources.list file, 

sudo gedit /etc/apt/sources.list

Then I was able to update and now apt-get works fine.

Thanks for the help.

---

### Post by tr0910 on 2006-09-12
Sorry I was too quick on the self congratulations.  SMBMOUNT still is not found even after completely opening up sources.list  (see below)


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by Jussi Kukkonen on 2006-09-12
I think you're looking for smbfs.

---

### Post by tr0910 on 2006-09-12
Thanks again, thats easy.

Is there any risk to leaving sources list wide open like I have?

---

### Post by akak8ty on 2006-09-12
Yep, ditto. I was getting a little grumpy and was trying to reinstall the whole thing, which jammed up my machine even further, it wouldn't go away, it wouldn't reload. 
I have an error on line 39 and:

Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

But not matter what I do, it won't give me permission to do this :@

---

### Post by Jussi Kukkonen on 2006-09-12
> **tr0910 said:**
> Thanks again, thats easy.

Is there any risk to leaving sources list wide open like I have?
No, not really. Enabling dapper-updates and dapper-backports does mean a slightly larger risk of breakage (changes are always risky), but that's not a big risk.
EDIT: now that I think of it, backports might be better commented out, if you don't need it... There is a possibility of not getting a security update because one has upgraded to a backported version.

Having multiverse/universe enabled doesn't increase risk at all in itself, but installing software from those repositories might be considered "more adventorous" as it's not "supported by the ubuntu team". In practice, I wouldn't worry. Adding some (non-ubuntu.com) 3rd party repositories like some people do is another matter.

akak8ty, You might want to start a new thread since your problem is clearly not the same one. Include the error message, and the output of these commands:
```
sudo cat /etc/apt/sources.list
ls -l /etc/apt/sources.list

```

---

