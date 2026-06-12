---
title: "update mgr. doesn't upgrade to 7.10"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by derek45 on 2007-12-29
Every time I try to update to 7.10,  it  does not do it.  it's like it tries for a second and stops.

How do I update this ToshibaM45-s165 laptop?  My desktop went easy.

I'm running 7.04

I have 1 gig of ram

1.5M DSL.

---

### Post by taurus on 2007-12-29
Was there any error message?  Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by derek45 on 2007-12-29
derek45@M45-S165:~$ cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted multiverse universe #Added by software-properties
derek45@M45-S165:~$

---

### Post by taurus on 2007-12-29
> **derek45 said:**
> derek45@M45-S165:~$ cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted multiverse universe #Added by software-properties
derek45@M45-S165:~$

That's all you have for your /etc/apt/sources.list, two lines?

Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove those two lines.  Then, add these in.

```

deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

deb http://archive.ubuntu.com/ubuntu feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

#deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

#deb http://archive.canonical.com/ubuntu feisty-commercial main 

```
Save it and close gedit window.  Then, run

```
sudo apt-get update
sudo apt-get upgrade
```
Wait for it to finish.  Then, see if you can upgrade to Gutsy now.

---

### Post by derek45 on 2007-12-29
thanks,  it's churning thru a bunch of updates now......


(fingers crossed)  :)

---

### Post by derek45 on 2007-12-30
COOL

That made it work.  I'm now running 7.10

Thanks Very Much !

HAPPY NEW YEAR !

---

