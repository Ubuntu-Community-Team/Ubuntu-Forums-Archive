---
title: "Network installation"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by movedx on 2008-05-02
Greetings,

I have a local mirror setup on a laptop that I use to install stuff from - it's very sexy. It currently doesn't handle security updates and -src debs, only main, restricted and universe. The former two debs use the gb mirrors.

When I try to install from a minimal CD and use my local mirror, it fails stating it can't find a certain file. Of course, to be extra helpful, the installation doesn't tell me what file it's looking for on the mirror.

So I ask; can anyone give me an idea of what is required of a mirror to act as an installation point? Does it require the security and source repos? What am I potentially missing here?

I setup the mirror using 'apt-mirror' and it's accessible via apache2. It works fine as I've installed apps from it. I run Ubuntu Hardy.

All help appreciated.

Thanks.

---

### Post by bryanagee on 2008-05-02
Up until hardy, I have been using a local mirror in our office to install feisty and gutsy on all of the workstations. in order to make that possible, I only had to add a repo to a couple of lines in the [FONT="Courier New"]/etc/apt/mirror.list[/FONT] :

```
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main **main/debian-installer** restricted universe multiverse
...
deb http://us.archive.ubuntu.com/ubuntu gutsy-security main restricted **main/debian-installer** universe multiverse
...
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted **main/debian-installer** universe multiverse


```

For some reason this does not work with hardy, despite my best efforts. I even added the lines:

```
deb http://mirrors.kernel.org/ubuntu hardy main main/debian-installer restricted restricted/debian-installer
deb http://mirrors.kernel.org/ubuntu hardy-updates main restricted
deb http://mirrors.kernel.org/ubuntu hardy-security main restricted

```

...but to no avail albeit it caused several additional gig of downloads. Update works just fine, but fresh install gives me a message saying that no kernel packages were available. If anyone has apt-mirror working for clean net installs of hardy, could you post your [FONT="Courier New"]mirror.list[/FONT] ? 

Here is mine:
```
############# config ##################
#
# set base_path    /var/spool/apt-mirror
#
# if you change the base path you must create the directories below with write privlages
#
# set mirror_path  $base_path/mirror
# set skel_path    $base_path/skel
# set var_path     $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
set nthreads     3
set tilde 0
#
############# end config ##############

##  Feisty Mirror ##

deb http://us.archive.ubuntu.com/ubuntu/ feisty main main/debian-installer restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted main/debian-installer universe multiverse

##  Gutsy Mirror ##

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main main/debian-installer restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted main/debian-installer universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted


##   Hardy Mirror ##

deb http://us.archive.ubuntu.com/ubuntu/ hardy restricted/debian-installer main/debian-installer main restricted universe multiverse
deb-amd64 http://us.archive.ubuntu.com/ubuntu/ hardy restricted/debian-installer main/debian-installer main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse

clean http://us.archive.ubuntu.com/ubuntu


##    Kernels   ##
deb http://mirrors.kernel.org/ubuntu hardy main main/debian-installer restricted restricted/debian-installer
deb http://mirrors.kernel.org/ubuntu hardy-updates main restricted
deb http://mirrors.kernel.org/ubuntu hardy-security main restricted

clean http://mirrors.kernel.org/ubuntu



##     Security Updates  ##
deb http://security.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse main/debian-installer restricted/debian-installer
deb-src http://security.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted main/debian-installer universe multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted main/debian-installer universe multiverse

clean http://security.ubuntu.com/ubuntu


##     Canonical    ##
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner
#deb http://archive.canonical.com/ubuntu hardy partner
#deb-src http://archive.canonical.com/ubuntu hardy partner

clean http://archive.canonical.com/ubuntu


```

---

### Post by movedx on 2008-05-03
I've not received any further assistance on this. I guess no one knows. No one on IRC knows either.

---

### Post by bryanagee on 2008-05-03
My mirror still works for Gutsy and Feisty, so I end up installing Gutsy and using update-manager to upgrade. It works well enough, but I'd love to skip a step.

---

### Post by movedx on 2008-05-05
Hi,

It appears we're doing it wrong. It seems instead of...

```
deb <url> hardy main main/debian-installer
```

it's required that you do

```
deb <url> hardy main/debian-installer
```

The former gave me the following error:

> Proceed indexes: [PPsh: cannot open archive.ubuntu.com/ubuntu//dists/hardy-updates/main/debian-installer/binary-i386/Packages.gz: No such file

Where as the latter simply executed fine and started/continued to download the files:

> Proceed indexes: [PPPP]

17.2 GiB will be downloaded into archive.
Downloading 17903 archive files using 20 threads...
Begin time: Mon May  5 12:37:23 2008
[20]...

Here is my mirror.list file:
```

deb http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu hardy main/debian-installer

deb http://archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse

#deb http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu hardy-proposed main restricted universe multiverse

#deb-src http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse

#deb-src http://archive.ubuntu.com/ubuntu hardy-proposed main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse

clean http://archive.ubuntu.com/ubuntu
```

I hope this helps in some manner and I'll let you know if this works or not.

---

