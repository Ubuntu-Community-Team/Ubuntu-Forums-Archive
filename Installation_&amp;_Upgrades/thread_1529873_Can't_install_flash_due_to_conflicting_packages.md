---
title: "Can't install flash due to conflicting packages"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by G1imt on 2010-07-12
I've tried to install flash packages using Synaptic Package Manager and Ubuntu Software Center. I always get the same error:

> installArchives() failed: Preconfiguring packages ...
Preconfiguring packages ...
dpkg: regarding .../flashplugin-installer_10.1.53.64ubuntu0.10.04.3_amd64.deb containing flashplugin-installer:
 adobe-flashplugin conflicts with flashplugin-installer
  flashplugin-installer (version 10.1.53.64ubuntu0.10.04.3) is to be installed.
dpkg: error processing /var/cache/apt/archives/flashplugin-installer_10.1.53.64ubuntu0.10.04.3_amd64.deb (--unpack):
 conflicting packages - not installing flashplugin-installer
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_10.1.53.64ubuntu0.10.04.3_amd64.deb


I've tried to get rid of everything flash related on the computer with no success.

Also I followed a guide on how to install flash to Chrome. I copied the correct .so file into Chrome's plugin folder and added the start up argument to the Chrome shortcut with no success.

Could anyone help me install flash?

---

### Post by G1imt on 2010-07-15
BUMP

This should be easy stuff for any ubuntu guru. There are probably just some commands i have to run to purge the old packages or something

---

### Post by G1imt on 2010-07-16
Pleez someone

Youtube is so close, yet so far away

---

### Post by claracc on 2010-07-16
You can use the flash-aid addon for firefox made by lovinglinux:[https://addons.mozilla.org/es-ES/firefox/collection/lovinglinux](https://addons.mozilla.org/es-ES/firefox/collection/lovinglinux)
As it is said in the description, it removes conflicting flash plugins and installs the appropriate ones.

I hope it can help

---

### Post by G1imt on 2010-07-16
Didn't work. I got an error message in the console that i tried to copy, but for mysterious reasons the console closed before i could. I've tried to reinstall the plugin but the console wont show up again.

In any case, stuff if ****ed up. I got a hint to repeat

sudo apt-get upgrade -f

and

sudo apt-get -f install

until i only get one error message, and here they are:

> codemonkey@ubuntu:~$ sudo apt-get upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following NEW packages will be installed
  flashplugin-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
13 not fully installed or removed.
Need to get 0B/19.8kB of archives.
After this operation, 188kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: regarding .../flashplugin-installer_10.1.53.64ubuntu0.10.04.3_amd64.deb containing flashplugin-installer:
 adobe-flashplugin conflicts with flashplugin-installer
  flashplugin-installer (version 10.1.53.64ubuntu0.10.04.3) is to be installed.
dpkg: error processing /var/cache/apt/archives/flashplugin-installer_10.1.53.64ubuntu0.10.04.3_amd64.deb (--unpack):
 conflicting packages - not installing flashplugin-installer
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_10.1.53.64ubuntu0.10.04.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


> codemonkey@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  flashplugin-installer
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
The following NEW packages will be installed
  flashplugin-installer
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
12 not fully installed or removed.
Need to get 0B/19.8kB of archives.
After this operation, 188kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: regarding .../flashplugin-installer_10.1.53.64ubuntu0.10.04.3_amd64.deb containing flashplugin-installer:
 adobe-flashplugin conflicts with flashplugin-installer
  flashplugin-installer (version 10.1.53.64ubuntu0.10.04.3) is to be installed.
dpkg: error processing /var/cache/apt/archives/flashplugin-installer_10.1.53.64ubuntu0.10.04.3_amd64.deb (--unpack):
 conflicting packages - not installing flashplugin-installer
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_10.1.53.64ubuntu0.10.04.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Could someone help me resolve these errors

---

### Post by G1imt on 2010-07-16
OK never mind. I used the broken package filter to uinstall the broken flash plugin. Now the above commands does nothing in the terminal.

I now tried to install the flash plugin via ubuntu software center, and got the following error:

> installArchives() failed: Preconfiguring packages ...
Preconfiguring packages ...
dpkg: regarding .../flashplugin-installer_10.1.53.64ubuntu0.10.04.3_amd64.deb containing flashplugin-installer:
 adobe-flashplugin conflicts with flashplugin-installer
  flashplugin-installer (version 10.1.53.64ubuntu0.10.04.3) is to be installed.
dpkg: error processing /var/cache/apt/archives/flashplugin-installer_10.1.53.64ubuntu0.10.04.3_amd64.deb (--unpack):
 conflicting packages - not installing flashplugin-installer
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_10.1.53.64ubuntu0.10.04.3_amd64.deb


---

### Post by lechien73 on 2010-07-16
You could try:

```
sudo apt-get remove --purge adobe-flashplugin
```

Since that file seems to be causing the conflict. A shell script that I modified and used for my flash installation is linked [here]("http://uri.tl/2"). This purges other versions of flash and then installs the flash-nonfree plugin from the non-free repositories.

---

### Post by G1imt on 2010-07-16
Your shell script seems to return the same error message every other attempt of installing flash has given me:
> codemonkey@ubuntu:~$ sudo '/home/codemonkey/Desktop/new-64bit-flash-installer.sh' 
[sudo] password for codemonkey: 
Stopping any Firefox instance that might be running
firefox: no process found
Removing all other flash plugins previously installed:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
Package libflashsupport is not installed, so not removed
The following packages will be REMOVED
  nspluginwrapper*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 565kB disk space will be freed.
(Reading database ... 199274 files and directories currently installed.)
Removing nspluginwrapper ...
Processing triggers for man-db ...
Installing Flash Player 10
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  flashplugin-installer nspluginwrapper
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-bitstream-vera ttf-dejavu
  ttf-xfree86-nonfree xfs
The following NEW packages will be installed
  flashplugin-installer flashplugin-nonfree nspluginwrapper
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 198kB/220kB of archives.
After this operation, 799kB of additional disk space will be used.
Get: 1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/multiverse nspluginwrapper 1.2.2-0ubuntu6 [198kB]
Fetched 198kB in 0s (261kB/s)         
Preconfiguring packages ...
Selecting previously deselected package nspluginwrapper.
(Reading database ... 199247 files and directories currently installed.)
Unpacking nspluginwrapper (from .../nspluginwrapper_1.2.2-0ubuntu6_amd64.deb) ...
dpkg: regarding .../flashplugin-installer_10.1.53.64ubuntu0.10.04.3_amd64.deb containing flashplugin-installer:
 adobe-flashplugin conflicts with flashplugin-installer
  flashplugin-installer (version 10.1.53.64ubuntu0.10.04.3) is to be installed.
dpkg: error processing /var/cache/apt/archives/flashplugin-installer_10.1.53.64ubuntu0.10.04.3_amd64.deb (--unpack):
 conflicting packages - not installing flashplugin-installer
Selecting previously deselected package flashplugin-nonfree.
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.1.53.64ubuntu0.10.04.3_amd64.deb) ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_10.1.53.64ubuntu0.10.04.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
codemonkey@ubuntu:~$ 


