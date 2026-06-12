---
title: "Unable to update or upgrade ubuntu 12.04"
date: 2014-02-15
forum: Installation &amp; Upgrades
---

### Post by gennadiy-rishkin on 2014-02-15
Hello,

I cannot update ubuntu 12.04 or update to a new release. I keep getting:

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

I've tried:
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

with no success.

How can I fix the problem. Thanks.

---

### Post by Bashing-om on 2014-02-15
gennadiy-rishkin; Hi !

Give it a try like this:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

```
Giving the new index files a home to go to.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by gennadiy-rishkin on 2014-02-15
Hi Bashing-om,

At the third step: sudo apt-get update, still gives:

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

---

### Post by Bashing-om on 2014-02-15
gennadiy-rishkin; Well,

Means we will have to dig deeper.
Got chores I have to get done outside, so be a while before I can get back to this.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-02-15
gennadiy-rishkin; Hey,

Going deeper:
Insure all repository sources are enabled in "Ubuntu Software Center" ; And,
Try terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get -f install
##Then run:##
sudo dpkg --configure -a
Then run this again:
sudo apt-get -f install

sudo apt-get -u dist-upgrade

```
Worst case, I hope the package manager directs our attention.

[INDENT][INDENT]directions are nice to have
[/INDENT][/INDENT]

---

### Post by gennadiy-rishkin on 2014-02-15
Hi Bashing-om,

I'm unable to get past sudo apt-get update. I keep getting the same error:

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

I then tried starting from: 
sudo dpkg --configure -a

which gives this error:

dpkg: error: parsing file '/var/lib/dpkg/status' near line 6741:
 missing package name

---

### Post by Bashing-om on 2014-02-15
gennadiy-rishkin; Hey,

That is of some help, at least now we know where to start looking.

Fire up your favorite text editor (as in gedit ), and let's look.
```

gksudo gedit /var/lib/dpkg/status

```

Go to line 6741. and post back that complete "paragraph". Will see if we can identify the package and fix the error. 

What might be the better thing is to do the same with "/var/lib/dpkg/status-old" and compare the stanzas. Hopefully status-old will still be intact and with out that error.
We can then edit the current status file using status-old as a guide.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by gennadiy-rishkin on 2014-02-16
Hi Bashing-om,

So I copied /var/lib/dpkg/status-old over /var/lib/dpkg/status and it works fine now. I can "sudo apt-get update" and "sudo apt-get upgrade". Thanks a lot. 

However, I'm not able to upgrade from 12.04 to new release. Doing:

sudo do-release-upgrade -d    gives:

```
Could not determine the upgrade 

An unresolvable problem occurred while calculating the upgrade. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. 


Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 
=== Command detached from window (Sun Feb 16 08:32:59 2014) ===
=== Command terminated with exit status 1 (Sun Feb 16 08:32:59 2014) ===
```

---

### Post by Bashing-om on 2014-02-16
gennadiy-rishkin; Outstanding!

You do good work.

As this situation is now under control, please mark this thread solved. Aids others seeking a similar solution and as well helps keep the forum tidy. 1st post -> thread tools

Off topic: "do-release-upgrade -d" With the '-d' option it directs to upgrade to the next devel release. As 14.04 is not in release at this time the command will fail.
see:
```

man do-release-upgrade

```
As 12.10 will soon expire, I do not advocate upgrading to that release from a Long Term Support release.. Wait until 14.04 is released (April), and then version upgrade.
If you do want to go to 12.10 then "do-release-upgrade" will do it.

[INDENT][INDENT]when you are good
[INDENT][INDENT][INDENT]you are good ![/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gennadiy-rishkin on 2014-02-16
Hi Bashing-om, 

Many thanks for your help. I'll wait for the 14.04 release.

---

