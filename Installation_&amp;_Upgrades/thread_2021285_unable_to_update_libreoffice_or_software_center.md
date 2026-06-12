---
title: "unable to update libreoffice or software center"
date: 2012-07-09
forum: Installation &amp; Upgrades
---

### Post by biohzrd87 on 2012-07-09
So I just set up Ubuntu on an old hdd that I found. I was in another computer that broke and it was larger then the one I had in a laptop so I swapped them out. I just done doing the full install but now I can not open the software center. I keep getting an error about a package needing to be repaired first. I try to repair it but it will not work. I think it has something to do with libreoffice not updating. I have the update "office productivity suite - arch-independent files" waiting to install. When I try to install I get this error: 

The following packages have unmet dependencies:

libreoffice-core: Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is installed

I use sudo apt-get install -f in the terminal I get:
```

s0ggyc0rnbr3ad@Jarvis:~$ sudo apt-get install -f
[sudo] password for s0ggyc0rnbr3ad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-hicontrast libreoffice-style-crystal
  libreoffice-style-oxygen
The following packages will be upgraded:
  libreoffice-common
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
15 not fully installed or removed.
Need to get 0 B/20.9 MB of archives.
After this operation, 644 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 167908 files and directories currently installed.)
Preparing to replace libreoffice-common 1:3.5.2-2ubuntu1 (using .../libreoffice-common_1%3a3.5.3-0ubuntu1_all.deb) ...
Unpacking replacement libreoffice-common ...
dpkg-deb (subprocess): failed to read on buffer copy for failed to write to pipe in copy: Input/output error
dpkg-deb (subprocess): data: internal bzip2 read error: 'UNEXPECTED_EOF'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a3.5.3-0ubuntu1_all.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/libreoffice/program/types/offapi.rdb'
rmdir: failed to remove `/var/lib/libreoffice/share/prereg/': No such file or directory
rmdir: failed to remove `/var/lib/libreoffice/share/': Directory not empty
rmdir: failed to remove `/var/lib/libreoffice/program/': No such file or directory
rmdir: failed to remove `/var/lib/libreoffice': Directory not empty
rmdir: failed to remove `/var/lib/libreoffice': Directory not empty
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a3.5.3-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```I tried to use sud apt-get remove libreoffice-common I get:

```
s0ggyc0rnbr3ad@Jarvis:~$ sudo apt-get remove libreoffice-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:3.5.3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```Any ides on what to try next?

---

### Post by jeSah8ci on 2013-03-25
I too ran into a very similar error.

> Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
```
The following packages have unmet dependencies:

libreoffice-core: Depends: libgcc1 (>= 1:4.1.1) but 1:4.7.2-2ubuntu1 is installed
libreoffice-emailmerge:
```

Also, after this error showed, the 'backend_helper.py' crashed:

> **Sorry, Ubuntu 12.10 has experienced an internal error.**
If you notice further problems, try restarting the computer.

Judging by some of the error messages:
> [LIST]
[*]Title
[*][INDENT]backend_helper.py crashed with libreoffice-emailmerge in _run()[/INDENT]
[*]UnreportableReason
[*][INDENT]You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs:[/INDENT]
[*][INDENT]libssl1.0.0[/INDENT]
[*]
[/LIST]


I proceeded to open Synaptic Package Manager to upgrade libssl1.0.0 and, curiously enough, it offered me to uninstall a lot of libreoffice packages; when I was about do that, I noticed that there was a lot of 'left unchanged' packages that were previously unavailable to upgrade. After selecting 'Mark all upgrades', I didn't get any unmet dependencies or broken packages anymore.

**Note:** I never had to disable LibreOffice's Launchpad ppa.

Hope you solved your problem.

---

### Post by tomdkat on 2013-03-25
> **rolandog said:**
> I too ran into a very similar error.


```
The following packages have unmet dependencies:

