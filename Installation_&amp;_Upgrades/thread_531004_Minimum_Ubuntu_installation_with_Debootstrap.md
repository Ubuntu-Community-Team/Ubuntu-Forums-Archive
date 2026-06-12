---
title: "Minimum Ubuntu installation with Debootstrap"
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by 50cc on 2007-08-21
I'm trying to create a minimum installation of Ubuntu using Debootstrap, so far I have managed to edit the file 'Feisty' in /usr/lib/debootstrap/scripts. 

I changed the base var to this:
base = "binutils libc6"

After that I ran debootstrap --variant=buildd feisty /var/chroot

This all goes well, but the problem is that I was expecting that only the packages binutils and libc6 would be installed. But what happens is that a lot of other things are installed also. 

Any ideas to create a minimum system?

---

### Post by heimo on 2007-08-21
> **50cc said:**
> This all goes well, but the problem is that I was expecting that only the packages binutils and libc6 would be installed. But what happens is that a lot of other things are installed also.

Like... kernel? Bash? Apt-utils? Login? Do you have a list of packages installed?

---

### Post by 50cc on 2007-08-21
> **heimo said:**
> Like... kernel? Bash? Apt-utils? Login? Do you have a list of packages installed?

How would one create/find such a list?

---

### Post by heimo on 2007-08-21
> **50cc said:**
> How would one create/find such a list?

This could help:
```
dpkg --get-selections
```

If you see unneccessary packages, you may want to try forcing uninstall.

---

### Post by 50cc on 2007-08-21
Packages currently installed:
```

base-files                                      install
base-passwd                                     install
bash                                            install
belocs-locales-bin                              install
binutils                                        install
bsdutils                                        install
coreutils                                       install
dash                                            install
debconf                                         install
debconf-i18n                                    install
debianutils                                     install
diff                                            install
dmsetup                                         install
dpkg                                            install
e2fslibs                                        install
e2fsprogs                                       install
findutils                                       install
gcc-4.1-base                                    install
grep                                            install
gzip                                            install
hostname                                        install
initscripts                                     install
libacl1                                         install
libattr1                                        install
libblkid1                                       install
libc6                                           install
libcap1                                         install
libcomerr2                                      install
libdb4.3                                        install
libdevmapper1.02                                install
libgcc1                                         install
liblocale-gettext-perl                          install
libncurses5                                     install
libpam-foreground                               install
libpam-modules                                  install
libpam-runtime                                  install
libpam0g                                        install
libselinux1                                     install
libsepol1                                       install
libslang2                                       install
libss2                                          install
libtext-charwidth-perl                          install
libtext-iconv-perl                              install
libtext-wrapi18n-perl                           install
libuuid1                                        install
locales                                         install
login                                           install
lsb-base                                        install
makedev                                         install
mawk                                            install
mktemp                                          install
mount                                           install
ncurses-base                                    install
ncurses-bin                                     install
passwd                                          install
perl-base                                       install
procps                                          install
python-minimal                                  install
python2.5-minimal                               install
sed                                             install
startup-tasks                                   install
system-services                                 install
sysv-rc                                         install
sysvutils                                       install
tar                                             install
tzdata                                          install
upstart                                         install
upstart-compat-sysv                             install
upstart-logd                                    install
util-linux                                      install
zlib1g                                          install

```

---

### Post by heimo on 2007-08-21
It's not terribly long list. Use [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to find out what each package does and remove unnecessary ones. Perhaps gcc, dash and python, but... what else? (*



*) Not even sure about those.

---

### Post by 50cc on 2007-08-21
Well, the thing is that I am building for an embedded/semi-embedded system. And I want te keep things small, safe and simple. Because the target is an embedded system, I won't need apt or dpkg on the target itself. Also things like Perl and Python are overhead. 

I am looking for a base system concisting of, for example: 
[LIST]
[*]busybox
[*]libc
[*]kernel
[*]lilo
[*]some compact httpd
[*]ppp
[/LIST]

I currently have a different linux version on the embedded board, but this is has very old libc stuff on it, and I would much rather install Ubuntu or Debian. The current Linux version is called X-linux: [http://www.dmp.com.tw/tech/os-xlinux/]("http://www.dmp.com.tw/tech/os-xlinux/")

---

### Post by heimo on 2007-08-21
> **50cc said:**
> Well, the thing is that I am building for an embedded/semi-embedded system.

Ah, ok. Then your question makes a little more sense. But I can't understand what made you to choose Ubuntu as a base for embedded system. Good luck.

---

