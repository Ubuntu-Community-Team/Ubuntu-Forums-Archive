---
title: "Cannot Clear Package Manager Error"
date: 2006-10-17
forum: Installation &amp; Upgrades
---

### Post by spincycle on 2006-10-17
I am a complete newbie.  Installed 6.0.6, plus all the updates.  Things went fine.  Poked around and decided to see about getting my printer working - Brother MFC8840d.  This led to a link from the forum to a file:
mfc8840dlpr-1.1.2-1.i386.deb

I tried to install it using Package Manager (so far, everything is done at the graphical level). It generaged some errors (e.g. /etc/init.d/lpd - No such file or directory, etc. , exit error 127).

So, I have since learned that I need to do other stuff (CUPS, etc.) to install a printer driver.  Here is the very simple question: How can I clear the system error?

The orange star icon in the upper right of the screen gives a rollover message to "please run Package Manager...package mfc8840dlpr needs to be reinstalled, but I can't find the archive for it".

I have run the Package Manager several times, to no avail.
I then ran apt-get and tried various commands such as remove and clean, and tried them with various options -f -m, all to no avail.  I ran them as sudo.

At this point, I don't care about re-installing the driver or installing the driver.  I just want to clear the error, as it precludes me from installing any other applications.

The help file for Synaptic Package Manager states, under Known Bugs, to try: apt-get install -f
which I did -- again to no avail.  I ran it as sudo, and got:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?


PLEASE HELP!
 
Thanks,

Jim   ](*,)

---

### Post by bsussman on 2006-10-17
> **spincycle said:**
> 

The help file for Synaptic Package Manager states, under Known Bugs, to try: apt-get install -f
which I did -- again to no avail.  I ran it as sudo, and got:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?


I bet you still had yer synaptic window open.  Only one instance of apt-get can have the lock so you need to close the graphical one prior to trying the apt-get at the command line.

---

### Post by spincycle on 2006-10-17
You are correct, but that was the second time I ran it and forgot to close synaptic package manager.  When I run it with just the terminal open, I get:

[INDENT]jsowers@gandhi2:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree... Done
E: The package mfc8840dlpr needs to be reinstalled, but I can't find an archive for it.
jsowers@gandhi2:~$[/INDENT]

jim

---

### Post by bsussman on 2006-10-18
OK - since you want it gone, try: > apt-get remove mfc8840dlpr    I am reluctant to recomment forcing options since I cannot see what is going on and it is not my system that could become inoperable. Especially since I do not know what broke it.

---

### Post by 9a3eedi on 2007-04-10
Well.. the problem here is that sometimes Synaptic or Adept crashes while downloading or installing something.. So you kill it, but the dpkg lock is still not cleared. So while you are not running synaptic or any dpkg application, the lock is still there.

I had this problem several times, especially when I try to download something using adept_manager... but then it gives me a license agreement thing, and it's impossible to press ok, so I have no choice but to kill it. I remember seeing the solution to this problem several times. 

It's by issuing some command in the terminal.. dpkg clear or something.

I always forget to bookmark such reference sites... so I have to do my research once again.. and will be back with you once I'm done..

---

### Post by 9a3eedi on 2007-04-10
From this page

[http://www.ubuntux.org/synaptic-sudden-reboot-exclusive-lock-problem](http://www.ubuntux.org/synaptic-sudden-reboot-exclusive-lock-problem)


```


sudo rm /var/lib/dpkg/lock 
sudo rm /var/cache/apt/archives/lock
sudo dpkg --configure -a


```

This should remove any locks that the dpkg thing has made.

Well.. it works for me :D

---