libreoffice-core: Depends: libgcc1 (>= 1:4.1.1) but 1:4.7.2-2ubuntu1 is installed
libreoffice-emailmerge:
```

Also, after this error showed, the 'backend_helper.py' crashed:



Judging by some of the error messages:


I proceeded to open Synaptic Package Manager to upgrade libssl1.0.0 and, curiously enough, it offered me to uninstall a lot of libreoffice packages; when I was about do that, I noticed that there was a lot of 'left unchanged' packages that were previously unavailable to upgrade. After selecting 'Mark all upgrades', I didn't get any unmet dependencies or broken packages anymore.

**Note:** I never had to disable LibreOffice's Launchpad ppa.

Hope you solved your problem.
I've run into this exact same problem just now and I'm trying to do what you describe above but Synaptic Package Manager identifies the two packages you listed above as being "broken":

libreoffice-core
libreoffice-emailmerge

and it won't let me do anything until I fix these.  Did you encounter this?  Also, I did get the crash in 'backend_helper.py' as you did. I'm also running Ubuntu 12.10 (64-bit).

Unfortunately, I don't know if I have an upgrade to libssl pending or not, since I can't get past the above two broken packages.

EDIT: When I run the "openssl version" command, it shows I have libssl 1.0.1c installed.  It's not the latest version but newer than libssl 1.0.0.

Any ideas or suggestions?

Thanks!

Peace...

---

### Post by tomdkat on 2013-03-25
> **tomdkat said:**
> I've run into this exact same problem just now and I'm trying to do what you describe above but Synaptic Package Manager identifies the two packages you listed above as being "broken":

libreoffice-core
libreoffice-emailmerge

and it won't let me do anything until I fix these.  Did you encounter this?  Also, I did get the crash in 'backend_helper.py' as you did. I'm also running Ubuntu 12.10 (64-bit).

Unfortunately, I don't know if I have an upgrade to libssl pending or not, since I can't get past the above two broken packages.

EDIT: When I run the "openssl version" command, it shows I have libssl 1.0.1c installed.  It's not the latest version but newer than libssl 1.0.0.

Any ideas or suggestions?

Thanks!

Peace...

*** UPDATE ***

Well, I guess the problem has resolved itself.  I ran the "sudo apt-get install -f" command mentioned above and it seems to have run successfully.

```

tom@deathstar:~$ sudo apt-get install -f
[sudo] password for tom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-crystal libreoffice-style-hicontrast libreoffice-style-oxygen
The following packages will be upgraded:
  libreoffice-common
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
19 not fully installed or removed.
Need to get 0 B/11.5 MB of archives.
After this operation, 12.3 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 551129 files and directories currently installed.)
Preparing to replace libreoffice-common 1:4.0.1~rc2-0ubuntu1~quantal1~ppa1 (using .../libreoffice-common_1%3a4.0.2~rc1-0ubuntu1~quantal2_all.deb) ...
Unpacking replacement libreoffice-common ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for hicolor-icon-theme ...
Processing triggers for gnome-icon-theme ...
Setting up libreoffice-common (1:4.0.2~rc1-0ubuntu1~quantal2) ...
Setting up libreoffice-core (1:4.0.2~rc1-0ubuntu1~quantal2) ...
Setting up libreoffice-pdfimport (1:4.0.2~rc1-0ubuntu1~quantal2) ...
Setting up python-uno (1:4.0.2~rc1-0ubuntu1~quantal2) ...
Setting up libreoffice-base-core (1:4.0.2~rc1-0ubuntu1~quantal2) ...
Setting up libreoffice-base (1:4.0.2~rc1-0ubuntu1~quantal2) ...
Setting up libreoffice-calc (1:4.0.2~rc1-0ubuntu1~quantal2) ...
Setting up libreoffice-draw (1:4.0.2~rc1-0ubuntu1~quantal2) ...
Setting up libreoffice-impress (1:4.0.2~rc1-0ubuntu1~quantal2) ...
Setting up libreoffice-math (1:4.0.2~rc1-0ubuntu1~quantal2) ...
Setting up libreoffice-report-builder-bin (1:4.0.2~rc1-0ubuntu1~quantal2) ...
Setting up libreoffice-writer (1:4.0.2~rc1-0ubuntu1~quantal2) ...
Setting up libreoffice (1:4.0.2~rc1-0ubuntu1~quantal2) ...
Setting up libreoffice-gtk (1:4.0.2~rc1-0ubuntu1~quantal2) ...
Setting up libreoffice-gnome (1:4.0.2~rc1-0ubuntu1~quantal2) ...
Setting up libreoffice-help-en-us (1:4.0.2~rc1-0ubuntu1~quantal2) ...
Setting up libreoffice-presentation-minimizer (1.0.4+LibO4.0.2~rc1-0ubuntu1~quantal2) ...
Setting up libreoffice-emailmerge (1:4.0.2~rc1-0ubuntu1~quantal2) ...
Setting up libreoffice-ogltrans (1:4.0.2~rc1-0ubuntu1~quantal2) ...
Setting up libreoffice-presenter-console (1:4.0.2~rc1-0ubuntu1~quantal2) ...
Processing triggers for menu ...
Processing triggers for libreoffice-common ...
tom@deathstar:~$ 

```

Now, when I go to "About this computer", it shows the system as being up to date.  Weird.  I'm not complaining. :)

Peace...

---

