---
title: "Stuck in an upgrade loop..."
date: 2020-07-27
forum: Installation &amp; Upgrades
---

### Post by mentalfoto on 2020-07-27
Trying to upgrade Ubuntu from 19.10 to 20.04 I seem to be stuck in a feedback loop. Searching the web for a week I can't seem to find a fix that works.

```
1 package can be upgraded. Run 'apt list --upgradable' to see it.
mike@ToshibaBlack:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libsnmp30
0 upgraded, 0 newly installed, 0 to remove and [COLOR=#ff0000]1 not upgraded[/COLOR].
```

When I try to run the version upgrade it wants me to do all the updates to the current version first, but when I run the command, it just tells me one is held back and I can't find the magic command to get it to upgrade this one straggler so I can do the distro upgrade...

Here's the complete loop I'm in. The libsmap30 whatever it is never upgrades nor do I know how to reinstall any dependencies it needs.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
```
mike@ToshibaBlack:~$ sudo apt update
Ign:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty InRelease
Hit:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty Release                       
Hit:3 [http://ppa.launchpad.net/nemh/systemback/ubuntu](http://ppa.launchpad.net/nemh/systemback/ubuntu) xenial InRelease         
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan InRelease
Hit:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates InRelease
Hit:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-backports InRelease
Hit:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-security InRelease
Hit:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-proposed InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
mike@ToshibaBlack:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libsnmp30
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
mike@ToshibaBlack:~$ sudo apt install update-manager-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager-core is already the newest version (1:19.04.8.1).
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
mike@ToshibaBlack:~$ sudo do-release-upgrade
Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
[http://www.ubuntu.com/releaseendoflife](http://www.ubuntu.com/releaseendoflife)


Please install all available updates for your release before upgrading.
```
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

I'm totally stuck. Help!

---

### Post by Paddy Landau on 2020-07-27
You need to complete the updates before your upgrade (as I believe you already know).

Try these commands in order.
```
sudo apt --fix-broken install
sudo dpkg --configure --pending
sudo apt update
sudo apt upgrade
sudo apt full-upgrade
```
I suspect that the last command is probably the "magic command", but please run the commands in order.

If that works, run [FONT=lucida console]do-release-upgrade[/FONT] again. If you still have errors, post back with the errors.

---

### Post by Impavidus on 2020-07-27
Do you use any third-party software sources? If the above commands don't work, show the output of```
apt-cache policy libsnmp30
```

---

### Post by mentalfoto on 2020-07-27
Well, I lost the code of what fixed it, but here's the skinny.
None of the stuff like
sudo apt --fix-broken install
sudo dpkg --configure --pending
sudo apt update
sudo apt upgrade
sudo apt full-upgrade


worked. I tried things like guessing a command it wanted "sudo apt update libsnmp30" and noodled away with little success until it told me the dependency of the bugger. I had a text doc open with the commands I was trying but inadvertently closed it, But it was a command to specifically update the library or package that thing was dependent on that cleared the "1 held back" that had the upgrade stuck in a loop. I wish I had that package name but the solution was like "sudo upgrade libsomething x.x.x" and it did and THEN the "apt ugrade command" would actually start downloading 20.04 

Sorry, I've use Ubuntu for years, I just never muck around in command line stuff and my grasp is rudimentary at best. I had been using like 14.04 with the Unity Desktop to do graphics in GIMP and INkscape and decided to upgrade and it's a mixed blessing. Being a former Macintosh guy from 30 years ago the Gnome interface still takes getting used to, much less command line stuff, but thanks for the help guys..

---

### Post by mentalfoto on 2020-07-27
Made it to 20.04 finally safe and sound!

---

