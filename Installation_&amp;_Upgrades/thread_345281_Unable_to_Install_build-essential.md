---
title: "Unable to Install build-essential"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by rabidgnome229 on 2007-01-24
When I try it gives me

> 
The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages


Attempting to install libc6-dev or libc-dev throws

> The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6-0ubuntu20.2 is to be installed
E: Broken packages


I'm a noob and have no idea what to do.

---

### Post by Chiro on 2007-01-24
> **rabidgnome229 said:**
> When I try it gives me



Attempting to install libc6-dev or libc-dev throws



I'm a noob and have no idea what to do.

You probably need to install your kernel-headers first. Look for something like 

linux-headers-2.x.xx-xx
linux-headers-2.x.xx-xx-386

The x's correspond to your kernel version. You can install kernel-headers through Synaptic. Too see your kernel version use "uname -r" from the terminal.

---

### Post by Rui Pais on 2007-01-24
libc6 has been updated recently, maybe something got broken or mixed old versions with new...

you could try:
(if you havn't done it before) ensure that your have an updated list:
```
sudo apt-get update
```
retry to install build-essential using aptitude that deal better with dependencies:
```
sudo aptitude purge build-essential
sudo aptitude install build-essential
```

and if it persist try:
```
sudo aptitude -f install 
```


you can use synaptic to check for broken packages:
click on 'Custom' (on left bottom of the window), and then on the list on the right choose 'Broken' and see you something appears there. If so clic on package to synaptic try to fix it.

good luck.

---

### Post by lorenco on 2007-01-24
[http://ubuntuforums.org/showthread.php?t=345318](http://ubuntuforums.org/showthread.php?t=345318)

I think I have the same problem.  Se posting above...

---

### Post by Rui Pais on 2007-01-24
> **lorenco said:**
> [http://ubuntuforums.org/showthread.php?t=345318](http://ubuntuforums.org/showthread.php?t=345318)

I think I have the same problem.  Se posting above...

uhmm... don't seems much related... 
rabidgnome229 seems to have some broken dependencie, which is usually a simple thing to fix.

Regrettably you seems to be in much worst troubles :( 
I don't know how but it looks like you managed to get a broken/wrong placed glibc.

Eventually to fix it you would need to remove/purge the broken thing... but since the broken thing is the heart of the all OS... it will ask for remove a lot of fundamental stuff, including apt and base system!

you can try to manually remove the incorrect libraries and (make a lot of prays to your favorite gods) do an aptitude reinstall libc6. 
On my Edgy i got (related with the output on your other thread "Matching libraries: /usr/lib/libdl.so.2 /lib/ld-linux.so.2"):
```
ls /usr/lib/libdl.so.2 
ls: /usr/lib/libdl.so.2: No such file or directory
```
and
```
ls -l /lib/ld-linux.so.2 
lrwxrwxrwx 1 root root 9 2007-01-22 22:06 /lib/ld-linux.so.2 -> ld-2.4.so
```

good luck (and you really may need it)

---

### Post by lorenco on 2007-01-24
Seems like one package is broken after the update.

See post [here]("http://ubuntuforums.org/showthread.php?t=344570")

---

### Post by Rui Pais on 2007-01-24
thanks for the link, lorenco. 
i'll keep it as reference for the case of found more people ask for this.

seems to be a weird problem that affects only some users after the upgrade...

I updated a dapper, an edgy32 and an edgy64 and didn't get any problem, message error or get to broken apt/installation. 

Those kind of errors that happen just to a few are weird and can make big headaches on the poor devs :( (and of course on the poor users that get those...)

---

### Post by thehumanfactor on 2007-01-24
Not certain if this is related. 

I tried installing build-essential on a new machine this morning.  I am no expert but have done this several times - and was quite surprised when I encountered:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main libc6-dev 2.4-1ubuntu12.2
  403 Forbidden [IP: 195.248.90.35 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12.2_i386.deb)  403 Forbidden [IP: 195.248.90.35 80]

I was able to navigate via browser all the way down to the file - my hypothesis is that the file may have been updated recently and it may be a permissions issue?

Any ideas on how to correct this?  

Thanks,

THF

---

### Post by lorenco on 2007-01-24
[http://ubuntuforums.org/showthread.php?mode=hybrid&t=345446](http://ubuntuforums.org/showthread.php?mode=hybrid&t=345446)

This will help to clarify: They have blocked the packages that broke some systems ! :) :)

---

