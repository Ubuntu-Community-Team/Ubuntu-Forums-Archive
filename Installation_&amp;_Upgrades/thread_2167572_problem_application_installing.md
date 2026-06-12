---
title: "problem application installing"
date: 2013-08-14
forum: Installation &amp; Upgrades
---

### Post by Gassoumi_Akrem on 2013-08-14
hi there,


every time i try to install new application (codeblocks,aircrack...) i encounter the following message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  codeblocks-common libcodeblocks0 libwxbase2.8-0 libwxgtk2.8-0
Suggested packages:
  libwxgtk2.8-dev wx-common codeblocks-contrib libgnomeprintui2.2-0
The following NEW packages will be installed:
  codeblocks codeblocks-common libcodeblocks0 libwxbase2.8-0 libwxgtk2.8-0
0 upgraded, 5 newly installed, 0 to remove and 83 not upgraded.
1 not fully installed or removed.
Need to get 9 474 kB of archives.
After this operation, 26,8 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) precise/universe libwxbase2.8-0 i386 2.8.12.1-6ubuntu2 [597 kB]
Get:2 [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) precise/universe libwxgtk2.8-0 i386 2.8.12.1-6ubuntu2 [3 254 kB]
Get:3 [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) precise/universe libcodeblocks0 i386 10.05-2 [1 695 kB]
Get:4 [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) precise/universe codeblocks-common all 10.05-2 [2 287 kB]
Get:5 [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) precise/universe codeblocks i386 10.05-2 [1 642 kB]
Fetched 9 474 kB in 23s (398 kB/s)                                             
Setting up install-info (4.13a.dfsg.1-8ubuntu2) ...
/etc/environment: line 2: :~$: command not found
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 install-info
E: Sub-process /usr/bin/dpkg returned an error code (1)




any help please
thx in advance;):P

---

### Post by Bashing-om on 2013-08-14
Gassoumi_Akrem; Hi !

From this:
> 
codeblocks codeblocks-common libcodeblocks0 libwxbase2.8-0 libwxgtk2.8-0
0 upgraded, 5 newly installed, 0 to remove and 83 not upgraded

the "83 not upgraded" suggest you have not updated the software in a spell.
From terminal (key combo ctl+alt+t yields a terminal) do:
```

sudo apt-get update
sudo apt-get upgrade

```
then try and install your application once more.

---

### Post by ian-weisser on 2013-08-14
> **Gassoumi_Akrem said:**
> ```
...
0 upgraded, 5 newly installed, 0 to remove and 83 not upgraded.
1 not fully installed or removed.
...
```

That is not an install problem.
You have a broken package. Until you fix it, you cannot install or remove packages, nor update your system.


> **Gassoumi_Akrem said:**
> ```
...
Setting up install-info (4.13a.dfsg.1-8ubuntu2) ...
/etc/environment: line 2: :~$: command not found
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 127
[COLOR=#ff0000]Errors were encountered while processing:
 install-info[/COLOR]
E: Sub-process /usr/bin/dpkg returned an error code (1)
...
```

That's the broken package.

Here is one way to fix it.
```
sudo apt-get clean install-info    # Delete the broken package from your cache.
sudo apt-get update
sudo apt-get upgrade
```

Read the output carefully. If there are any more error messages, post the entire output here.
Please use CODE tags (the '#' edit button) when you paste output.

---

