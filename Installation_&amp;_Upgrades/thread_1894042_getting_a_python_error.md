---
title: "getting a python error"
date: 2011-12-11
forum: Installation &amp; Upgrades
---

### Post by TheRacerX on 2011-12-11
ive noticed everytime i remove or install something on my computer i get this error in the terminal could someone tell me what it is or how to fix it?


INFO: using unknown version '/usr/bin/python2.7' (debian_defaults not up-to-date?)

this is the error

---

### Post by papibe on 2011-12-11
It looks like a version mismatch.

Which version of Ubuntu are you using?
Have you installed a newer Python version?

Regards.

---

### Post by TheRacerX on 2011-12-11
im running Ubuntu 10.10 Maverick Meerkat 32bit and i dont remember ever upgrading the python stuff, thats why im confused

---

### Post by papibe on 2011-12-11
It looks that Maverick should be using [v2.6]("http://packages.ubuntu.com/maverick/python"), and from natty and above [v2.7]("http://packages.ubuntu.com/natty/python").

Could you post the result of this command:
```
apt-cache policy python
```
Regards.

---

### Post by TheRacerX on 2011-12-11
heres what i get 


oddball@Cunningham:~$ apt-cache policy python
python:
  Installed: 2.6.6-2ubuntu2
  Candidate: 2.6.6-2ubuntu2
  Version table:
 *** 2.6.6-2ubuntu2 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/main i386 Packages
        100 /var/lib/dpkg/status
     2.6.6-2ubuntu1 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/main i386 Packages

---

### Post by papibe on 2011-12-11
That is what it should be.

Have you added a ppa to your sources? Are other versions of python installed?

Could you post the result of these commands?
```
python --version

whereis python

which python

ls -l $(which python)
```
Regards.

---

### Post by TheRacerX on 2011-12-11
here is everything that you asked for 

oddball@Cunningham:~$ python --version
Python 2.6.6

oddball@Cunningham:~$ whereis python
python: /usr/bin/python2.7 /usr/bin/python /usr/bin/python2.6 /etc/python2.7 /etc/python /etc/python2.6 /usr/lib/python2.7 /usr/lib/python /usr/lib/python2.6 /usr/local/lib/python2.7 /usr/local/lib/python2.6 /usr/include/python2.7 /usr/include/python2.6_d /usr/include/python2.6 /usr/share/python /usr/share/man/man1/python.1.gz

oddball@Cunningham:~$ which python
/usr/bin/python

oddball@Cunningham:~$ ls -l $(which python)
lrwxrwxrwx 1 root root 9 2011-12-05 10:02 /usr/bin/python -> python2.6

---

### Post by papibe on 2011-12-11
Somehow python2.7 it is also installed. If you don't installed yourself, then probably was a requisite from a ppa you added.

You may remove it using 'Synaptic', but my guess is it may damage the software you installed using the ppa.

Which ppa's have you added?

Regards.

---

### Post by TheRacerX on 2011-12-11
how do i make a list do i just go sudo apt-get update then copy the entire list to here?

---

### Post by papibe on 2011-12-11
I believe this command will show all ppas you added:
```
ls /etc/apt/sources.list.d/
```
(except the ones you added editing the source list manually).
Regards.

---

### Post by TheRacerX on 2011-12-11
here you go 


oddball@Cunningham:~$ ls /etc/apt/sources.list.d/
am-monkeyd-nautilus-elementary-ppa-maverick.list
am-monkeyd-nautilus-elementary-ppa-maverick.list.save
amsn-daily-ppa-maverick.list
amsn-daily-ppa-maverick.list.save
banshee-team-ppa-maverick.list
banshee-team-ppa-maverick.list.save
chromium-daily-ppa-maverick.list
chromium-daily-ppa-maverick.list.save
cinelerra-ppa-ppa-maverick.list
cinelerra-ppa-ppa-maverick.list.save
elegant-gnome-ppa-maverick.list
elegant-gnome-ppa-maverick.list.save
emesene-team-emesene-stable-maverick.list
emesene-team-emesene-stable-maverick.list.save
gnome3-team-gnome3-maverick.list
gnome3-team-gnome3-maverick.list.save
gnome3-team-gnome3-oneiric.list
gnome3-team-gnome3-oneiric.list.save
konradgraefe-pidgin-plugins-maverick.list
konradgraefe-pidgin-plugins-maverick.list.save
libreoffice-ppa-maverick.list
libreoffice-ppa-maverick.list.save
medibuntu.list
medibuntu.list.save
mozillateam-firefox-next-maverick.list
mozillateam-firefox-next-maverick.list.save
pidgin-developers-ppa-maverick.list
pidgin-developers-ppa-maverick.list.save
ricotz-testing-maverick.list
ricotz-testing-maverick.list.save
sevenmachines-flash-maverick.list
sevenmachines-flash-maverick.list.save
sunab-kdenlive-release-maverick.list
sunab-kdenlive-release-maverick.list.save
swiftfox.list
swiftfox.list.save
team-xbmc-ppa-maverick.list
team-xbmc-ppa-maverick.list.save
telepathy-ppa-maverick.list
telepathy-ppa-maverick.list.save
transmissionbt-ppa-maverick.list
transmissionbt-ppa-maverick.list.save
tualatrix-ppa-maverick.list
tualatrix-ppa-maverick.list.save
ubuntu-tweak-stable.list.save
ubuntu-tweak-testing-ppa-maverick.list
ubuntu-tweak-testing-ppa-maverick.list.save
ubuntu-x-swat-x-updates-maverick.list
unity-2d-team-unity-2d-daily-maverick.list
unity-2d-team-unity-2d-daily-maverick.list.save
unity-ppa-maverick.list
unity-ppa-maverick.list.save

some of these i dont have enabled or ive removed but they still seem to be showing up on this list.

---

### Post by papibe on 2011-12-11
Wow, that's a lot ;)  I can only guess... may be the gnome3 stuff, but it may not matter if deleted then.

Try this to clean up your sources:
```
sudo apt-get autoremove
sudo apt-get autoclean
```
Regards.

---

### Post by TheRacerX on 2011-12-11
it didnt do anything wasnt anything to clean up and yeah i know i like to test and play around with programs learn how they work and how to improve upon them stuff like that

---

### Post by papibe on 2011-12-11
Sorry if my previous post wasn't clear enough.

Those commands don't clean your sources, but remove packages that don't have dependents. For example:

I installed synapse (the launcher not Synaptic the package manager) in my 10.04 desktop from a ppa. synapse's dependencies includes the zeitgeist package, so zeitgeist is installed too. If I remove synapse (almost for sure) you won't be deleting zeitgeist. The way the last one gets removed is by doing:
```
sudo apt-get autoremove
```

In your case, if 2.7 was just a dependency that had to be made, but it is no longer supporting any package, that command could resolve your problem.

In any case, let's try to figure out how python2.7 got installed.

In order to check what are python2.7's dependents packages:

- Open Synaptic.
- Search for python2.7.
- Right click on it, and select properties.
- Select the Dependencies tab.
- Select 'Dependent Packages' on the selection bar.

If some of those packages are still installed, you won't be able to remove python2.7 without breaking dependencies.

Is that more clear?
Regards.

---

