---
title: "'identical' 32 bit and 64 bit installation"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by funkyade on 2010-04-01
Hi folks,

I want to keep the same set of packages across several different machines, 2 32bit, and 2 64bit, from the same base install (currently 9.1). I'm not bothered about duplicating home folders etc, but in having the same apps/packages available on both platforms.

How would I go about exporting the list of installed packages from one machine (master) and then bringing that in to say aptitude (command line) so it reads the list and installs them on the others (slaves)? exporting the .deb filenames won't work as different architectures plus possible version mismatches at least...

workflow something like -

1. Export package list from master to txt file
2. import package list into aptitude on command-line
3. install stuff

this wouldn't work -

```
sudo aptitude -y install < packagelist.txt
```

maybe -

```
for (package in packagelist); sudo aptitude -y install (package); do
```

I assume a script would be easy enough to write, but how do I get the list in the first place?

I noticed there are some OEM features available in the alternate install, but am not sure I can mix 32bit and 64bit with this... or if I can do what I want...

Any suggestions appreciated... :)

---

### Post by oldfred on 2010-04-01
You can already do this:
sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work.
generate new sources file

[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
from lovinglinux
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

This is from my history previously created file as instructions above:
  432  sudo dpkg --set-selections < ubuntu-filesport2010Mar
  434  sudo apt-get -y update
  435  sudo apt-get update
  436  sudo apt-get dselect-upgrade
  437  history

When I installed Karmic to my desktop I tried to do as much from command line as possible and then saved history. I then used that history to help me install to my portable. Next I plan to convert history to several bash files to automate it.

---

### Post by funkyade on 2010-04-01
Thank you.

I googled again just now before I read your post and found this link (I couldn't find anything before weirdly) - 

[http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/](http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/)

I've managed to do it successfully between two 32bit machines, just need to replicate this on the 64bit ones.

on source machine -

```
dpkg --get-selections | grep -v deinstall > packagelist.txt
cp /var/cache/apt/archives/*deb 32bitpackages/
```

the cp is there to save downloading all the same packages again. The process is the same for the 64bit clone. I'm using a USB stick to store the list and packages...

then, on target machine - 

```
sudo aptitude update; sudo aptitude dist-upgrade; dpkg --set-selections < packagelist.txt
sudo cp 32bitpackages/*deb /var/cache/apt/archives/
sudo dselect
```

slight fiddle with dselect, but works for me...

However, I like the idea of using history... I will check out those other links too... Thanks again..

---

