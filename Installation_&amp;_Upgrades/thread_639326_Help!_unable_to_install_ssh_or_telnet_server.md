---
title: "Help! unable to install ssh or telnet server"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by whydoesntwork on 2007-12-13
Hello,

Just did a fresh install with Ubuntu desktop 7.1, trying to enable ssh or telnet server so I can  remotely manage it.. (btw, I know telnet is not secure but I need it to verify other protocols.).

This is ridiculous that I can't find a clear answer even I  saw so many people posts their similar problems, I have spent much time reading all the posts but now come to the point to need your help..   someone mentioned to modify the source.list file to enable ssh and telnet, but didn't give details, is that going to solve the problem?  then what about ftp or sftp?

this is the error when trying to install ssh..


$ sudo apt-get install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openssh-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package openssh-server has no installation candidate
$
$ sudo apt-get install ssh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ssh is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  openssh-client ssh-askpass-gnome
E: Package ssh has no installation candidate
$



Your help is greatly appreciated!

---

### Post by louieb on 2007-12-13
openssh-server is generally one of the first packages I install. Its in the main repository. I guess you have a internet connection. Did you have  one when you installed? 
Theres a GUI to check which repositories are enabled. can't remember where it at or 
Press Alt+F2 and enter.
```
gksudo gedit /etc/apt/sources.list
```
Instruction for editing are in the file. 
When done open a terminal window and run
```
sudo aptitude update
```
and you should be all set.

---

### Post by malaprohibita on 2007-12-13
Hmmm, I've always installed it as "sudo apt-get install ssh".

---

### Post by daengbo on 2007-12-13
Whydoesntwork,

Both the openss client and server are available in the main repositories but neither are on the install CD.

You probably haven't had time for your first scheduled update to run, so the package lists from the internet haven't been loaded yet. The computer only knows about the packages on teh install CD at this time. Fixing the problem is simple:

Go to System -> Administration -> Synaptic Package Manager
and enter you password to get admin rights. Then click on "Reload."

This will check the repositories and update the package lists. Then you can search from within Synaptic or use the command line the way you were before.

You can also solve the problem by leaving the system on until tomorrow (after the lists have loaded), then trying again. Meh.

---

### Post by whydoesntwork on 2007-12-13
Thanks Daengbo, I tried what you said but still have the same problem, do I need modify the source.list first? or do I do some editing on the synapatic manager? I click "reload", then search the "ssh" but found only ssh-clinet is installed.


> **daengbo said:**
> Whydoesntwork,

Both the openss client and server are available in the main repositories but neither are on the install CD.

You probably haven't had time for your first scheduled update to run, so the package lists from the internet haven't been loaded yet. The computer only knows about the packages on teh install CD at this time. Fixing the problem is simple:

Go to System -> Administration -> Synaptic Package Manager
and enter you password to get admin rights. Then click on "Reload."

This will check the repositories and update the package lists. Then you can search from within Synaptic or use the command line the way you were before.

You can also solve the problem by leaving the system on until tomorrow (after the lists have loaded), then trying again. Meh.

---

### Post by whydoesntwork on 2007-12-13
Louieb, thanks for the answer. 

Please pardon my ignorance, this is the part I didn't get: what lines need to be edited in the source.list file? do I need uncomment all the lines start with "deb http://security.ubuntu.com/..."? Do I need uncomment all other lines with "universal" or "multiservice"? or what else? I actually tried edit it before I post the question but didn't solve the problem so I think I must missed some lines... thanks.

> **louieb said:**
> openssh-server is generally one of the first packages I install. Its in the main repository. I guess you have a internet connection. Did you have  one when you installed? 
Theres a GUI to check which repositories are enabled. can't remember where it at or 
Press Alt+F2 and enter.
```
gksudo gedit /etc/apt/sources.list
```
Instruction for editing are in the file. 
When done open a terminal window and run
```
sudo aptitude update
```
and you should be all set.

---

### Post by louieb on 2007-12-13
Because I know sooner or later I know I'll want something from it I'll  uncomment all the lines that start 
```
# deb http:...
to look like
deb http:...

``` universe multiverse ... what ever.

Just don't forget to run sudo aptitude update  when your finished.

---

