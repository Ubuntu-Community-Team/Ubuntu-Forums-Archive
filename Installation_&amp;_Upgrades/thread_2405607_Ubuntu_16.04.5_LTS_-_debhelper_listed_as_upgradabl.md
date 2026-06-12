---
title: "Ubuntu 16.04.5 LTS - debhelper listed as upgradable but won't upgrade"
date: 2018-11-08
forum: Installation &amp; Upgrades
---

### Post by Dan L. on 2018-11-08
My issue is that if I run ```
sudo apt update && sudo apt upgrade
``` from the terminal, it shows that I have 1 package that can be upgraded, but it won't upgrade it (and it isn't held as far as I can tell).

I've attached my attempts to fix this situation and output from the terminal here:

```
[COLOR="#008000"]daniel@desktop:~$ sudo apt update[/COLOR]

[COLOR="#0000FF"]...(all sources fetched appropriately)...
Fetched 323 kB in 5s (54.9 kB/s) 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.[/COLOR]

[COLOR="#008000"]daniel@desktop:~$ sudo apt upgrade[/COLOR]

[COLOR="#0000FF"]Reading package lists... Done
Building dependency tree 
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/COLOR]

[COLOR="#008000"]daniel@desktop:~$ sudo apt full-upgrade[/COLOR]

[COLOR="#0000FF"]Reading package lists... Done
Building dependency tree 
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/COLOR]

[COLOR="#008000"]daniel@desktop:~$ sudo apt list --upgradable -a[/COLOR]

[COLOR="#0000FF"]Listing... Done
debhelper/xenial,xenial 11.5.1ppa1~ubuntu16.04.4 all [upgradable from: 10.2.2ubuntu1~ubuntu16.04.1]
debhelper/xenial-backports,xenial-backports,now 10.2.2ubuntu1~ubuntu16.04.1 all [installed,upgradable to: 11.5.1ppa1~ubuntu16.04.4]
debhelper/xenial,xenial 9.20160115ubuntu3 all[/COLOR]

[COLOR="#008000"]daniel@desktop:~$ sudo apt install debhelper[/COLOR]

[COLOR="#0000FF"]Reading package lists... Done
Building dependency tree 
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 debhelper : Depends: dh-autoreconf (>= 17~) but 12~ubuntu16.04.1 is to be installed
 Depends: dh-strip-nondeterminism (>= 0.028~) but 0.015-1 is to be installed
E: Unable to correct problems, you have held broken packages.[/COLOR]

```

When I then also check/manually install [COLOR="#0000FF"]dh-autoreconf[/COLOR] and [COLOR="#0000FF"]dh-strip-nondeterminism[/COLOR], it says they are both the newest versions already...

---

### Post by ajgreeny on 2018-11-08
Have you enabled any non-standard repos?

You have not shown the full output of the **sudo apt update** command which might give us some better clues than we have so far, so please show that complete output. In my Xubuntu 18.04 install the versions of those two problem packages are correct as required according to your terminal output shown at the bottom of your code box but I'm not on 16.04 so I'm unable to check versions in that.

Do you really need the **debhelper** package?  I am not aware that I have ever had it in any of my *ubuntu installs, and it's certainly not in any that I am currently running.

---

### Post by Dan L. on 2018-11-08
Thanks ajgreeny!  I just assumed it was somehow related to base Ubuntu packages since it had to do with building Debian packages (and I hadn't installed anything for that purpose, or at least thought I hadn't).  

But, when you asked me this, I looked up the possible available versions of debhelper (from the repos I had set up) using *apt-show-versions*.  Then realized that it was a new available version from my Neovim PPA.  I actually don't really use Neovim much, so I just uninstalled Neovim and the repo and that solved the problem.

Thank you for pointing me in the right direction!  And I'll definitely keep this in mind, and make sure to show all the repos, if I run into any problems in the future.

---

### Post by ajgreeny on 2018-11-09
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

