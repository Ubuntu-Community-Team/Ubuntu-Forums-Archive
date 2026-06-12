---
title: "libpcap0.8-dev error install ?"
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by fairbird on 2011-10-28
I was tried to install libpcap0.8-dev but i got error lines ..
in use main server in software sources and and sources.list contains a tow servers only

> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse restricted universe main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse restricted universe main #Added by software-propertiesand here is error message in terminal

> raed@ubuntu:~$ sudo apt-get install libpcap0.8-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libpcap0.8-dev: Depends: libpcap0.8 (= 1.0.0-6) but 1.1.1-6 is to be installed
E: Broken packages
i use ubuntu 10.04 (lucid) ... please help my .
Thank you :)

---

### Post by fairbird on 2011-10-28
WoW ... 31 [COLOR=#000000]Views and no body replay any suggestion[/COLOR]

---

### Post by fairbird on 2011-10-29
Is a difficult question :(

---

### Post by raja.genupula on 2011-10-29
ok do this 

```
sudo apt-get install -f
sudo apt-get install libpcap0.8-dev
```

and now check it out . If its not done then use your synaptic to get that else
go with this

[http://packages.ubuntu.com/lucid/libpcap0.8-dev](http://packages.ubuntu.com/lucid/libpcap0.8-dev)

and then install it by using 
```
sudo dpkg -i filename.deb
```

All The best man.

---

### Post by fairbird on 2011-10-29
> **raja.genupula said:**
> ok do this 

```
sudo apt-get install -f
sudo apt-get install libpcap0.8-dev
```and now check it out . If its not done then use your synaptic to get that else
go with this

[http://packages.ubuntu.com/lucid/libpcap0.8-dev](http://packages.ubuntu.com/lucid/libpcap0.8-dev)

and then install it by using 
```
sudo dpkg -i filename.deb
```All The best man.

thank you friend .. but nothing done ...

after do 
> sudo apt-get install -f
sudo apt-get install libpcap0.8-dev

i got this
> raed@ubuntu:~$ sudo apt-get install libpcap0.8-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libpcap0.8-dev: Depends: libpcap0.8 (= 1.0.0-6) but 1.1.1-6 is to be installed
E: Broken packages

and also after this step
> sudo dpkg -i filename.deb

i got this error
> raed@ubuntu:~$ sudo dpkg -i libpcap0.8-dev_1.0.0-6_i386.deb
Selecting previously deselected package libpcap0.8-dev.
(Reading database ... 172421 files and directories currently installed.)
Unpacking libpcap0.8-dev (from libpcap0.8-dev_1.0.0-6_i386.deb) ...
dpkg: dependency problems prevent configuration of libpcap0.8-dev:
 libpcap0.8-dev depends on libpcap0.8 (= 1.0.0-6); however:
  Version of libpcap0.8 on system is 1.1.1-6.
dpkg: error processing libpcap0.8-dev (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 libpcap0.8-dev

any other suggestion ...:(

---

### Post by raja.genupula on 2011-10-29
have you seen in synaptic ? 

and then please do it in reverse 
i mean first install command and then that -f command.

---

### Post by fairbird on 2011-10-29
Thank you again 

> **raja.genupula said:**
> have you seen in synaptic ? 
yes. when i download it i got this error same as below picture.

[http://ubuntuforums.org/attachment.php?attachmentid=205787&stc=1&d=1319910900](http://ubuntuforums.org/attachment.php?attachmentid=205787&stc=1&d=1319910900)

> and then please do it in reverse 
i mean first install command and then that -f command 	
same problem :(

---

### Post by fairbird on 2011-10-29
VVVV
  Up

---

### Post by fairbird on 2011-10-30
Thank you ...

i solved the problem ...

i was copied source.list from live cd to my ubuntu and i was download packages success

---

### Post by raja.genupula on 2011-10-30
hi man 
   its really a good news that you have solved your issue. could you please mark the thread as solved from thread tools.

   have nice day a head.

---

### Post by fairbird on 2011-10-30
> **raja.genupula said:**
> hi man 
its really a good news that you have solved your issue. could you please mark the thread as solved from thread tools.
 
have nice day a head.
 
Ok ... good man
i will mark it ;) 
thank you

---

