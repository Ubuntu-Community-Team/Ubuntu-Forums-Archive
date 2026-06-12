---
title: "package install fails with message: `xlibmesa-dri' is missing final newline"
date: 2005-06-04
forum: Installation &amp; Upgrades
---

### Post by dude_a_b_c on 2005-06-04
Hello all.  
I installed Ubuntu 5.04, and am trying to install the nvidia-glx package.
However, the install fails with the following error output:

Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  nvidia-settings nvidia-kernel-source
The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 24 not upgraded.
Need to get 0B/3052kB of archives.
After unpacking 9986kB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/nvidia-glx_1.0.7174-0ubuntu1_i386.deb (--unpack):
 files list file for package `xlibmesa-dri' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1.0.7174-0ubuntu1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

======
It is a plain install with no other tweaks or packages installed.  

Any advice on how to solve this?

Thanks in advance.

---

### Post by dude_a_b_c on 2005-06-04
Update: I am getting this error when I try to install any package either from the cdrom or from the online repositories...

---

### Post by dude_a_b_c on 2005-06-05
[QUOTE=dude_a_b_c]Update: I am getting this error when I try to install any package either from the cdrom or from the online repositories...[/QUOTE]
Any suggestions on how to go about fixing this?  Except for this major showstopper problem, everything else is working fine.   But this is a major hurdle. 

 :-?

---

### Post by Gtaylor on 2005-06-05
Your best bet is to re-update and try again if you haven't already. Try typing this in a console:
```

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install nvidia-glx

```
Hope that helps

---

### Post by dude_a_b_c on 2005-06-06
Thanks for the suggestion.

However,  executing 


sudo apt-get update
sudo apt-get dist-upgrade

results in the following:

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/gzip_1.3.5-9ubuntu3.2_i386.deb (--unpack):
 files list file for package `xlibmesa-dri' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/gzip_1.3.5-9ubuntu3.2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

The same error that `xlibmesa-dri' is missing final newline

Is reinstallation now the only option?  I would like to avoid that... or is there anything else to try?   ](*,) 

Thanks in advance.

---

### Post by dude_a_b_c on 2005-06-06
A bit more searching has revealed that this is not a new problem...

[http://ubuntuforums.org/archive/index.php/t-12737.html](http://ubuntuforums.org/archive/index.php/t-12737.html)

lists a similiar situation...

but so far no sign of a solution anywhere ???

Thanks in advance.

UPDATE:

[http://www.linuxquestions.org/questions/history/318950](http://www.linuxquestions.org/questions/history/318950)

presented the solution:  Adding a newline to the xlibmesa-dri.list file in vi .

this seems to be a fairly common stumbling block for newbies!!!

---