Copying the line from your post and running it gave this output:

> codemonkey@ubuntu:~$ sudo apt-get remove --purge adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
codemonkey@ubuntu:~$ 


Running apt-get -f install gave me the same old ****ING error message again

> codemonkey@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  flashplugin-installer
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-bitstream-vera ttf-dejavu
  ttf-xfree86-nonfree xfs
The following NEW packages will be installed
  flashplugin-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/19.8kB of archives.
After this operation, 188kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: regarding .../flashplugin-installer_10.1.53.64ubuntu0.10.04.3_amd64.deb containing flashplugin-installer:
 adobe-flashplugin conflicts with flashplugin-installer
  flashplugin-installer (version 10.1.53.64ubuntu0.10.04.3) is to be installed.
dpkg: error processing /var/cache/apt/archives/flashplugin-installer_10.1.53.64ubuntu0.10.04.3_amd64.deb (--unpack):
 conflicting packages - not installing flashplugin-installer
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_10.1.53.64ubuntu0.10.04.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
codemonkey@ubuntu:~$ 


Why would Ubuntu implement this unfixable damned error message just to haunt me.

Any ideas?

---

### Post by lechien73 on 2010-07-16
Ok, I would try going to Places > Search for files and search for adobe-flashplugin. If it doesn't find it, then try the following to force a removal of the flashplugin-nonfree module:

```
sudo rm /var/lib/dpkg/info/flashplugin-nonfree.prerm
sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
sudo dpkg --purge --force-remove-reinstreq flashplugin-nonfree

```
Then try my script again. Hope this helps!

---

### Post by G1imt on 2010-07-19
I did the search, found quite a few files and folders, deleted ALL of them.

Ran all of your commands, all of which were ignored because file didn't exist or package not installed. Tried to install flash again:

> installArchives() failed: Preconfiguring packages ...
Preconfiguring packages ...
dpkg: regarding .../flashplugin-installer_10.1.53.64ubuntu0.10.04.3_amd64.deb containing flashplugin-installer:
 adobe-flashplugin conflicts with flashplugin-installer
  flashplugin-installer (version 10.1.53.64ubuntu0.10.04.3) is to be installed.
dpkg: error processing /var/cache/apt/archives/flashplugin-installer_10.1.53.64ubuntu0.10.04.3_amd64.deb (--unpack):
 conflicting packages - not installing flashplugin-installer
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_10.1.53.64ubuntu0.10.04.3_amd64.deb


---

### Post by dino99 on 2010-07-19
[http://www.blueplastic.net/en/ubuntu-10-04-lucid-lynx-plugin-de-flash-64-bits/](http://www.blueplastic.net/en/ubuntu-10-04-lucid-lynx-plugin-de-flash-64-bits/)

---

