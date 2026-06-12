---
title: "after upgradeing from 9.04 to karmik 9.10 all I get is a shall prompt"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by hogar.strashni on 2010-03-24
Hello.
I should mention that I'm quite a newbie, and that being terse haven't ever been in the list of my virtues. Still, I tried so many things, that this post couldn't possibly be shorter then it is.

Yesterday I upgraded my Kubuntu from 9.04 to 9.10 using adept. During upgrade I accepted everything that was offered including (one)new configuration file for I don't know what. After reboot I still had **grub1**, after trying regular boot system froze with error message that ***usplash process doesn't exist*** or so; briefly, only recovery mode worked properly. I think I entered clean option accidentally, if not, I haven't done anything special, yet after n-th reboot usplash problem disappeared, but I had another freezing screen, with something like:
> mount: proc already mounted on /proc
mount: UUID=d6163745-e30e-4c00-b158-66e46d40b1a8 already mounted on /home
mount: /dev/scd0 already mounted on /media/cdrom0
mount: /dev/sda1 already mounted on /mnt/podaci
mount: you didn't specify a filesystem type for /dev/sdc1
       I will try all types mentioned in /etc/filesystems or /proc/filesystems
Trying fuseblk
ip address 192.168.1.5 override specified
ip address specified explicitly
mount error(113): No route to host
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
plus it said it cannot mount everything from fstab. Problem was partition from another computer that was smbfs, which is truly not reachable right now. Someone said it's problem with mountall.

I tried solutions I found here:
1. provided by @kentaur

mount -o remount,rw /
sudo dpkg --configure -a

2. provided by @danlea

mount -n -o remount,rw /
mount -v -a
swapon -v -a
apt-get -f install
apt-get upgrade

I'm writing both, because I did both.

after typing **apt-get upgrade** I was in a deadloop with message 
> Reading package lists...
Building dependency tree...
Reading state information...
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  kdebase-workspace-dev: Depends: kdebase-workspace-libs4+5 (= 4:4.2.2-0ubuntu2) but 4:4.3.5-0ubuntu1~karmic1 is installed
                         Depends: libkwineffects1 (= 4:4.2.2-0ubuntu2) but 4:4.3.5-0ubuntu1~karmic1 is installed
                         Depends: libkdecorations4 (= 4:4.2.2-0ubuntu2) but 4:4.3.5-0ubuntu1~karmic1 is installed
I tried this loop twice then I tried one more thing I (think I)saw in the next few lines that are not displayed here **apt-get -f upgrade**. It ended up with recovery mode not working properly(only resume was possible), and regular boot ending in shell prompt. When I commanded startx from root kde started my last session(with some error messages immediately covered with firefox window). Mouse and keyboard were dead! Hard reset, logging to my home and startx led me to karmik kde login menager, and again that was dead end, because keyboard and mouse were dead!

Thanks in advance [-o<
Hogar

_It REALLY would help me a lot if anybody could, at least, solve the problem with **unmet dependencies**, and tell what went wrong._

PS. Isn't ubuntu suppose to resolve dependencies automatically?!?! :?

Do you need my dmesg report

---

### Post by lemming465 on 2010-03-28
> Yesterday I upgraded my Kubuntu from 9.04 to 9.10 using adept. 
I haven't tried that, but a more typical upgrade path would be *sudo update-manager -c* from a Konsole terminal window.  Distribution upgrades have some more complicated behaviors to work through than simple package updates.

First, check that the APT configuration file /etc/apt/sources.list has lines containing "karmic" rather than "jaunty".  If not, a quick workaround is:```
sudo -i
cd /etc/apt
perl -p -i.bak -e 's/jaunty/karmic/;' sources.list
```
It's OK if some commented out lines (starting with '#' or '##') have jaunty in them, but you need 12-18 "deb" and "deb-src" repository definitions specifying karmic, too.  On the ubuntu/kubuntu 9.10 system I'm typing this from I've got> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse


Next, before trying to run package upgrades, you need to make sure you have updated the package and dependency lists.  So make your next try```

sudo -i
apt-get update  # very important
apt-get upgrade --fix-broken
```
Dependency resolution by APT doesn't work if you don't feed it the right data.

---

### Post by hogar.strashni on 2010-03-31
I couldn't find "thanks" option on this forum, so I have to do it this way. Thank you @leming465 ! That was one good reply! You left nothing undefined, even coments were explained, just in case. Unfortunately :( I needed my computer desperately, I managed to save my data and formated the hard drive, so we'll never know if any of the possible solutions to my problem had been correct, though I have some doubts. I tried to boot from karmik live CD, and it stuck as well. I'm leaving possibility that some piece of hardware, of my aged 1.5GHz pentium4 from the very begining of the century, is not supported anymore.

Thanks!

---

