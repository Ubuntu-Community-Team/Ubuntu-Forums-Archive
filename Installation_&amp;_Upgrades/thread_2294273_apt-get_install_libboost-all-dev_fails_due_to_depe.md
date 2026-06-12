---
title: "apt-get install libboost-all-dev fails due to dependencies"
date: 2015-09-10
forum: Installation &amp; Upgrades
---

### Post by Jeremy_Greene on 2015-09-10
I have installed 14.0.4 LTS a few times over the last couple of months. I have a pretty detailed recipe that I've followed each time (I think all pretty normal).
However, this morning, I got this:

```
root@zyper:/etc# apt-get install  libboost-all-dev
apt-get install  libboost-all-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libboost-all-dev : Depends: libboost-date-time-dev but it is not going to be installed
                    Depends: libboost-filesystem-dev but it is not going to be 
(total of 10 )

So, the first thing, is why this happened this time. Here are the packages I installed on a clean 14.0.4 install up to the libbost error:
apt-get install -y  emacs
apt-get install -y  gnome-tweak-tool
sudo apt-get install ifplugd
apt-get **purge** network-manager
sudo apt-get install -y  openssh-server
sudo apt-get install -y  gnome-core  ==> I used gdm display mgr
sudo apt-get install -y  vnc4server 
sudo apt-get install -y  fluxbox
sudo apt-get instal firefox
sudo apt-get install -y  apache2
sudo apt-get install -y  mysql-server  (make password zazzle!!!)
sudo apt-get install -y  php5 libapache2-mod-php5
sudo apt-get install -y php5-curl
sudo apt-get install -y php5-mysqlnd
sudo apt-get install -y  mysql*   <<<==== Skip this for starters, it may not be needed (and caused lots of errors)
sudo apt-get install -y  mysql-client libmysqlclient-dev
sudo apt-get install -y  g++
```

NOTE: I will admit that I changed the order this time to do the purge of "network-manager" before installing libboost. (Need to remove network-manager to get link-local addressing to work!!). But they sure do seem like worlds apart. 

Ok, so, then I did:

```
root@zyper:/etc# apt-get install -f
root@zyper:/etc# dpkg --configure -a
root@zyper:/etc# apt-get --fix-broken install
root@zyper:/etc# apt-get --fix-missing install
root@zyper:/etc# apt-get clean
root@zyper:/etc# apt-get autoclean
root@zyper:/etc# apt-get autoremove
root@zyper:/etc# apt-get update
root@zyper:/etc# apt-get upgrade
root@zyper:/etc# apt-get install  libboost-all-dev

```
And it still fails. I guess I can do the who install over and do the libboost install before the network manager purge. But that's painful and seems like a long shot.
Or... is this due to getting the latest updates during ubuntu install and getting something that conflicts with libboost?

---

### Post by Bashing-om on 2015-09-10
Jeremy_Greene; Hello;

Let's take a look and see if we can find out what is taking place here ....
We have available in 14.04:
```

sysop@1404mini:~$ apt-cache show libboost-all-dev
Version: 1.54.0.1ubuntu1
Filename: pool/universe/b/boost-defaults/libboost-all-dev_1.54.0.1ubuntu1_amd64.deb

sysop@1404mini:~$ apt-cache show libboost-date-time-dev
Version: 1.54.0.1ubuntu1
Filename: pool/main/b/boost-defaults/libboost-date-time-dev_1.54.0.1ubuntu1_amd64.deb

sysop@1404mini:~$ apt-cache show libboost-filesystem-dev
Version: 1.54.0.1ubuntu1
Filename: pool/main/b/boost-defaults/libboost-filesystem-dev_1.54.0.1ubuntu1_amd64.deb

```
Now let's see what is installed on your system, and what the package manager expects:
```

apt-cache policy libboost-all-dev
apt-cache policy libboost-date-time-dev
apt-cache policy ibboost-filesystem-dev

```

Once we know what we have, we can make a plan for what we want.

[INDENT][INDENT][INDENT]all in how you do it
[/INDENT][/INDENT][/INDENT]

---

### Post by Jeremy_Greene on 2015-09-10
This is getting somewhat depressing. Decided to just reinstall 14.0.4 and this time do the purge of network-manager after the install of libbost-all-dev.
So, that worked -- I installed all of the apps up to and including libpost-all-dev.
Not terribly comforting, but hey, it worked.
But then... the very next thing I did to install openssh-server. And I get *another* case of an unmet dependency. This time for openssh-client. Which, if I try to do an install for, I am informed that I have the latest sshclient. I have done all of the standard apt-get "corrective" commands as I list in my first post. (note, I have not yet done the purge of network manager).
Oh.... and I forgot to mention that after the install, my etc/shadow password file and passwd file disagreed.  Had to mess around with that too.
But boy... this is seriously shaking my confidence in linux and/or ubuntu.
Could this all be at least in part due to selecting the "get latest updates" check box during install? Or is this really the "normal" way things go?

---

### Post by Bashing-om on 2015-09-10
Jeremy_Greene; Agreed !

depressing -> aggravating .

There is a great amount of effort expended to make sure that what is in the repository is complementary in all respects .
A fault found then a bug report is submitted ( rare, I can recall none ) .

So we have a stable system up until " very next thing I did to install openssh-server ' . So that begs the question. How did you install openssh-server ? from a PPA such that a later release elevated the supporting library versions ?

As we seek to find the cause ... and if a fault .. well, we tell our developers there is a problem.


