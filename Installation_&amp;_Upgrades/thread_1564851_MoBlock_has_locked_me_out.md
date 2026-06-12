---
title: "MoBlock has locked me out"
date: 2010-08-31
forum: Installation &amp; Upgrades
---

### Post by roschell on 2010-08-31
I have searched for a parental control software and found Moblock. Which I did install through command line after adding the required lines to the sources list as follows.

Ubuntu 10.04 lucid:

deb [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) lucid main


Note for Ubuntu users:
You also need the "universe" section, something like

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main universe

...and install

sudo aptitude install moblock blockcontrol mobloquer

the moblock is perhaps installed but more difficult to use then I had thought. Then I attempt to remove it, and it just wont let me do anything. 

**~$ sudo aptitude purge moblock blockcontrol mobloquer**

I get the following lines...

[U]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/U]

I made sure no packaging application is running, even re-logged in, but with now success. 

I am desperate to find this just after installing ubuntu on my pc. 
Could I get some help in removing this beast? Thank you in advance.

roschell

---

### Post by BrandyBear on 2010-08-31
Does Xubuntu use a software centre like ubuntu

---

### Post by roschell on 2010-08-31
Perhaps not, and that would be question for Xubuntian. I am running Ubuntu on my laptop after coming back from "lite" Mandriva

---

### Post by jrusso2 on 2010-08-31
Sounds to me like you have the app open.  Close it and make sure the ubuntu software center is closed when you try to remove it by command line.

---

### Post by roschell on 2010-08-31
As I mentioned before. I closed all the applications and it did not resolve the problem. Then logged out and still having the centre reported as active. Is possible to close it from command line like force exit or so. 

Would reboot do anything?

---

### Post by lechien73 on 2010-08-31
Please run the following command, and then post the contents of the psoutout.txt file here. It will help us to see if there are any processes running that could have the lock file open:

```
ps aux >~/psoutput.txt
```

When you post the contents, please highlight the text, and then click the # button on the toolbar to wrap it in [CODE] tags.

Thanks

---

### Post by roschell on 2010-08-31
```
~$ ps aux >~/psoutput.txt
~$ 

```

It did not return any result. Can I do anything to remove or purge the application moblock?

---

### Post by roschell on 2010-08-31
I restarted the pc finally and went to purge the moblock again..

```
~$ sudo aptitude purge moblock blockcontrol mobloquer
 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```
```

~$ sudo dpkg --configure -a
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Setting up blockcontrol (1.6.12-1~lucid) ...
 * blockcontrol is configured not to start automatically at boot time.
 * To change this edit the INIT entry in /etc/blockcontrol/blockcontrol.conf.
 * If you don't want to see this message set VERBOSITY="2" there.

Setting up mobloquer (0.6+svn20090817+3-1~lucid) ...
```

Problem solved. Thank you to contributors for their responses.

---

