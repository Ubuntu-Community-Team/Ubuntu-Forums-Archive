---
title: "How do I apply updates and packages to a non-networked PC?"
date: 2006-03-17
forum: Installation &amp; Upgrades
---

### Post by backportmoose on 2006-03-17
I've just installed Ubuntu 5.10 on a dialup-only (56k) PC. The dialup is far too slow for e.g. Synaptic, to download specific packages or regular updates.

Please can anyone tell me how I can achieve the following:

1) Copy the latest 5.10 updates onto CD (from my broadband PC),
2) copy any specific software packages AND their required libraries onto CD (as above),
3) Install the updates & packages from the CD onto the dialup PC?

This would be very helpful to the masses of people who would benefit from using Ubuntu (etc) but who do not yet have broadband. \\:D/

---

### Post by magisterludi on 2006-03-18
I did not try this. I do not think it is the best solution(since you need to have ubuntu/debian installed on the other machine too). Just my first thought.
So be careful.
This one basically tries to make the broadband ubuntu believe it is the dial up ubuntu to make
it download the relevant updates.

You may try to dump all the information about which packages
are installed on your system by
```

dpkg --get-selections > /tmp/installed_packages_target

```
and backup the /etc/apt/sources.list too

put that file on the other machine and do a backup of the targets
selections.
```

dpkg --get-selections > /tmp/installed_packages_backup

```
then cheat this ubuntu to believe the packages from the other
installation are installed:

```

cat installed_packages_target | dpkg --set-selections

```
backup the sources.list of this machine and overwrite
it with the target ones.
do a ```
apt-get clean
``` to clean the archive
then just download the updates:
```

apt-get --download-only dist-upgrade

```
downloaded packages will be in /var/cache/apt/archives
write them on a cd and install them with ```
dpkg -i *
```

Then you have to turn the broadband machine back to its original state.
You may want to write a bash script for that.

---

### Post by Bartender on 2006-03-19
A few questions -
#1 Do you have access to broadband at school, work, the library, a friend's house, etc.?
#2 Does yur Linux PC have a network card or onboard networking, & can you go in to Administration > Networking to enable it?
#3 If yes to above, how awkward would it be to bundle up your PC, mouse, & keyboard and take it to the broadband?

I don't know how often this is going to work for other people, but that's what I did.  Brought my PC in to work on a slow night.  Plugged in the ethernet cable BEFORE turning the PC on.  Turned it on.  When I clicked on the Firefox icon it went online as if it'd been doing that all its life.

---

### Post by vinodis on 2006-06-21
[http://ubuntuforums.org/showthread.php?t=183933&page=5](http://ubuntuforums.org/showthread.php?t=183933&page=5)
Try this pls.

---

