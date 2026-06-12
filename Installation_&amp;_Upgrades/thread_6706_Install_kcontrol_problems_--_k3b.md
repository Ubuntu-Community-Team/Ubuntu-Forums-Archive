---
title: "Install kcontrol problems -- k3b"
date: 2004-11-30
forum: Installation &amp; Upgrades
---

### Post by VaDor on 2004-11-30
HI, everybody

I am using gnome, and i haven't and don't waNt KDE, but ok i have to install some packages to run some programs such as k3b,  I tried to install k3b using synaptics. He calculate the depencies , then download all files needed but the problem was when he was trying to install.  In the middle of the instalation some errors ocurr . I saw in scroll that was a kcontrol problem so  i went to  a shell and did apt-get install kcontrol and this is  the problem:

 [I]   root@speedy:/home/vador/leic/trabalhos/proxyweb # apt-get install kcontrol
Reading Package Lists... Done
Building Dependency Tree... Done
Suggested packages:
  khelpcenter
The following NEW packages will be installed:
  kcontrol
0 upgraded, 1 newly installed, 0 to remove and 58 not upgraded.
3 not fully installed or removed.
Need to get 0B/6280kB of archives.
After unpacking 15.4MB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 84214 files and directories currently installed.)
Unpacking kcontrol (from .../kcontrol_4%3a3.2.2-1ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/kcontrol_4%3a3.2.2-1ubuntu2_i386.deb (--unpack):
 trying to overwrite directory `/usr/bin/fileshareset' in package kdelibs-bin with nondirectory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kcontrol_4%3a3.2.2-1ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@speedy:/home/vador/leic/trabalhos/proxyweb #
[/I]



Can anybody help ? without this package i can't install k3b!! :(


Thanks everybody  =D>

---

### Post by calvinpriest on 2004-12-01
Try looking in the directory /usr/bin/fileshareset/ and find a relatively unusual looking filename.

Then do:
dpkg -S filename

This command will tell you which package(s) contain a file of that name (which is why it helps if the filename is unique).

Then, depending on what the package is, it may be safe to:
apt-get remove packagename

Before doing the last part you may want to post the package name back here so we can make sure removing it isn't going to screw up your system.

After that package is removed you should be able to install kcontrol and k3b.

---

### Post by VaDor on 2004-12-01
HI and thanks for helping!!  Here is what is inside:

[B]root@speedy:/usr/bin/fileshareset # ls
dbootstrap_settings  fileshareset  install-report.template[/B]

Then i made the dpkg -S

[B]root@speedy:/usr/bin/fileshareset # dpkg -S fileshareset
kdelibs-bin: /usr/bin/fileshareset[/B]

So kdelibs-bin package has this file too..    ](*,) 

remove kdelibs-bin?   :-k

---

### Post by calvinpriest on 2004-12-01
Yes, remove kdelibs-bin.  It may want to remove a bunch of other kde stuff as well, but that's ok.

Then try installing kcontrol and k3b.

---

### Post by TravisNewman on 2004-12-01
If that doesn't work, do

dpkg --force-overwrite /path/to/kcontrol_4%3a3.2.2-1ubuntu2_i386.deb

It may complain about not being able to configure because of a dependency not being configured. If so, do something like "sudo apt-get install nano" or some other package you know to be installed already.

---

### Post by VaDor on 2004-12-01
I tried first remove kdelibs-bin and then install k3b kcontrol same error... that i post in the beginning of this thread.

But then i tried to force package kcontrol has panickedthumb i presume he meant:
"dpkg --force-overwrite -i  /path/to/kcontrol_4%3a3.2.2-1ubuntu2_i386.deb" (flag -i) .

And then he asks me about kdelibs4 i installed with apt-get install, then I  forced again kcontrol.  Sucess kcontrol was installed, then i just did apt-get install k3b and Voula everything working now!!!  =D> 

Thanks everyone to help :)   i was a slackware user for too long i am not habitued to fast install packages, and everything working when we install this distro  8-[      

So I have to say this is a pretty good distribution, and i want to keep her  8) .

The only problem is the kernel compiling,   vanilla + patchs like cko or ack  and then compille and use here is a bit changelling.   

Cya and thnks for help  =D>      =D>     :D

---

