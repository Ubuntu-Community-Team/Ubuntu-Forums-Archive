---
title: "sudo apt-get update error"
date: 2015-06-03
forum: Installation &amp; Upgrades
---

### Post by ramsforums on 2015-06-03
I am running the following command


```
sudo apt-get update;
```


after successfully executing the command I get the following error message.
> 
Fetched 60.2 kB in 10s (5,511 B/s)
W: Failed to fetch [http://packages.linuxmint.com/dists/rebecca/main/binary-i386/Packages](http://packages.linuxmint.com/dists/rebecca/main/binary-i386/Packages)  Hash Sum mismatch


E: Some index files failed to download. They have been ignored, or old ones used instead.



The I ran the following command


```
 inxi -Sr
```


I got the following message.


> 
System:    Host: dc7700 Kernel: 3.13.0-37-generic i686 (32 bit) Console: tty 0 Distro: Linux Mint 17.1 Rebecca
Repos:     Active apt sources in file: /etc/apt/sources.list.d/official-package-repositories.list
           deb [http://packages.linuxmint.com](http://packages.linuxmint.com) rebecca main upstream import #id:linuxmint_main
           deb [http://extra.linuxmint.com](http://extra.linuxmint.com) rebecca main #id:linuxmint_extra
           deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted universe multiverse
           deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted universe multiverse
           deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security main restricted universe multiverse
           deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) trusty partner



How do I fix the error? Thank you :)

---

### Post by dino99 on 2015-06-03
comment out (# at the begin of line) the rebecca entries

---

### Post by RobGoss on 2015-06-03
> **ramsforums said:**
> I am running the following command


```
sudo apt-get update;
```


after successfully executing the command I get the following error message.



The I ran the following command


```
 inxi -Sr
```


I got the following message.





How do I fix the error? Thank you :)


I'm assuming you ran that command as you displayed it in your above post correct?
```
 [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update;[/FONT][/COLOR]
```

If you are trying to update your system it should be executed like this
```
 [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update[/FONT][/COLOR]
```

I'm I not understanding your question.

---

### Post by ramsforums on 2015-06-08
> **RobGoss said:**
> I'm assuming you ran that command as you displayed it in your above post correct?
```
 [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update;[/FONT][/COLOR]
```

If you are trying to update your system it should be executed like this
```
 [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update[/FONT][/COLOR]
```

I'm I not understanding your question.

Thanks RobGoss

The problem is I am getting the following error when I update. (Please note I have extracted only portion of error which displays at the end upon completion of update command)

> 
[COLOR=#000000]*Fetched 60.2 kB in 10s (5,511 B/s)*[/COLOR]
[COLOR=#000000]*W: Failed to fetch *[/COLOR][http://packages.linuxmint.com/dists/...-i386/Packages]("http://packages.linuxmint.com/dists/rebecca/main/binary-i386/Packages")[COLOR=#000000]* Hash Sum mismatch*[/COLOR]


[COLOR=#000000]*E: Some index files failed to download. They have been ignored, or old ones used instead.*[/COLOR]

I do not know how to fix.

---

