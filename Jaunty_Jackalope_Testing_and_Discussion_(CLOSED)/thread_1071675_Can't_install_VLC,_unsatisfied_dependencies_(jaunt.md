---
title: "Can't install VLC, unsatisfied dependencies (jaunty)"
date: 2009-02-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Ben Page on 2009-02-16
Got some problems installing the VLC player in Jaunty Jackalope - Kubuntu. multiverse repositories are enabled, have added ppa repository, Adept finds the VLC player, but when the download completes I get an error about dependencies. Tried apt-get, too, same story, tried apt-get install -f, no go. Is it posible to install VLC in Kubuntu at all?

---

### Post by zvacet on 2009-02-16
Yes it is posible to install VLC in Kubuntu.Did you try

```
sudo dpkg --configure -a
```

---

### Post by Ben Page on 2009-02-16
I think I tried that, too, and now I tried it again and I got this:
```
ben@ben:~$ sudo dpkg --configure -a
[sudo] password for ben:
dpkg: dependency problems prevent configuration of vlc-nox:
 vlc-nox depends on libvlc2 (>= 0.9.1); however:
  Package libvlc2 is not installed.
 vlc-nox depends on libvlccore0 (>= 0.9.1); however:
  Package libvlccore0 is not installed.
dpkg: error processing vlc-nox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on vlc-nox (= 0.9.8a-1ubuntu3); however:
  Package vlc-nox is not configured yet.
 vlc depends on libvlccore0 (>= 0.9.1); however:
  Package libvlccore0 is not installed.
dpkg: error processing vlc (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 vlc-nox
 vlc

```

---

### Post by Crafty Kisses on 2009-02-16
Run the following command:
```
sudo apt-get update
```
Then try installing the following package:
```
sudo apt-get install libvlc2
```
Once you have done that, try reinstalling VLC:
```
sudo apt-get install vlc
```

---

### Post by Ben Page on 2009-02-16
No go, yes that is a logical step, but I got this:
```
ben@ben:~$ sudo apt-get install libvlc2
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libvlc2: Depends: libvlccore0 (>= 0.9.1) but it is not going to be installed
  vlc: Depends: libvlccore0 (>= 0.9.1) but it is not going to be installed
  vlc-nox: Depends: libvlccore0 (>= 0.9.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Also tried to install libvlccore0 and got this:
```
ben@ben:~$ sudo apt-get install libvlccore0
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  vlc-nox: Depends: libvlc2 (>= 0.9.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by Ben Page on 2009-02-16
Bump...:popcorn:

---

### Post by mkvnmtr on 2009-02-16
When I saw your post I started my 9.04 ubuntu and installed vlc and the package you are having problems with. It must conflict with something on Kubuntu. You know they have a forum for 9.04 you might get better answers on?

---

### Post by Ben Page on 2009-02-16
> **mkvnmtr said:**
> When I saw your post I started my 9.04 ubuntu and installed vlc and the package you are having problems with. It must conflict with something on Kubuntu. You know they have a forum for 9.04 you might get better answers on?

Yeah, well I guess ill have to register there, I never had any problems vith VLC in Ubuntu, but I had similar problems with Kubuntu 8.10 also. Thought this community would know how to solve the issue, because its the best! But sadly Ubuntu orientated...Thanx anyway guys!

---

### Post by dmizer on 2009-02-16
As Jaunty is certainly not an "Absolute Beginners" OS, I've moved this to the Jaunty testing section.

Thank you. :)

---

### Post by cariboo on 2009-02-16
Never mind

---

### Post by mkvnmtr on 2009-02-16
Don't give up. Remember they are working on it and I recieve 15 to 60 updates every day. Sometimes I have something like that one day and in a couple of days it is resolved.

---

### Post by ronacc on 2009-02-16
try this , first make sure your repos are uptodate  "sudo apt-get update" 
then open synaptic , I dont remember if its installed by default in kubuntu if not install it . check what version of vlc you are showing , I have 0.9.8a-1ubuntu3 . now one at a time install in this  order .
1 vlc-data
2 libvlccore0
3 libvlc2
4 vlc-nox
5 vlc 
if something fails to install click on the details button in the dialog box to see why .

---

### Post by tqft on 2009-02-18
One thing you might try without doing much if any damage is 
sudo ldconfig

This basically looks for and updates exectuables.

It is possible the vlc components are installed and the system is not seeing them - ldconfig should fix that if it is the problem

[http://linux.die.net/man/8/ldconfig](http://linux.die.net/man/8/ldconfig)
"ldconfig creates the necessary links and cache to the most recent shared libraries found in the directories specified on the command line, in the file /etc/ld.so.conf, and in the trusted directories (/lib and /usr/lib). The cache is used by the run-time linker, ld.so or ld-linux.so. ldconfig checks the header and filenames of the libraries it encounters when determining which versions should have their links updated. "

---

### Post by n3had on 2009-02-18
Brother i had a similar problem with different dependencies and i finally succeeded in installing VLC after this 


```
sudo aptitude install vlc
```

---

### Post by chamithal on 2009-04-06
> **Codename said:**
> Run the following command:
```
sudo apt-get update
```
Then try installing the following package:
```
sudo apt-get install libvlc2
```
Once you have done that, try reinstalling VLC:
```
sudo apt-get install vlc
```

thanks mate... helped me for Ubuntu 9.04 :)

---

