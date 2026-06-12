---
title: "Unable to upgrade - exclusive lock !!!"
date: 2011-07-13
forum: Installation &amp; Upgrades
---

### Post by joneslh on 2011-07-13
I am trying to upgrade to 11.04, but I keep getting this error notice.  I have no other application runing so not sure what is going on, can anyone shed some light on what the mesage actually means ?



Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.

---

### Post by raja.genupula on 2011-07-13
not only at the upgrade , even at the update also i am getting the error some times and i do restart my pc .

---

### Post by jerrrys on 2011-07-13
this means that you have a package manager open and need to close it.  you cannot have two package managers open at once.  if you do not have another one open then try this.  go to

System>administration>system monitor>processes

and look for an open **synaptic**.  if you find one, kill it

---

### Post by joneslh on 2011-07-13
Thanks for your reply but,I have checked the system monotor and no upgrade package is running. Synaptic or Tweak

Anbyone any further thoughts on what is causing this problem and how it can be fixed

---

### Post by joneslh on 2011-07-13
UPDATE:

I have just been checking UBUNTU Tweak for anything open and received this error message below -

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory 

How can I close this directory ?

---

### Post by dFlyer on 2011-07-13
You may have a process running that preventing you from running the upgrade. It usually is a package manager ie synaptic, apt-get, dpkg, ubuntu software center, etc. From a terminal try:

ps -A

This will list all your processes.

---

### Post by joneslh on 2011-07-13
OK Gary  Run that command  and I find that apt-get looks to be running. (see below) so how can I stop it ?

2001 ?        00:00:00 sh
 2003 ?        00:00:00 run-parts
 2008 ?        00:00:00 apt
 2050 ?        09:47:26 apt-get
 2053 ?        00:00:00 http
 2054 ?        00:00:00 http
 2055 ?        00:00:00 http
 2056 ?        00:00:00 http

---

### Post by matt_symes on 2011-07-13
Hi

> 2050 ?        09:47:26 apt-get

It's been running for almost 10 hours. Send it a SIGTERM and see if it exits gracefully.

```
sudo kill 2050
```

Enter your password. It will not be echoed to the screen.

Kind regards

---

### Post by joneslh on 2011-07-14
thanks Matt for your reply

I had already worked out that I could kill the application with running in root kill -9 PID  with the PID found from running ps -A

However, why is apt-get running in the first place.  I checked this morning when first logged on and it was running.  What process at boot-up starts apt-get?

I never had this problem before when upgrading, so wonder why it has happening now !!!

anyone any thoughts ?

---

### Post by matt_symes on 2011-07-14
Hi

> **joneslh said:**
> thanks Matt for your reply

I had already worked out that I could kill the application with running in root kill -9 PID  with the PID found from running ps -A

Please only use 

```
kill -9 <pid>


```as a last resort. 

The -9 is the SIGKILL signal and the running process never gets to handle it and shutdown gracefully. The init process kills it directly. 

Always try a SIGTERM first as that can be handled by the process, and gives it the opportunity to shutdown gracefully. 

```
kill <pid>
```

SIGKILL should be a last resort if nothing else works. 

> 
However, why is apt-get running in the first place.  I checked this morning when first logged on and it was running.  What process at boot-up starts apt-get?

I expect it was update manager looking for updates. Is it still hanging ?

> 
I never had this problem before when upgrading, so wonder why it has happening now !!!

anyone any thoughts ?

Sounds like you might have an issue with apt-get after the upgrade. From what version, to what version of Ubuntu did you upgrade ?

Kind regards

---

### Post by joneslh on 2011-07-14
Thanks for info Matt about using kill command all noted.

I have not done the upgradeto 11.04, still using 10.10

Only updates I do are those that come via update manager and never had a problem before with this e.lock issue so not sure why it has suddenly started.

I

---

### Post by matt_symes on 2011-07-14
Hi

Keep an eye on it. If it happens again post back and we'll take a closer look.

This command will tell you if it is running. Look at the time column and check for a long running process.

```
ps -A | grep apt
```Kind regards

---

