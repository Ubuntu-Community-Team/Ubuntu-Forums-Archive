---
title: "dpkg process_queue: Assertion 'dependtry &lt;= 4' failed."
date: 2006-08-07
forum: Installation &amp; Upgrades
---

### Post by dans0n on 2006-08-07
Full error is:

> 
root@ubuntu:dpkg --configure -a

dpkg: ../../src/packages.c:191: process_queue: Assertion 'dependtry <=4' failed.
Aborted


Happens every time i run the dpkg --configure -a command and I'm always told to run that command before running dpkg or synaptic.

However I only seem to need to run it once per session. Synaptic starts without error afterwards. 

I'm still not sure if all is healthy though!

Daniel

---

### Post by mlind on 2006-08-07
> **dans0n said:**
> 
Happens every time i run the dpkg --configure -a command and I'm always told to run that command before running dpkg or synaptic.

However I only seem to need to run it once per session. Synaptic starts without error afterwards. 

I'm still not sure if all is healthy though!

Daniel

It doesn't look healthy to me.. I think you should report a bug about this to Ubuntu [launchpad]("https://launchpad.net/distros/ubuntu/+source/dpkg/+bugs").

Any ideas when this started to happen?

---

### Post by dans0n on 2006-08-08
Bug reported:
[https://launchpad.net/distros/ubuntu/+source/dpkg/+bug/55641](https://launchpad.net/distros/ubuntu/+source/dpkg/+bug/55641)

---

### Post by A2A on 2006-08-08
Hi, i'm using Xubuntu 6.06 on my laptop.  I get the following errors when I try to run synaptic.  
It says something about dpkg failed and asks me to run "dpkg --configure -a".
Once I run that command in terminal, Synaptic works just fine.  

I think this started happening after I did 2 things.
1. I went to Applications -> System -> Software Properties -> Selected the "Internet" Tab and put a check mark in "Check For Updates Automatically : Daily"
2. I ran Update Manager after my first install, and it got a bunch of updated and installed them.  

Since then I have changed the settings I mentioned in point 1 (above) but it still asks me to run "dpkg --configure -a"  once a session, everytime I log in to Xubuntu.

Please advise :-)

A2A

---

### Post by A2A on 2006-08-08
UPDATE:
I rebooted using my old kernel  2.6.15-23-386 (This was the one prior to the update of my system) and both Synaptec and Update Manager worked fine.  So I thought it must be something to do with the new kernel ( 2.6.15-26-386).  So I logged off and rebooted into the  2.6.15-26-386 kernel and tried out Synaptec and Update Manager.  This time BOTH worked and it did not ask me to execute any commands (dpkg --configure -a) like it was doing a few times before!
I don't know if it was a fluke of what caused it to go whack and then fix itself.  Will post again if it happens.

Regards,

A2A

---

### Post by dleuen on 2006-08-28
I've just started getting this same error (process_queue: Assertion 'dependtry <= 4' failed). I see the bug you filed is still open. But I'd like to have a definitive answer on how to repair my system. Unlike the case mentioned above, I didn't get this error by switchink kernel packages. Anoyone have any idea on how to repair this problem until a proper fix is issued by the devs?

Don

Update: following the instructions here:

[http://techxplorer.wordpress.com/2006/05/21/resolving-an-odd-dpkg-error-in-ubuntu/](http://techxplorer.wordpress.com/2006/05/21/resolving-an-odd-dpkg-error-in-ubuntu/)

repaired the problem.

---

### Post by sycamore on 2006-10-26
listing the installed packages via the "dpkg -l" command (as per the previous post) helped me out.

---

### Post by germania on 2007-05-03
> **sycamore said:**
> listing the installed packages via the "dpkg -l" command (as per the previous post) helped me out.

If you have a normal linux desktop with a ton of packages install, the command you will want is:

```

dpkg -l | grep -v ^ii

```

which should list broken packages.  If you then use

```

dpkg --purge remove *those packages listed before*

```

it should fix what's going on.  You may have to reinstall those broken packages you removed after.

---

### Post by plugwash on 2008-07-13
you probablly want to exclude packages that have been cleanly removed too

dpkg -l | grep -v ^ii | grep -V ^rc

for the actual removals the easiest way is probablly to remove the packages with dpkg --purge --force-depends <package name> and then use apt-get -f install

---

