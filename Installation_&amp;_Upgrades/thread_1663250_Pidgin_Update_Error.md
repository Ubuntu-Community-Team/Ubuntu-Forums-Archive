---
title: "Pidgin Update Error"
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by teejay17 on 2011-01-09
Hi all, did an update/upgrade and received this message:

```
The following packages will be upgraded:
  pidgin-data 
The following partially installed packages will be configured:
  pidgin 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8,650kB of archives. After unpacking 463kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 296797 files and directories currently installed.)
Preparing to replace pidgin-data 1:2.7.7-1ubuntu0+pidgin1.10.04 (using .../pidgin-data_1%3a2.7.9-1ubuntu0+pidgin1.10.04_all.deb) ...
Unpacking replacement pidgin-data ...
dpkg: error processing /var/cache/apt/archives/pidgin-data_1%3a2.7.9-1ubuntu0+pidgin1.10.04_all.deb (--unpack):
 trying to overwrite '/usr/share/pixmaps/pidgin/protocols/48/facebook.png', which is also in package pidgin-facebookchat 0:1.68
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/pidgin-data_1%3a2.7.9-1ubuntu0+pidgin1.10.04_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of pidgin:
 pidgin depends on pidgin-data (>= 1:2.7.9); however:
  Version of pidgin-data on system is 1:2.7.7-1ubuntu0+pidgin1.10.04.
dpkg: error processing pidgin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pidgin
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
```
I then tried to uninstall Pidgin in the software centre, but it won't let me do that either, saying "The package system is broken."
Anyone have any suggestions as to how I should proceed? Should the broken package be fixed, or should I remove Pidgin completely? I think the simplest route should be to remove completely, but I'm curious what the experts think. 
Thanks in advance.

---

### Post by jmatthews13 on 2011-01-09
The issue here is with pidgin-facebookchat plugin, which has yet to be fixed.

Removing just pidgin-facebookchat is useless.

Quick solution is to make sure you've made a copy of your .purple folder (in case something goes wrong, though the folder should remain untouched), then remove pidgin via Synaptic or command line, then reinstall.

Hopefully FBChat plugin will be fixed soon.

---

### Post by teejay17 on 2011-01-09
Okay, thanks. I hope it gets fixed soon too!

---

### Post by teejay17 on 2011-01-09
What should I do as a next step? Should I run sudo apt-get install -f, or should I just wait for the fixes to come downstream? I tried to uninstall Pidgin all together, but I'm also prevented from doing this by unmet dependencies.

---

### Post by jmatthews13 on 2011-01-09
apt-get install -f won't fix the problem.

As long as you mark pidgin-data for removal instead of upgrade, along with all other pidgin packages (pidgin, pidgin-facebookchat, pidgin-ppa, etc.), they should all uninstall just fine.

---

### Post by teejay17 on 2011-01-09
> **jmatthews13 said:**
> apt-get install -f won't fix the problem.

As long as you mark pidgin-data for removal instead of upgrade, along with all other pidgin packages (pidgin, pidgin-facebookchat, pidgin-ppa, etc.), they should all uninstall just fine.

Thanks. I uninstalled it. I wonder if I should hold off reinstalling Pidgin and just use Empathy instead. The problem is, Empathy is just so *different*.

---

### Post by jmatthews13 on 2011-01-11
Nah, Pidgin itself runs fine. The only issue was the facebookchat plugin, which has tons of problems of its own!

---

### Post by teejay17 on 2011-01-11
> **jmatthews13 said:**
> Nah, Pidgin itself runs fine. The only issue was the facebookchat plugin, which has tons of problems of its own!

Well I completely removed Pidgin and Pidgin data, then downloaded the newest .deb from the Pidgin site, but I cannot install it anymore; I'm still getting warnings of broken dependencies (I'm on my work computer, so I can't replicate the exact warning at this time).

---

### Post by teejay17 on 2011-01-12
> **jmatthews13 said:**
> Nah, Pidgin itself runs fine. The only issue was the facebookchat plugin, which has tons of problems of its own!

Okay, i'll take your word for it--been using it for years and Pidgin has never let me down. 
However, I still have a weird Pidgin issue. When I try to reinstall Pidgin using the Ubuntu Software Centre, this happens: 

[http://img809.imageshack.us/f/screenshotyn.png/]("http://img809.imageshack.us/f/screenshotyn.png/")

and when I try to install from the newest .deb, this happens:

[URL="http://img828.imageshack.us/f/screenshot1jd.png/"]http://img828.imageshack.us/f/screenshot1jd.png/
[/URL]

No idea what could be causing this. Everything else works fine, updates, installing other packages.

---

### Post by teejay17 on 2011-01-23
Has anyone else encountered similar problems with Pidgin, such as the one described above? Is this a bug that should be reported somewhere?

---

### Post by isamudysan on 2011-02-03
i've been having the similar issues just the past few days after an update -- "broken," dependency issues, etc. just like the previous posts.

i just uninstall all of pidgin and haven't touched it since.  i do like it, and really need the FB plugin to stay in contact with my friends who is on FB every freaking day.

like everyone, i would like to know if there's a fix to the FB plugin (anytime soon...lol).

---