[INDENT][INDENT]gotta be a cause
[INDENT][INDENT][INDENT]gotta be a fix
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mc4man on 2015-09-10
There is no connection between libboost* & network-manager, network-manager-gnome,  so your issue there is from elsewhere.
If you are installing gnome-core then why use ubuntu-14.04 as base?

---

### Post by jeremy-spagnet on 2016-02-03
I have the same issue (actually just the same symptoms) installing libboost on an ibm softlayer ubuntu 14.04 machine.

    ```
1929  sudo apt-get install -f
    1930  sudo dpkg --configure -a
    1931  sudo apt-get clean
    1932  sudo apt-get update
    root@brain2:~/caffe# sudo apt-get install libboost-all-dev
    Reading package lists... Done 
    Building dependency tree       
    Reading state information... Done 
    Some packages could not be installed. This may mean that you have
    requested an impossible situation or if you are using the unstable
    distribution that some required packages have not yet been created
    or been moved out of Incoming.
    The following information may help to resolve the situation:
    The following packages have unmet dependencies:
     libboost-all-dev : Depends: libboost-tools-dev

```
... and about ten more. 
using my powers of reading comprehension I tried 
```

root@brain2:~/caffe# apt-get install  libboost-tools-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libboost-tools-dev : Depends: libboost1.54-tools-dev but it is not installable
E: Unable to correct problems, you have held broken packages.

```
apt-get -f install didn't help matters .
in case it sheds light i tried the following:
```

root@brain2:~/caffe# apt-cache policy libboost-all-dev
libboost-all-dev:
  Installed: (none)
  Candidate: 1.54.0.1ubuntu1
  Version table:
     1.54.0.1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages

```

based on the info from apt-get info command I tried downloading  libboost-all-dev_1.54.0.1ubuntu1_amd64.deb ( wget [http://archive.ubuntu.com/ubuntu/pool/universe/b/boost-defaults/libboost-all-dev_1.54.0.1ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/b/boost-defaults/libboost-all-dev_1.54.0.1ubuntu1_amd64.deb)) and doing 

dpkg -i libboost-all-dev_1.54.0.1ubuntu1_amd64.deb 
Selecting previously unselected package libboost-all-dev.
(Reading database ... 128528 files and directories currently installed.)
Preparing to unpack libboost-all-dev_1.54.0.1ubuntu1_amd64.deb ...
Unpacking libboost-all-dev (1.54.0.1ubuntu1) ...
dpkg: dependency problems prevent configuration of libboost-all-dev:
 libboost-all-dev depends on libboost-tools-dev; however...

Perhaps there is a chain of dependency where A needs B, B needs C, C needs A this being the 'impossible situation' the system reports.
in any case any help would be appreciated

---

### Post by jeremy-spagnet on 2016-02-03
update - I edited /etc/apt/sources.list and added restricted and main .
Then did apt-get update, upgrade.   
then sudo apt-get install apt-file software-properties-common 
since these were apparently missing from this ibm softlayer machine.
now libboost-dev installs but libboost-all-dev still has unmet dependencies as above

---

### Post by Bashing-om on 2016-02-03
jeremy-spagnet; Well, well ..

Let's see what we can find out :
As we have this advisory:
> 
Depends: libboost1.54-tools-dev but it is not installable

```

apt-cache show libboost1.54-tools-dev 
apt-cache policy ibboost1.54-tools-dev
apt-cache depends ibboost1.54-tools-dev

```
See if we can find out why the system will not install it.

[INDENT][INDENT]system will not give us the rope
[INDENT][INDENT][INDENT]to hang ourselves with ??
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jeremy-spagnet on 2016-02-04
thanks for you offer of help
in the meantime i traced it back to /etc/apt/sources.list which for some reason had the ubuntu 12 name (silent snail or whatever it is) instead of the ubuntu14 name (trusty telomere) and only a single line . So I copied a fresh version from the ubuntu site and I also added 'main' and 'restricted'  to the list of repos in the first source . not sure if that is entirely recommended but my problems have vanished.

---

### Post by Bashing-om on 2016-02-05
jeremy-spagnet; Yep;

You done good . An invalid fetch request would sure do that.
As this matter is now concluded:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

### Post by jeremy-spagnet on 2016-02-08
ok I would mark as solved but I don't have the power to do so under 'thread tools' , I suppose since I'm not the thread initiator (different jeremy as it happens)
btw what is an invalid fetch request - and did you mean that such an invalid fetch request would overwrite /etc/apt/sources.list ?

---

### Post by Bashing-om on 2016-02-08
jeremy-spagnet; OK ...

My bad :
> 
I suppose since I'm not the thread initiator (different jeremy as it happens)

in not perceiving that "you" are not the Original Poster. Slow down and look Bashing -om.

As to my phraseology of the term "fetch";
well, as you know the database updates are controlled by the package management system. The file " /etc/apt/sources.list " and for 3rd party packages the files in the directory " /etc/apt/sources.list.d" control where to find these updates. If one of these sources as in error .. then I call that request a bad 'fetch' . when the system attempts to comply as directed and can not .

> 
and did you mean that such an invalid fetch request would overwrite /etc/apt/sources.list

so, no - not going to overwrite anything, the system will try to comply as directed, but if the path does not exist, or the files at that distant end do not exist .. then the update process for the package will fail. In this case the system will scream and holler and tell you that it can not comply . Nothing else will happen.

[INDENT][INDENT]understanding is a good thing
[/INDENT][/INDENT]

---

