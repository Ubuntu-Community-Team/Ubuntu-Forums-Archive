---
title: "dpkg: error processing archive /var/cache/apt/locales"
date: 2015-10-08
forum: Installation &amp; Upgrades
---

### Post by android4682 on 2015-10-08
What ever I try to install I get this error message:

```

Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:

{A lot of packages with depends errors}

E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

And when I do
```
root@localhost:~# apt-get -f install
```

I get this:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  locales
The following packages will be upgraded:
  locales
1 upgraded, 0 newly installed, 0 to remove and 1260 not upgraded.
3 not fully installed or removed.
Need to get 0 B/3,924 kB of archives.
After this operation, 6,904 kB of additional disk space will be used.
Do you want to continue? [Y/n] ^C
root@localhost:/home/droid443/Downloads/git# cd ~
root@localhost:~# apt-get -f install
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  locales
The following packages will be upgraded:
  locales
1 upgraded, 0 newly installed, 0 to remove and 1260 not upgraded.
3 not fully installed or removed.
Need to get 0 B/3,924 kB of archives.
After this operation, 6,904 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Preconfiguring packages ...
(Reading database ... 190368 files and directories currently installed.)
Preparing to unpack .../locales_2.19-18_all.deb ...
Unpacking locales (2.19-18) over (2.13+git20120306-12.1) ...
dpkg: error processing archive /var/cache/apt/archives/locales_2.19-18_all.deb (--unpack):
 trying to overwrite '/usr/sbin/validlocale', which is also in package libc-bin 2.19-0ubuntu6.6
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/locales_2.19-18_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So what can I do to fix this?

I'm running Ubuntu 14.04 LTS 64-bit (Server) with GNOME.

---

### Post by v3.xx on 2015-10-08
Try cleaning the cache.

```
sudo apt-get clean && sudo apt-get update
```

---

### Post by android4682 on 2015-10-08
> **v3.xx said:**
> Try cleaning the cache.

```
sudo apt-get clean && sudo apt-get update
```

Already tried, I tried again but still the same error.

---

### Post by v3.xx on 2015-10-08
Is this a possibility?

[http://askubuntu.com/questions/573720/ubuntu-14-04-server-upgrade-error](http://askubuntu.com/questions/573720/ubuntu-14-04-server-upgrade-error)

[locales_2.19-18_all.deb]("https://www.google.com/search?client=ubuntu&channel=fs&q=locales_2.19-18_all.deb&ie=utf-8&oe=utf-8")

---

### Post by Bashing-om on 2015-10-08
android4682; Yukkie poo ...

@ v3.xx :)
We meet again ole buddy .

Has this system ever seen an update ?
> 
1 upgraded, 0 newly installed, 0 to remove and [color=red]1260 not upgraded[/color].

Try and see what results:
```

sudo apt update
sudo apt full-upgrade

```

As a 1st approximation to get to the bull's eye.

Depending on what the package manager advises is what is to be done next.

[INDENT][INDENT]a happy package manager
[INDENT][INDENT][INDENT]is a happy system
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by v3.xx on 2015-10-08
Nice catch Bashing, missed that.

---

### Post by Bashing-om on 2015-10-08
> **v3.xx said:**
> Nice catch Bashing, missed that.

Hey, and extra set of eyes can be a good thing .. look at all the times you have seen where I did not.

[INDENT][INDENT]just goes to prove
[INDENT][INDENT][INDENT]we are all in this together
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

