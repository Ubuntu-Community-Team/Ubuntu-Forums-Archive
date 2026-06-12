---
title: "Software Index is broken"
date: 2011-07-15
forum: Installation &amp; Upgrades
---

### Post by SnoopFogg on 2011-07-15
Hi, I'm getting a message from Update Manager that the Software Index is broken and that it is impossible to install or remove any software.  I'm using Ubuntu 10.04.  I've tried 

Synaptic -> Edit -> Fix broken Packages (which did nothing). 

sudo apt-get install -f gives:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  fglrx
0 upgraded, 0 newly installed, 1 to remove and 87 not upgraded.
1 not fully installed or removed.
After this operation, 60.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 381250 files and directories currently installed.)
Removing fglrx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any idea what I can do to fix this?  Cheers

---

### Post by raja.genupula on 2011-07-15
try this 
```
sudo rm -rf /var/lib/apt/lists/*
```
```
sudo apt-get update 
```

---

### Post by SnoopFogg on 2011-07-15
Thanks, after apt-get update I get:

E: Lists directory /var/lib/apt/lists/partial is missing.

Any other ideas?

---

### Post by dino99 on 2011-07-15
> **SnoopFogg said:**
> Thanks, after apt-get update I get:

E: Lists directory /var/lib/apt/lists/partial is missing.

Any other ideas?

blindly following risky command without understanding its meaning is scary, remember that for future :)

open nautilus to recreate /partial/

---

### Post by raja.genupula on 2011-07-15
i never faced the problem thats why i suggest , dont mind .

---

### Post by dino99 on 2011-07-15
> **raja.genupula said:**
> i never faced the problem thats why i suggest , dont mind .

dont use "-rf" its too scary (but you are free to use it indeed)

---

### Post by SnoopFogg on 2011-07-15
Hi, thanks. I'll be more cautious in future.  Though I am backed-up in preparation for having to reinstall 10.04.  

Tried opening nautilus to recreate /partial/.  Though all I did was to open nautilus - was I supposed to do anything else once it was opened?  It's not helped in as much as I still get the error message when I run update manager.

---

### Post by ak331 on 2011-07-15
I recently upgraded to image 2.6.32-33 these are the results

If I run synaptic manager it tells me that package is broken and I should run "sudo pkge -config -d"
when I run it in terminal the system hangs at the generating grub.cfg and just hangs and I am not sure whether I can manually remove the latest kernel or reinstall it as terminal freezes and synaptic manager quits after the message.

Any suggestions.

---

### Post by SnoopFogg on 2011-07-17
Hi, I'm still unable to use update manager which says that the software index is broken.

sudo apt-get install -f now shows:
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  fglrx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Lists directory /var/lib/apt/lists/partial is missing.

Any ideas what I can do to fix this?

---

### Post by raja.genupula on 2011-07-17
@snoopfog

             ```
sudo mkdir /var/lib/apt/lists/partial
```

try this man ,

---

### Post by SnoopFogg on 2011-07-17
Thanks, but I'm still getting error messages that the software index is broken. Then apt-get install -f shows:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  fglrx
0 upgraded, 0 newly installed, 1 to remove and 91 not upgraded.
1 not fully installed or removed.
After this operation, 60.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 381250 files and directories currently installed.)
Removing fglrx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any other ideas on how to get updates working again?

---

### Post by SnoopFogg on 2011-07-18
Hi, can anyone help with this problem - Update Manager says  Software Index is broken and that it is impossible to install or remove any software. I'm using Ubuntu 10.04 - would upgrading to 10.10 fix this?  Ideally I would like to avoid re-installation or upgrade as I'm happy with LTS.  Any help much appreciated.

---

### Post by dino99 on 2011-07-18
Update-Manager is not the only one's tool to do the job: apt-get, synaptic

sudo rm /var/cache/apt/archives/*
( dont worry about the warning, here nothing is destroyed as "-rf" is not used)

if you are using not genuine repo (like ppa, or mixing distro), then update, otherwise deactivate them first.

---

### Post by SnoopFogg on 2011-07-19
Hi, thanks for the help and your patience as I'm well out of my depth here.  Think I might have screwed something up earlier:

russ@russ-desktop:~$ sudo apt-get update
E: Lists directory /var/lib/apt/lists/partial is missing.
E: Archive directory /var/cache/apt/archives/partial is missing.

Is this fixable?

(I should point out that I tried sudo rm /var/cache/apt/archives/*, which appeared to work but didn't give any error messages when I was expecting to receive one).

---

### Post by SnoopFogg on 2011-07-24
I still cannot make any updates.  I get the following error messages:

1. System/Administration/Update manager 
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first

2. Synaptic package manager
Could not download all repository indexes
Lists directory /var/lib/apt/lists/partial is missing.Archive directory /var/cache/apt/archives/partial is missing.

3. sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  fglrx
0 upgraded, 0 newly installed, 1 to remove and 91 not upgraded.
1 not fully installed or removed.
E: Lists directory /var/lib/apt/lists/partial is missing.
E: Archive directory /var/cache/apt/archives/partial is missing.

4. sudo apt-get update
E: Lists directory /var/lib/apt/lists/partial is missing.
E: Archive directory /var/cache/apt/archives/partial is missing.


Any suggestions to fix this gratefully received.

---

### Post by SnoopFogg on 2011-07-25
Hi, Can anyone confirm whether the broken software index problem I am having is related to problems installing the nvidia closed source driver on my 10.04 machine?  (I want to use Compiz).    

russ@russ-desktop:~$ sudo apt-get install nvidia-xconfig
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-xconfig


Below is a summary of the errors I get when attempting updates on my 10.04 machine:

1. System/Administration/Update manager 
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first

2. Synaptic package manager
Could not download all repository indexes
Lists directory /var/lib/apt/lists/partial is missing.
Archive directory /var/cache/apt/archives/partial is missing.

3. sudo apt-get install -f
Reading package lists... Done
Building dependency tree 
Reading state information... Done
The following packages will be REMOVED
fglrx
0 upgraded, 0 newly installed, 1 to remove and 91 not upgraded.
1 not fully installed or removed.
E: Lists directory /var/lib/apt/lists/partial is missing.
E: Archive directory /var/cache/apt/archives/partial is missing.

4. sudo apt-get update
E: Lists directory /var/lib/apt/lists/partial is missing.
E: Archive directory /var/cache/apt/archives/partial is missing.


Are there any solutions to this problem other than a complete re-install?  I really don't want to do that if I can avoid it!  

Cheers

---

### Post by el_koraco on 2011-07-25
Try 

```
sudo mkdir /var/lib/apt/lists/partial
sudo mkdir /var/cache/apt/archives/partial
sudo apt-get update
```

---

### Post by SnoopFogg on 2011-07-25
Brilliant.  Thanks for your help.  Back in business now and all working with compiz too.  Cheers

---

