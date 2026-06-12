---
title: "AAHHH What happened to Ubuntu!! (apt)"
date: 2005-06-14
forum: Installation &amp; Upgrades
---

### Post by crane on 2005-06-14
OK so I decide it's time to reinstall on my main computer.
So I install hoary, no problems.
Then sudo apt-get update
Then Apt-get upgrade
after that I get all kind of errors!!

> jason@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  cupsys-driver-gimpprint: Depends: libgimpprint1 (>= 4.2.7) but it is not installed
  gimp: Depends: gimp-data (= 2.2.2-1ubuntu5) but it is not installed
        Depends: libgimpprint1 (>= 4.2.7) but it is not installed
  gs-esp: Depends: libgimpprint1 (>= 4.2.7) but it is not installed
  ijsgimpprint: Depends: libgimpprint1 (>= 4.2.7) but it is not installed
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Unmet dependencies. Try using -f. 

Also tried installing nvidia
sudo apt-get install nvidia-glx

> jason@ubuntu:~$ sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  cupsys-driver-gimpprint: Depends: libgimpprint1 (>= 4.2.7) but it is not going to be installed
  gimp: Depends: gimp-data (= 2.2.2-1ubuntu5) but it is not going to be installed
        Depends: libgimpprint1 (>= 4.2.7) but it is not going to be installed
  gs-esp: Depends: libgimpprint1 (>= 4.2.7) but it is not going to be installed
  ijsgimpprint: Depends: libgimpprint1 (>= 4.2.7) but it is not going to be installed
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution). 

Man I need some Quake3!!!! Any Ideas on how to fix?

---

### Post by Xian on 2005-06-14
Two quick ideas:

1. Comment the line in your sources.list so that it appears: 
```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
```

2. Do the following commands in order:
```
$ sudo apt-get udpate
$ sudo apt-get -f install
$ sudo apt-get dist-upgrade
```

---

### Post by crane on 2005-06-15
I did used the -f switch and was able to install some things.
One question?
wouldn't the "sudo apt-get dist upgrade" take me to breezy?

---

### Post by bored2k on 2005-06-15
[QUOTE=crane]I did used the -f switch and was able to install some things.
One question?
wouldn't the "sudo apt-get dist upgrade" take me to breezy?[/QUOTE]
 Nope. YOu would have to change your repositories for that.

---

