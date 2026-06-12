---
title: "apt hell rollback"
date: 2018-02-12
forum: Installation &amp; Upgrades
---

### Post by luca31 on 2018-02-12
Hi all, a couple of days ago I managed to install guitarpro6 (a 32bit release) on a amd64 xenial os following [this reddit post]("https://www.reddit.com/r/GuitarPro/comments/4vqlpc/installing_guitarpro6_on_64_bit_ubuntu_1604_and/"). I did a favour to a friend, unfortunately the program isn't mine and the filesystem of the host hasn't snapshot capacity:( Now I'm wondering what to do if a future upgrade will break the required dependencies. What is the best strategy to save the current status before / rollback a future upgrade? 
 I read about apt-clone or using the dpkg log to undo the updated package, but I'm not sure if it's the right/simpler way, I'm also wondering if I should take a look to puppet or ansible. 
Surely I need to review aptitude, apt, dpkg documentation, anyway I'd like to have also your opinions.

Regards

Luca

---

### Post by cruzer001 on 2018-02-12
You really don't want the entire system not updating, stopping security and other fixes.  Lock the individual packages using Synaptic Package Manager.   

[https://askubuntu.com/questions/27063/how-to-hold-a-package-back-from-being-upgraded](https://askubuntu.com/questions/27063/how-to-hold-a-package-back-from-being-upgraded)

---

### Post by luca31 on 2018-02-12
Yes but I'd like to try a complete upgrade and if it broke the dependencies I would like to rollback and tweak the necessary pinning. I also thought to dump the entire filesystem with dd or use a backup software like amanda but they seems drastic solutions.. I would prefer to use package manager tools to get the rollback done if possible.

---

### Post by cruzer001 on 2018-02-12
Just do a simulated run and see what happens.

First update:
```
sudo apt-get update
```

Then upgrade:
```
sudo apt-get -s upgrade
```

Using the "-s" switch:
No action; perform a simulation of events that would occur based on the current system state but do not actually change the system.

Look it up:
```
man apt-get
```

---

### Post by luca31 on 2018-02-13
Uh thanks for the hint, the option -s seems really useful to keep in mind. Anyway I copied the program manually following a tutorial... not my play, I mean, I opened the deb archive, copied specific files, launched the program and installed a set of missing i386 libreries whenever I got an error. I'm sure a specific version of zlib and libcrypto is required so I can avoid those upgrade but I don't know  if other libreries could be problematic, but I presume the package manager wouldn't complain to overwrite them. I think the only way is installing it and downgrade in case of problem. A rollback solution ready would be comforting.. Sorry for my English

---

### Post by cruzer001 on 2018-02-13
dpkg-repack creates a .deb file out of a package that has already been installed.

[http://manpages.ubuntu.com/manpages/xenial/man1/dpkg-repack.1.html](http://manpages.ubuntu.com/manpages/xenial/man1/dpkg-repack.1.html)

[https://askubuntu.com/questions/309527/how-to-package-installed-packages](https://askubuntu.com/questions/309527/how-to-package-installed-packages)

---

### Post by #&amp;thj^% on 2018-02-13
Along with the good advice you have been given by cruzer001.
**Warning have good back ups in place before going forward>**
The short answer - you could use the following command:
```
apt-get -s install $(apt-history rollback | tr '\n' ' ')

```
if it does what you want remove the -s and run it again. Here are the steps I took to get this working properly:

*I temporarily trimmed my /var/log/dpkg.log to leave just today's upgrade

**I installed the tiny script apt-history from here into ~/.bashrc and ran

```
apt-history rollback > rollback.txt
```
This provides a nicely formatted list of versioned packages to roll-back to by feeding it into apt-get install. Trim this list as needed in a text editor and then run **(with -s for dry-run first):**
```
apt-get -s install $(cat rollback.txt | tr '\n' ' ')
Now without the safety net:
apt-get install $(cat rollback.txt | tr '\n' ' ')
```
Apt will warn about the downgrades which is expected. To prevent this rollback to be overwritten by the next upgrade, the packages will need to be pinned, until the original issue is resolved. For example with: "apt-mark hold zfsutils libzfs2 ..."
My script used is:
```
function apt-history(){
    case "$1" in
      install)
            cat /var/log/dpkg.log | grep 'install '
            ;;
      upgrade|remove)
            cat /var/log/dpkg.log | grep $1
            ;;
      rollback)
            cat /var/log/dpkg.log | grep upgrade | \
                grep "$2" -A10000000 | \
                grep "$3" -B10000000 | \
                awk '{print $4"="$5}'
            ;;
      *)
            cat /var/log/dpkg.log
            ;;
    esac
}

```
Fair warning again BACKUPS BACKUPS BACKUPS :D Prevention is 90% of the cure. ;)

---

### Post by cruzer001 on 2018-02-13
^^^+1 - an excellent post^^

---

### Post by luca31 on 2018-02-17
The arguments $2 and $3 of the apt-history function are meant to contain dates to filter out upgrades in a specific period, right?
Sorry for the late answer, I was out of town
You rock, guys

---

