---
title: "Upgrade to 8.10: &quot;Upgrade failed&quot; maybe... How to check"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by Mr_JMM on 2008-10-30
Hi, 

Sorry, this is going to be an incredibly vague thread but I hope someone can make sense of it.

I have just upgraded (??) from Hardy to Intrepid. I did this using the update manager (as per [this thread]("http://www.ubuntu.com/getubuntu/upgrading")). Right at the end I got an error message saying that the upgrade could not be completed. Sorry but I didn't get a chance to note the exact message but I'm sure it said that the upgrade will not happen. However, when I check using lsb_release -a I get:
```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid
```

I appreciate that that should be that but after the error message is there any way to double check everything or better still, some way of running a "repair" install from a CD?

Additionally, I also got a window asking for Nullmailer which I have no idea about. I just hit forward. I also got an error message about the ufw failing to install.

Many thanks as always

James

---

### Post by Partyboi2 on 2008-10-30
Open a terminal and try[FONT=monospace]
[/FONT]```
sudo dpkg --configure -a
sudo apt-get upgrade
sudo apt-get dist-upgrade 

```

---

### Post by Partyboi2 on 2008-10-30
deleted

---

### Post by Mr_JMM on 2008-10-30
Hi,

Ok, here is the results:
```
xxxxx@yyyy-ubuntu:~$ sudo dpkg --configure -a
[sudo] password for xxxxx: 
xxxxx@yyyy-ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
xxxxx@yyyy-ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
xxxxx@yyyy-ubuntu:~$ 
```

Does this confirm all is ok? Is this the only check? What about the "repair" option?

Many thanks again

---

### Post by kostkon on 2008-10-30
> **Mr_JMM said:**
> Hi, 

Sorry, this is going to be an incredibly vague thread but I hope someone can make sense of it.

I have just upgraded (??) from Hardy to Intrepid. I did this using the update manager (as per [this thread]("http://www.ubuntu.com/getubuntu/upgrading")). Right at the end I got an error message saying that the upgrade could not be completed. Sorry but I didn't get a chance to note the exact message but I'm sure it said that the upgrade will not happen. However, when I check using lsb_release -a I get:
```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid
```

I appreciate that that should be that but after the error message is there any way to double check everything or better still, some way of running a "repair" install from a CD?

Additionally, I also got a window asking for Nullmailer which I have no idea about. I just hit forward. I also got an error message about the ufw failing to install.

Many thanks as always

James
Everything looks OK.

Don't worry about the
```
No LSB modules are available.
```
it is not an error message that should worry you. We all get it when we give the above command.

Now about *ufw*, give in a terminal
```
apt-cache policy ufw
```
and see if it says that is installed and it is the latest version. But since *sudo dpkg --configure -a* does not give you any errors then you should be fine.

No clue about *NullMailer*... :(

---

### Post by Mr_JMM on 2008-10-30
Hi,

Results of apt-cache policy ufw:

```
ufw:
  Installed: 0.23.2
  Candidate: 0.23.2
  Version table:
 *** 0.23.2 0
        500 http://gb.archive.ubuntu.com intrepid/main Packages
        100 /var/lib/dpkg/status
```

Many thanks

---

### Post by Mr_JMM on 2008-10-31
Could someone just confirm if it is possible or not to do a "repair" installation (as you can with Windoze)?

Cheers

---

