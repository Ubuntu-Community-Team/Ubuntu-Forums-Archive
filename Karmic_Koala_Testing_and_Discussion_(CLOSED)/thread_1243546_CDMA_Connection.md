---
title: "CDMA Connection"
date: 2009-08-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Michaelg14 on 2009-08-18
Has anyone gotten CDMA to connect with a Verizon USB broadband modem?  Mine is stuck trying to get an IP address and never gets one.  This is in Karmic it works fine in Jaunty.

---

### Post by tekstr1der on 2009-08-18
Already a thread about this:

[http://ubuntuforums.org/showthread.php?t=1234128](http://ubuntuforums.org/showthread.php?t=1234128)

---

### Post by GeorgeVita on 2009-08-18
Hi **Michaelg14**, you are probably trying using network manager which has a 'bug' at this time (some days actually). If you need this connection with karmic you can use 'alternative' methods such as wvdial, pppconfig, etc

Please read thread regarding the bug:
[http://ubuntuforums.org/showthread.php?t=1234128](http://ubuntuforums.org/showthread.php?t=1234128)

Another way is to install previous version of nm, I am using wvdial and 'direct' pppd methods.

Regards,
George

P.S. Hi **tekstr1der**, still waiting for the solving actions!

---

### Post by Michaelg14 on 2009-08-18
Thank you, I will try that when I get home.

---

### Post by JK3mp on 2009-08-18
I too recommend wvdial extremely easy, Sprint has a guide on setting up theres with it, not sure if verizon does.

---

### Post by Michaelg14 on 2009-08-18
I attempted to install wvdial using synaptic and it hung 'setting up wvdial'.  now I can't do anything with any package manager because none can get a lock on /var/lib/dpkg/.

any ideas short of a total reinstall?

---

### Post by GeorgeVita on 2009-08-18
Hi again,
as ubuntu 9.04 has no wvdial by default, to install it you need an internet connection (ethernet/wifi) or all 5 .deb packages including dependencies for an 'offline' installation.

Where did your PC stucked? What where your actions? how are you connected now (dual boot or internet other than CDMA)?

George

---

### Post by Michaelg14 on 2009-08-18
I have a wireless connection I can use. I am attempting to do this in 9.10 and it hung while Synaptic was trying to configure wvdial as part of the install process. Did sudo dpkg --configure -a still hung.

---

### Post by GeorgeVita on 2009-08-18
For wvdial only you can check 1st remove it (just in case of bad?) and reinstall it from terminal:
```
sudo apt-get purge wvdial
```
```
sudo apt-get install wvdial
```

G

P.S. rebooting also with 9.10 to check in parallel

---

### Post by Michaelg14 on 2009-08-18
greybeard@greybeard-desktop:~$ sudo apt-get purge wvdial
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
greybeard@greybeard-desktop:~$

---

### Post by GeorgeVita on 2009-08-18
! this never happened to me, can you read:
[http://ubuntuforums.org/showthread.php?t=1230903&highlight=Resource+temporarily+unavailable](http://ubuntuforums.org/showthread.php?t=1230903&highlight=Resource+temporarily+unavailable)

I am searching also.

fuser -v /var/cache/debconf/config.dat
for your purpose: fuser -v /var/lib/dpkg/   ???

---

### Post by Michaelg14 on 2009-08-18
Tried both, nothing works.  I will probably reinstall 9.10.  I have the latest daily build.  Thanks for all your help.  When I get it back in I will try wvdial again.

---

### Post by GeorgeVita on 2009-08-18
> **Michaelg14 said:**
> ...
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I think that rebooting should stop or finishing it. Otherwise from terminal: ```
ps -A
``` will list all processes. Scroll to see all of them and write down the numbers for a running "update..." or "Synaptic" or "apt-...".

Using ```
ps -A | grep -i update
``` you can see the one that  matches. Replace "update" with "Synaptic" or "apt-"

Then you can stop this process with ```
sudo kill 1234
``` where 1234 is the number at the specific line and try again with a new Synaptic or apt-get.

Also try ```
sudo dpkg --audit
```
From **man dpkg**>  --audit
              Searches for packages that have been installed only partially on
              your  system. dpkg will suggest what to do with them to get them
              working.

As this moves from modem to upgrade issue, I am running out of 'knowledge'! Think about making a new thread to solve the "/var/lib/dpkg/ locked" or "cannot resume broken package installation" ?

G

---

### Post by Michaelg14 on 2009-08-18
That is extremely helpful and very good information.  What I have done is this:

I used a live CD with 2.6.31-6 on it.  When it was loaded without doing anything else in a terminal I entered 

```
sudo apt-get install wvdial
```

It downloaded the software and hung at the configuring wvdial step.

I then reloaded a live CD wh 2.6.31-4 on it and the same thing happened.

I think I must have some hardware that interferes with wvdial. I am goingto load another live CD, let it get hung and follow your instructions.  I will let you know what happens.  BTW rebooting didn't have any effect.

---

### Post by Michaelg14 on 2009-08-18
I tried it again with a live CD and used your suggestions.  This is what I got:

> ubuntu@ubuntu:~$ sudo kill 4578
ubuntu@ubuntu:~$ sudo dpkg --audit
The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 wvdial               PPP dialer with built-in intelligence

The following packages have been triggered, but the trigger processing
has not yet been done.  Trigger processing can be requested using
dselect or dpkg --configure --pending (or dpkg --triggers-only):
 libc6                GNU C Library: Shared libraries

ubuntu@ubuntu:~$ dpkg --configure wvdial
dpkg: requested operation requires superuser privilege
ubuntu@ubuntu:~$ sudo dpkg --configure wvdial
dpkg: status database area is locked by another process
ubuntu@ubuntu:~$ 

I think it is pretty hopeless for now, as time progresses it will likely be addressed.

Thanks for all your help

---

### Post by cariboo on 2009-08-18
Have you tried removing the lock file in /var/lib/dpkg?

---

### Post by Michaelg14 on 2009-08-18
> Have you tried removing the lock file in /var/lib/dpkg? 

No, I haven't.  The fact that it is locked is a consequence of the attempt to load and configure wvdial.  It shouldn't be occuring in the first place.  I have now reinstalled from the latest daily build and will wait for someone smarter than me to get my CDMA working.  This seems to be a known problem with network manager.  Hopefully it will be fixed before I lose my WIFI.  :)

---

### Post by GeorgeVita on 2009-08-19
Hi **Michaelg14**,

**[COLOR="Blue"]Stop Press:[/COLOR]** first try the latest network manager build, adding 'trunk' version at System > Administration > software sources
>>> more info at: **[https://edge.launchpad.net/~network-manager/+archive/trunk](https://edge.launchpad.net/~network-manager/+archive/trunk)**

**EDIT note**
the 'easy way' is to wait for the bug-fix (network manager), hope it will come ASAP because affects a lot of mobile broadband users.

Other ways like wvdial and pppd (below) can 'self-educate' us using 'Linux basics'.
**/EDIT note**

would you like to try a 'hard core' altrnative method? A pppd comaaaaaaand?
(after the recent problems with network manager [THIS]("http://ubuntuforums.org/showpost.php?p=7790046") is the way I am connecting!

If your connection was OK with network manager running, yoou must do some 'reverse engineering':
Boot without the modem, wait for the system to fully load, attach the modem, wait some seconds, try:```
dmesg | grep tty
```Above will show your system's activity creating the tty ports for your modem.

Create (network manager) the mobile broadband connection (hope this was working in the past), STOP network manager and RESTART it in debug mode:```
sudo /etc/init.d/NetworkManager stop
sudo /usr/sbin/NetworkManager --no-daemon
```
Try to connect and see lines running. After some lines printed in terminal, it will stop. Scroll upwards and 'catch' the line '**/usr/sbin/pppd nodetach...**
[size=0](my specific line is: NetworkManager: <debug> [1250658424.730525] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute user web ttyUSB0 noipdefault noauth usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/0 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so)[/size]

Post it here to follow up!

Regards,
George

---

