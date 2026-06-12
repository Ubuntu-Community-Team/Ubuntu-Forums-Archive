---
title: "Screenlet"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by scoobyd on 2011-02-02
Hi,

I tried to install 'screenlet' via terminal but came up with this error message:


~$ sudo apt-get install screenlets
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 screenlets : Depends: python-rsvg but it is not installable or
                       python-gnome2-desktop but it is not installable
              Recommends: python-gtkmozembed but it is not installable or
                          python-gnome2-extras (< 2.19) but it is not installable
              Recommends: python-evolution but it is not installable or
                          python-gnome2-desktop but it is not installable
E: Broken packages


When I tried using the ubuntu software centre, it tells me that it can't be installed/removed until it's repaired. Everytime I click repair, the same message pops up time and time again.

Any idea how to fix this?

---

### Post by sikander3786 on 2011-02-03
Which version of Ubuntu is this? If 10.04, try this.

```
sudo aptitude install screenlets
```

If it is 10.10, please post the output of these commands.

```
cat /etc/apt
```

```
ls -l /etc/apt/sources.list.d
```

---

### Post by scoobyd on 2011-02-04
I'm on Ubunutu 10.10. The output is:


~$ cat /etc/apt
cat: /etc/apt: Is a directory
~$ ls -l /etc/apt/sources.list.d
total 28
-rw-r--r-- 1 root root 126 2011-01-31 16:48 bisigi-ppa-maverick.list.save
-rw-r--r-- 1 root root 176 2011-02-01 14:32 google-chrome.list
-rw-r--r-- 1 root root 176 2011-02-01 14:32 google-chrome.list.save
-rw-r--r-- 1 root root 134 2011-01-31 16:48 tiheum-equinox-maverick.list.save
-rw-r--r-- 1 root root  92 2011-02-01 14:32 tualatrix-ppa-maverick.list
-rw-r--r-- 1 root root  92 2011-02-01 14:32 tualatrix-ppa-maverick.list.save
-rw-r--r-- 1 root root 136 2011-02-01 14:32 ubuntu-wine-ppa-maverick.list

---

### Post by sikander3786 on 2011-02-04
Go to Software Center > Edit > Software Sources > Other Software Tab and disable all the repositories there for time being excluding the Canonical Partners ones. Then try,

```
sudo apt-get update && sudo apt-get install screenlets
```

If that doesn't solve the issue, please post the output of this command. (I mis-typed in my above post)

```
cat /etc/apt/sources.list
```

---

### Post by scoobyd on 2011-02-04
sudo apt-get update && sudo apt-get install screenlets
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_NZ
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_NZ
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 screenlets : Depends: python-rsvg but it is not installable or
                       python-gnome2-desktop but it is not installable
              Recommends: python-gtkmozembed but it is not installable or
                          python-gnome2-extras (< 2.19) but it is not installable
              Recommends: python-evolution but it is not installable or
                          python-gnome2-desktop but it is not installable
E: Broken packages

[CENTER]-----------------------------------------------------------------------[/CENTER]

cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse universe

---

### Post by sikander3786 on 2011-02-04
So you are missing some repositories in your sources.list.

Generate a new sources.list and replace your existing one with the new one. Then try installation again.

See here.

[http://ubuntu4beginners.blogspot.com/2011/01/restore-your-sources-list-to-defaults.html](http://ubuntu4beginners.blogspot.com/2011/01/restore-your-sources-list-to-defaults.html)

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by scoobyd on 2011-02-04
Thanks a lot sikander3786!

It worked. Screenlet is installing as I type :)

---

