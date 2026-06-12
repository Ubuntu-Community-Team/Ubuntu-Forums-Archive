---
title: "I have a problem in getting updates in ubuntu 9.04"
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by abhimanyu23 on 2011-06-11
I am trying to get a .rpm to .deb converter for ubuntu 9.04 but update is failing.here is the msg being displayed:
abhimanyu@abhimanyu-laptop:~$ sudo apt-get install alien
[sudo] password for abhimanyu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package alien


also the the system update is also failing .....
I hav newly installed 9.04 and would like to know if there is any system setting required for these updates or there is sum other problem.....??

will highly appreciate any help...

---

### Post by jocko on 2011-06-11
When support for ubuntu 9.04 ended in september 2010 the software repositories were moved to another server (old-releases.ubuntu.com), which is why you can't install anything.
Is there any reason you need to run 9.04? Otherwise you are probably better off using 11.04 (the latest release).

If you really need to run 9.04 despite it being unsupported you have to change your software sources to use the old-releases server. Note that you will not get any updates (except those that were released during the support lifetime of 9.04)...
This is one way of doing it:
1. Make a backup copy of your current sources.list (probably not needed, but just in case...). Open up a terminal, run this command:
```
cp /etc/apt/sources.list ~/sources.list.backup
```
2. Run this command:
```
gksudo gedit /etc/apt/sources.list
```
Replace the entire contents of the file with this:
```
[COLOR=Black]deb [/COLOR][COLOR=Black]http://old-releases.ubuntu.com/ubuntu/ [/COLOR][COLOR=Black]jaunty main restricted universe multiverse
[/COLOR][COLOR=Black]deb [/COLOR][COLOR=Black]http://old-releases.ubuntu.com/ubuntu/ [/COLOR][COLOR=Black]jaunty-updates main restricted universe multiverse[/COLOR]
[COLOR=Black]deb [/COLOR][COLOR=Black]http://old-releases.ubuntu.com/ubuntu/ [/COLOR][COLOR=Black]jaunty-security main restricted universe multiverse[/COLOR]
[COLOR=Black]#deb [/COLOR][COLOR=Black]http://old-releases.ubuntu.com/ubuntu/ [/COLOR][COLOR=Black]jaunty-proposed main restricted universe multiverse[/COLOR]
[COLOR=Black]#deb [/COLOR][COLOR=Black]http://old-releases.ubuntu.com/ubuntu/ [/COLOR][COLOR=Black]jaunty-backports main restricted universe multiverse[/COLOR]

```
Save and close the file.

Note that I left the last two lines (jaunty-proposed and jaunty-backports) inactive (the # before the text).
The backports repo contain packages that were added or updated from newer source code than the versions in the standard jaunty repos. It is probably safe to use this. If you want to use it, just remove the #.
The proposed repo contained updates that needed more testing before they were moved to the standard repos. If nothing was wrong with the packages, they have already been moved to the normal repos, so you probably want to keep this inactivated.


3. Run these commands:
```
sudo apt-get update
sudo apt-get upgrade
```
The first command downloads the lists of available packages from the server, the second command downloads and installs all updates that were released during jaunty's supported lifetime.
If you prefer using synaptic, the same can be accomplished by pressing the "reload" button and then "mark all upgrades" and "apply".

---

### Post by mörgæs on 2011-06-11
If you manage to get this working, you will have to do it again, since 9.10 is also unsupported. 

Have you thought of jumping straight to 10.10 or 11.04?

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

---

