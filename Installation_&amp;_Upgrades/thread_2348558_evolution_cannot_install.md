---
title: "evolution cannot install"
date: 2017-01-04
forum: Installation &amp; Upgrades
---

### Post by deh6 on 2017-01-04
I cannot get evolution to install and I need some guidance.  Here is a *brief* review of the last couple of days--

1)  Update from 12.04 LTS to 14.04 LTS

2)  evolution would not start from the desktop icon.  Trying from the command line it showed it was missing a routine with a name something like ?????cuuc???so.

3)  Try some online posts on how to correct the problem.  Number of errors now increased.

4)  Try removing evolution and reinstalling.  

The current status--

```
deh@dehmain:~/Downloads$ sudo apt-get install evolution
[sudo] password for deh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 evolution : Depends: libecal-1.2-18 but it is not going to be installed
             Depends: libedataserver-1.2-20 (>= 3.13.1) but it is not going to be installed
             Depends: libevolution (= 3.16.0-fta1~utopic) but 3.10.4-0ubuntu2 is to be installed
             Depends: evolution-data-server (>= 3.16.0) but 3.10.4-0ubuntu1.5 is to be installed
             Recommends: evolution-plugins but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
deh@dehmain:~/Downloads$ 
```

In step 3 above I remember adding some 'ppa's.  Upon further investigation I think the above "Depends" are saying that several repositories are offering up a different version.  I need some guidance as what to do next.

---

### Post by QIII on 2017-01-04
Hello!

It would be helpful to know some of the "tried some online posts" you might have done.

We can't very well guess the state of your machine without such.

Would you please post the output of 

```
apt-cache policy | grep http | awk '{print $2 $3}' | sort -u 
```

between code tags.  That should give us a list of your repos and ppas.

---

### Post by deh6 on 2017-01-05
Thanks for the reply.  

I don't remember all the details of what I tried.

> deh@dehmain:~$ apt-cache policy | grep http | awk '{print $2 $3}' | sort -u
[http://archive.canonical.com/trusty/partner](http://archive.canonical.com/trusty/partner)
[http://extras.ubuntu.com/ubuntu/trusty/main](http://extras.ubuntu.com/ubuntu/trusty/main)
[http://ppa.launchpad.net/fta/gnome3/ubuntu/trusty/main](http://ppa.launchpad.net/fta/gnome3/ubuntu/trusty/main)
[http://ppa.launchpad.net/fta/gnome3/ubuntu/utopic/main](http://ppa.launchpad.net/fta/gnome3/ubuntu/utopic/main)
[http://ppa.launchpad.net/openscad/releases/ubuntu/trusty/main](http://ppa.launchpad.net/openscad/releases/ubuntu/trusty/main)
[http://security.ubuntu.com/ubuntu/trusty-security/main](http://security.ubuntu.com/ubuntu/trusty-security/main)
[http://security.ubuntu.com/ubuntu/trusty-security/multiverse](http://security.ubuntu.com/ubuntu/trusty-security/multiverse)
[http://security.ubuntu.com/ubuntu/trusty-security/restricted](http://security.ubuntu.com/ubuntu/trusty-security/restricted)
[http://security.ubuntu.com/ubuntu/trusty-security/universe](http://security.ubuntu.com/ubuntu/trusty-security/universe)
[http://us.archive.ubuntu.com/ubuntu/trusty-backports/main](http://us.archive.ubuntu.com/ubuntu/trusty-backports/main)
[http://us.archive.ubuntu.com/ubuntu/trusty-backports/multiverse](http://us.archive.ubuntu.com/ubuntu/trusty-backports/multiverse)
[http://us.archive.ubuntu.com/ubuntu/trusty-backports/restricted](http://us.archive.ubuntu.com/ubuntu/trusty-backports/restricted)
[http://us.archive.ubuntu.com/ubuntu/trusty-backports/universe](http://us.archive.ubuntu.com/ubuntu/trusty-backports/universe)
[http://us.archive.ubuntu.com/ubuntu/trusty/main](http://us.archive.ubuntu.com/ubuntu/trusty/main)
[http://us.archive.ubuntu.com/ubuntu/trusty/multiverse](http://us.archive.ubuntu.com/ubuntu/trusty/multiverse)
[http://us.archive.ubuntu.com/ubuntu/trusty/restricted](http://us.archive.ubuntu.com/ubuntu/trusty/restricted)
[http://us.archive.ubuntu.com/ubuntu/trusty/universe](http://us.archive.ubuntu.com/ubuntu/trusty/universe)
[http://us.archive.ubuntu.com/ubuntu/trusty-updates/main](http://us.archive.ubuntu.com/ubuntu/trusty-updates/main)
[http://us.archive.ubuntu.com/ubuntu/trusty-updates/multiverse](http://us.archive.ubuntu.com/ubuntu/trusty-updates/multiverse)
[http://us.archive.ubuntu.com/ubuntu/trusty-updates/restricted](http://us.archive.ubuntu.com/ubuntu/trusty-updates/restricted)
[http://us.archive.ubuntu.com/ubuntu/trusty-updates/universe](http://us.archive.ubuntu.com/ubuntu/trusty-updates/universe)
deh@dehmain:~$ 


---

