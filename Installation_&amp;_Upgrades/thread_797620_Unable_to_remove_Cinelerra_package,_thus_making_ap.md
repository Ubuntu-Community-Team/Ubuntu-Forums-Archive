---
title: "Unable to remove Cinelerra package, thus making apt-get pointless"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by slackerwarenative on 2008-05-17
Hi.

I wanted to try out Cinelerra for editing a class movie project, and so I installed it. Cinelerra was only offer as source code, but the comunity verson, which is compiled for Ubuntu & includes updates/impovements was avalible at:
[HTML]http://cinelerra.org/[/HTML]
[http://cinelerra.org/getting_cinelerra.php#ubuntu]("http://cinelerra.org/getting_cinelerra.php#ubuntu")

I would have just compiled it, but since I am using Ubuntu, I figured I would see if there was a .deb available. I found one and added [http://repository.akirad.net](http://repository.akirad.net) to my repository. Then I reloaded Synaptic, installed it, and ran Cinelerra. Cinelerra was slightly slow, but there were no other configuration / install problems. It did not do exactly what I wanted, so I *attempted* to uninstall it through Synaptic. This apparently failed because there was an extra dependency that, although did not give me trouble in the install, realized that it could not be uninstalled. I though "Fine, it does not have to be installed", but "Opps... it crashed anyway." Now Apt-get is completely useless. I cannot install or uninstall anything, since it wants me to fix broken packages. Unfortunately, it crashes every time it tries to fix them. I REALLY don't want to reinstall the OS, since I might lose too much work, and the time it would take to back it up is pointless (compared to the time it *should* take to fix apt-get).

I have tried several methods, including:
```
$: sudo apt-get install -f
```
```
sudo dpkg -i --force-all Cinelerra
```
```
sudo synaptic
```
```
sudo dpkg-divert --rename --remove /usr/bin/Cinelerra
```
```
sudo aptitude
```

Is apt-get really that poorly written? I don't care if it leaves trace files, since I can remove them myself in a couple of minutes. Is there a file I can just manually edit to make apt-get be quite? :confused:

I am running:
Ubuntu 7.10 (gutsy)
Kernel Linux 2.6.22-14-generic
GNOME 2.20.1
Synaptic 0.60ubuntu5
Compiled all for x86, since this box is a 32bit x86 (P4 cpu)



Thank you for your help.

---

### Post by zvacet on 2008-05-17
```
sudo apt-get --purge remove package_name
```

```
sudo dpkg --remove --force-remove-reinstreq package_name
```

---

### Post by slackerwarenative on 2008-05-18
Thanks for the response zvacet, but no luck.

```

user@desktop:~$ sudo apt-get autoremove
[sudo] password for user:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  cinelerra
0 upgraded, 0 newly installed, 1 to remove and 26 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 23.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 177663 files and directories currently installed.)
Removing cinelerra ...
Description:    Ubuntu 7.10
locale "en_US.ISO-8859-15" not in archive
rm: cannot remove `/usr/bin/Cinelerra': No such file or directory
dpkg: error processing cinelerra (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 cinelerra
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

user@desktop:~$ sudo apt-get --purge remove cinelerra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  cinelerra
0 upgraded, 0 newly installed, 1 to remove and 26 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 23.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 177663 files and directories currently installed.)
Removing cinelerra ...
Description:    Ubuntu 7.10
locale "en_US.ISO-8859-15" not in archive
rm: cannot remove `/usr/bin/Cinelerra': No such file or directory
dpkg: error processing cinelerra (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 cinelerra
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

user@desktop:~$ sudo dpkg --remove --force-remove-reinstreq cinelerra
(Reading database ... 177663 files and directories currently installed.)
Removing cinelerra ...
Description:    Ubuntu 7.10
locale "en_US.ISO-8859-15" not in archive
rm: cannot remove `/usr/bin/Cinelerra': No such file or directory
dpkg: error processing cinelerra (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 cinelerra

```

I even tried adding a file called Cinelerra in /usr/bin

Can't I just manually tell it to permanently ignore that problem? I mean, I can't even upgrade until it ignores it. I REALLY don't want to reinstall the OS, because it would take me a weekend+ to set it all up again.

---

### Post by slackerwarenative on 2008-05-18
I do want to upgrade to 8.04.

I guess I can just backup my drive overnight. Is there a way I can automate the new install to install all the .debs?

What I could really use is a way to save what is installed, so I can just select it in synaptic and let it install over the next night.

Thanks again for any suggestions.

---

### Post by slackerwarenative on 2008-05-18
Huh. Synaptic has some save feature. Does anyone have experience with this?

---

### Post by rafalr on 2008-05-22
hi slackerwarenative,

got exactly the same problem (just another package - some lousy/outdated stuff from Dell server which failed to fully install due to broken dependencies)

the final error messga is exactly the same, I guess dpkg fails to remove some files as those were simply not installed, although some logs possibly keep track of them as having been installed

my guess is we need to find that log/tracking file and manually remove the foulty files 

if you manage to solve this - pls let me know.

Rafal

---

### Post by rafalr on 2008-05-22
hi there again,

I was right, you need to edit

sudo gedit /var/lib/dpkg/status

and remove the whole passage relating to your package at problem

more here: [http://ubuntuforums.org/showthread.php?p=4861243](http://ubuntuforums.org/showthread.php?p=4861243) (message #3)

cheers,
rafal

---

### Post by Swagman on 2011-02-01
Sorry for thread necromancy..

Just had this exact same problem as OP trying to remove latest Cinelerra.

It was previously installed via akirad but disabled on update to Maverick.

Running Cinelerra and I found no load menu would work so removed old version with Synaptic and entered new ppa and installed fresh only to receive a "Run as root" 0x7fffffff >/shmmax  <--- not 100% correct message.

Did that as sudo su and ran from cli and prog worked but had the same menu issue.

So I decided to remove it only to end up with a b0rked update manager as described in OP.

rafair was correct with his cure

```
sudo gedit /var/lib/dpkg/status
```

Just use find cinelerra option  in gedit to fasttrack to relevant section, highlight entire cinelerra section and delete and save.

Thanks rafair.

---

### Post by lex-alex on 2011-04-14
i had the same problem...i used all the above, but nothing happened. so i searched manually the files. i had problem with cinelerra. so in /var/lib/dpkg/info/ i looked for cinelerra conf files, i deleted them i made an "apt-get update" and my sistem is back online. for administrator rules run "sudo nautilus /var/lib/info/" and that's all

---

### Post by sespress on 2012-01-14
That was it for me too.  I had the Bacula module stuck after dbconfig crashed on me.  Had to delete like over a dozen entries.   But it worked immediately afterwards.  

> **rafalr said:**
> hi there again,

I was right, you need to edit

sudo gedit /var/lib/dpkg/status

and remove the whole passage relating to your package at problem

more here: [http://ubuntuforums.org/showthread.php?p=4861243](http://ubuntuforums.org/showthread.php?p=4861243) (message #3)

cheers,
rafal

---

### Post by coffeecat on 2012-01-14
Old thread. If anyone needs help removing cinelerra, please start a fresh thread.

Thread closed.

---

