---
title: "packages don't install?"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by siman on 2007-07-04
I have a strange problem on my ibook g3 with the inofficial (...) newest ubuntu. When I install packages with apt-get, they just don't seem to get installed. For example:

```

simon@fatwhite:~$ sudo apt-get install wesnoth-all
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wesnoth-all is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
simon@fatwhite:~$ wesnoth
The program 'wesnoth' is currently not installed.  You can install it by typing:
sudo apt-get install wesnoth
Make sure you have the 'universe' component enabled
bash: wesnoth: command not found
simon@fatwhite:~$ locate wesnoth
/usr/share/app-install/desktop/wesnoth.desktop

```

I also tried find / -name wesnoth with no results except the desktop shortcut.

any ideas? This seems to be the problem with a lot of games (empire, fortz). other things like SVN install without a problem.

---

### Post by spd106 on 2007-07-05
What happens when you run this?
```
sudo apt-get --reinstall install wesnoth-all
```
or
```
sudo apt-get install wesnoth wesnoth-data wesnoth-all
```

---

### Post by siman on 2007-07-07
thanks for the reply, I tried both commands, but it didn't seem to help. I would guess this is PPC specific, since on my Intel machine - same ubuntu - wesnoth installed with no probs.

```

simon@fatwhite:~$ sudo apt-get --reinstall install wesnoth-all
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 6 not upgraded.
Need to get 0B/80.4kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 163228 files and directories currently installed.)
Preparing to replace wesnoth-all 1.2.3-0ubuntu1 (using .../wesnoth-all_1.2.3-0ubuntu1_powerpc.deb) ...
Unpacking replacement wesnoth-all ...
Setting up wesnoth-all (1.2.3-0ubuntu1) ...
simon@fatwhite:~$ wesnoth
The program 'wesnoth' is currently not installed.  You can install it by typing:
sudo apt-get install wesnoth
Make sure you have the 'universe' component enabled
bash: wesnoth: command not found

```
and
```

simon@fatwhite:~$ sudo apt-get install wesnoth wesnoth-data wesnoth-all
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wesnoth is already the newest version.
wesnoth set to manual installed.
wesnoth-data is already the newest version.
wesnoth-data set to manual installed.
wesnoth-all is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
simon@fatwhite:~$ uname -a
Linux fatwhite 2.6.20-16-powerpc #3 Thu Jun 7 19:32:55 UTC 2007 ppc GNU/Linux


```

Should I try installing the .debs from the project page? But this would be not-so-cool

---

### Post by bmorency on 2007-07-07
in your initial post the error mesage said to make sure you have the 'universe' repo enabled. do you have that enabled?

---

### Post by spd106 on 2007-07-07
This is rather strange. Have you refreshed the package lists recently? Are those 6 held back upgrades related to wesnoth? Try re-installing the other packages as well, not just wesnoth-all.

You might have to resort to downloading from the Debian archives or failing that compile yourself.

---

