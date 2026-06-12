---
title: "Feisty 7.04 (Ubuntustudio) can't install build-essential"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by bascheez on 2008-02-18
When trying to install build-essential (so I can make use of tarballs), I get the following:

steven@ubuntu:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

I'm running Feisty 7.04 (Ubuntustudio) on i386. Universe & multiverse are enabled. I could be mistaken, but I think it used to work...? TIA, Steve

---

### Post by Pumalite on 2008-02-18
Post the output of
sudo apt-get install -f

---

### Post by the1417 on 2008-02-19
depend on bla blabla cannot ins@@@

are you use the repo? i often have this problem. what i do, and its work, just open synaptic and add cdrom again. just like that. and reinstall software depend on.

---

### Post by wolfen69 on 2008-02-19
insert ubuntu cd, then:
```
sudo apt-cdrom add
```
```
sudo aptitude update
```
```
sudo aptitude install build-essential
gcc -v
```

---

### Post by ashmew2 on 2008-02-19
If you dont have a cd rom , just try in the terminal

```
sudo aptitude install build-essential
```

I think aptitude resolves dependencies better as compared to apt-get.

---

### Post by bascheez on 2008-02-22
Thanks, all. Aptitude seems to have succeeded. It downgraded libc6, and the install worked. Now to try an actual build!

---

### Post by mikembm on 2008-02-26
Wow, registered just now to say that I also had this problem and this solution worked for me. I don't know how I got that newer version oflibc6 though....

---

