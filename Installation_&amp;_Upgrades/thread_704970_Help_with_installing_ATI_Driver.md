---
title: "Help with installing ATI Driver"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by Tohdman on 2008-02-22
I have had a lot of problems installing the driver for my ATI Radeon 9550 in Ubuntu Gutsy and I have given up many times trying to install it. But now I am trying to do it again, but I will just skip right to my situation,

I am following [this](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) guide. Everything went fine until I had to install the "fglrx-kernel-source" .deb file. This is what I   entered into the terminal and what I got back:
[I]todd@todd-desktop:~/Desktop$ sudo dpkg -i fglrx-kernel-source_8.455.2-0ubuntu1_i386.deb 
(Reading database ... 91531 files and directories currently installed.)
Preparing to replace fglrx-kernel-source 8.455.2-0ubuntu1 (using fglrx-kernel-source_8.455.2-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-kernel-source ...
dpkg: dependency problems prevent configuration of fglrx-kernel-source:
 fglrx-kernel-source depends on dkms; however:
  Package dkms is not installed.
dpkg: error processing fglrx-kernel-source (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx-kernel-source[/I]

I have looked around alot and haven't found anymore else with this problem. I would really appreciate any help that you guys can offer.

---

### Post by strick242 on 2008-02-22
try sudo apt-get install dkms
then try your install again

---

### Post by Tohdman on 2008-02-22
> **strick242 said:**
> try sudo apt-get install dkms
then try your install again
This is what I get back in the terminal when I enter that:
[i]todd@todd-desktop:~$ apt-get install dkms
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?[/i]

There is something keeping me from using that "/var/lib/dpkg/" directory. I read somewhere that the "lock" file inside the dpkg folder that does this. Any ideas on what to do now?

---

### Post by lsmobrian on 2008-02-22
Forgot sudo ... ie "are you root"

---

### Post by Tohdman on 2008-02-24
> **lsmobrian said:**
> Forgot sudo ... ie "are you root"
When I put "sudo apt-get install dkms" I get this:

[i]Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  dkms: Depends: gawk but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/i]
And when I run "apt-get -f instal" I get this again:

[i]E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?[/i]

And if I run "sudo apt-get install gawk" I get this again:

[i]Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  fglrx-kernel-source: Depends: dkms but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/i]

Any ideas now?

---

### Post by Tohdman on 2008-02-24
What if I were to manually install dkms somehow?

---

### Post by dstew on 2008-02-24
> nd when I run "apt-get -f instal" I get this again:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?Try ```
sudo apt-get -f install
```

---

