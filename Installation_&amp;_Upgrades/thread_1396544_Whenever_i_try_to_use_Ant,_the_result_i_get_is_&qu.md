---
title: "Whenever i try to use Ant, the result i get is &quot;Killed&quot; , anyone??"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by rd.pt on 2010-02-02
Hi all, 

i'm am sorry for yet another thread about ant install issues, but it's proven to be quite difficult to search for help on this matter...

I've installed ant using apt-get, and it all goes well (supposedly..) the problem is that when i use the comand: 

```
~$ant
```,
 i get an immediate "killed" response, instead of the supposed 

```

~$ant
Buildfile: build.xml does not exist!
Build failed
```i've tried install ant again, after removing everything....i also have other linux boxes, same version of linux where i have had no trouble like this.... The only difference is that in this one i've patched the kernel with GRsecurity, and i'm quite new to these procedures, so i admit that i can have messed it up somehow...although everything else seems to be working properly, it boots correctly and have installed some other pieces of software. It was only when building the Globus Toolkit that i noticed this problem (once again, i've installed Globus on other machines, the same version, and all went well so i dont think it's a problem with this...)


Any help greatly apreciated, 

Daniel:popcorn:

---

### Post by rd.pt on 2010-02-02
So....i found out that it's indeed related with the GRsecurity patch.....does anyone had to deal with this problem? 
the tail -f syslog result follows:

```
Feb  2 15:29:04 pfound-grsec kernel: PAX: execution attempt in: <anonymous mapping>, 512db000-51303000 512db000
Feb  2 15:29:04 pfound-grsec kernel: PAX: terminating task: /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/bin/java(java):9289, uid/euid: 1001/1001, PC: 512db040, SP: 5fe7c22c
Feb  2 15:29:04 pfound-grsec kernel: PAX: bytes at PC: 55 8b 6c 24 08 53 56 9c 58 50 8b c8 81 f0 00 00 04 00 50 9d 
Feb  2 15:29:04 pfound-grsec kernel: PAX: bytes at SP-4: 
Feb  2 15:29:04 pfound-grsec kernel: grsec: denied resource overstep by requesting 4096 for RLIMIT_CORE against limit 0 for /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/bin/java[java:9289] uid/euid:1001/1001 gid/egid:100/100, parent /bin/bash[bash:5613] uid/euid:1001/1001 gid/egid:100/100

```

once again, any help solving this, without saying to unload the grsec modules :D, is greatly apreciated.

Thanks for reading,
Daniel

---

### Post by rd.pt on 2010-02-03
Well, I already know what's the problem....
 for the record, if you're using a grsecurity patched kernel, and have the intention of running Java, it seems that the option mprotect() must be OFF, at least for that process...(you'll see that in the config manual, under the section "Address Space Protection" they suggest that it should be ON)...

so, install chpax , and also is always useful to read [http://www.grsecurity.org/confighelp.php](http://www.grsecurity.org/confighelp.php)

This is not written on stone, i just think it's the solution for this particular problem...

Hope to have helped anyone...

Daniel

---

