---
title: "not able to upgrade and install applications on ubuntu 11.10"
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by ramu.37 on 2011-11-12
when i try to install multimedia plugins, it shows "updating cache -- waiting for jockey-backend to exit";

why is it showing like this and what is the solution for this.

pls help me .... as i am struggling from 2 days....

---

### Post by ramu.37 on 2011-11-12
once  i waited for long time (approximately 10 min.) it showing a message like "updating cache: downloading".... but no progress...

what should i do for download to progress???

---

### Post by jerrrys on 2011-11-12
open a terminal and enter

sudo apt-get update

followed by

sudo apt-get install **NAME OF PACKAGE**

and post back any errors you get

---

### Post by ramu.37 on 2011-11-12
the fallowing message is displayed.......

ramu@Ramu:~$ sudo apt-get update
[sudo] password for ramu: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
ramu@Ramu:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package vlc
ramu@Ramu:~$ ^C
ramu@Ramu:~$ 

Thanks for the reply.....

---

### Post by raja.genupula on 2011-11-13
> **ramu.37 said:**
> the fallowing message is displayed.......

ramu@Ramu:~$ sudo apt-get update
[sudo] password for ramu: 
> E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

ramu@Ramu:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package vlc
ramu@Ramu:~$ ^C
ramu@Ramu:~$ 

Thanks for the reply.....

when you got errors like that then use this command 
```
sudo fuser -k -KILL /var/lib/dpkg/lock
sudo rm -rf /var/lib/dpkg/lock
```

and then do update

```
sudo apt-get update
```

..if you want to install the vlc media player , you can get that from software center.

If you wanna install from terminal 

> sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc

all the best

---

### Post by ramu.37 on 2011-11-13
when i tried your reply..... the fallowing message has come:

ramu@Ramu:~$ sudo apt-get update
[sudo] password for ramu: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ramu@Ramu:~$ fuser -k -KILL /var/lib/dpkg/lock 
ramu@Ramu:~$ rm -rf /var/lib/dpkg/lock 
rm: cannot remove `/var/lib/dpkg/lock': Permission denied

---

### Post by raja.genupula on 2011-11-13
> **ramu.37 said:**
> when i tried your reply..... the fallowing message has come:

ramu@Ramu:~$ sudo apt-get update
[sudo] password for ramu: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[B]> ramu@Ramu:~$ fuser -k -KILL /var/lib/dpkg/lock 
ramu@Ramu:~$ rm -rf /var/lib/dpkg/lock [/B]
rm: cannot remove `/var/lib/dpkg/lock': Permission denied

Ramu look there the commands .....type there as it is i have given , you're missing sudo there.

---

### Post by ramu.37 on 2011-11-13
the fallowing message has come:

 
ramu@Ramu:~$ sudo apt-get update
[sudo] password for ramu: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ramu@Ramu:~$ sudo fuser -k -KILL /var/lib/dpkg/lock 
/var/lib/dpkg/lock:   2162
ramu@Ramu:~$ sudo rm -rf /var/lib/dpkg/lock 
ramu@Ramu:~$ sudo apt-get update
0% [Connecting to us.archive.ubuntu.com (91.189.92.169)] [Connecting to security.ubuntu.com (91.189.92.166)] [Connecting to extras.ubuntu.com^ramu@Ramu:~$ 


what is my next step????

---

### Post by raja.genupula on 2011-11-13
why are you interrupting the update process  ..? 

to install anything first you need to do update.

dont press ctrl+z or dont stop update process.
once update done then only you'll be able to install anything to your system.
type this and dont stop or close upto it will finish

```
sudo apt-get update
```

after finishing update install what ever you want.

---

