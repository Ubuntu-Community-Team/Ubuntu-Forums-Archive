---
title: "The Installer is Being Really Annoying"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by gorcq on 2008-03-10
[FONT="Times New Roman"]Every time I try to install something now, including through the command-line with apt-get, I get an error message saying that it cannotinstall until it has first removed the broken package wacom-kernel-source. If I tell it to go ahead and remove that package, I get another error:
```

dpkg: error processing wacom-kernel-source (--remove):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 wacom-kernel-source
E: Sub-process /usr/bin/dpkg returned error code (1)
```
This occurs even if I run sudo apt-get autoremove or sudo apt-get install -f, or using the synaptics utility.

wacom-kernel-source, by the way, is a package I got off ubuntu.com when I was trying to get the stylus of my tablet pc working right. (I got that fixed now, thanks to a helpful how-to guide on this site.) I got a list of the files in wacom-kernel-source, and none of them are in my computer now, nor the directories they are supposed to be in; but the package must be listed somewhere in my computer as being installed. 

Any help with this annoying problem would be greatly appreciated. Thank you in advance.[/FONT]

---

### Post by zvacet on 2008-03-10
Did you try in** synaptic>edit tab>fix broken packages**?To find package 

```
locate** packagename**
```

or go to the top of filesystem with command** cd /** and after that 

```
sudo find / -name *packagename*
```

---

### Post by RSLxH on 2008-03-10
It&#8217;s worthwhile to do this every now again again on your box when you&#8217;ve been installing and uninstalling new apps. This will go through and check which packages have been installed that are no longer needed. It will then remove them for you.

```
sudo apt-get autoremove
```


 Output looks like below
 

```
Reading package lists&#8230; Done
Building dependency tree
Reading state information&#8230; Done
The following packages were automatically installed and are no longer required:
libcommoncpp2-1.5.3-0
The following packages will be REMOVED
libcommoncpp2-1.5.3-0
0 upgraded, 0 newly installed, 1 to remove and 29 not upgraded.
Need to get 0B of archives.
After unpacking 688kB disk space will be freed.
Do you want to continue [Y/n]?
```


 Here you need to select Y to remove these packages

---

### Post by gorcq on 2008-03-10
autoremove just gives me the same error I posted above.
Both of zvacet's commands gave no output at all.

---

### Post by torer1 on 2008-03-10
I have got the same error during two recent installations. It first occurred when installing the **ntp** package and again - today - when installing the **nis** package. At the time being I have not really found what causes this. The problem occurs whatever I do - using Synaptic, aptitude, apt-get or dpkg gives the same error. 

For the ntp package I managed to work around the problem by removing the half-configured package, downloading an older debian package and installing that with dpkg. 

The nis package is still causing me troubles, however.

What makes it difficult is that I have no real idea how to troubleshoot the installation procedure. The only clue I got during the failed ntp installation is the following output:

[FONT="Courier New"]Selecting previously deselected package ntp.
(Reading database ... 118704 files and directories currently installed.)
Unpacking ntp (from .../ntp_1%3a4.2.4p0+dfsg-1ubuntu2_i386.deb) ...
Setting up ntp (1:4.2.4p0+dfsg-1ubuntu2) ...
[COLOR="Red"]usage: update-rc.d [-n] [-f] <basename> remove
[INDENT]       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
[INDENT]		-n: not really
		-f: force
[/INDENT][/INDENT][/COLOR]dpkg: error processing ntp (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ntp
[/FONT]
update-rc.d seems to be started with some incorrect parameters. However, in the case of the failed nis installation, I don't even get that message. Anyone have any ideas of what's going on ?

---

### Post by zvacet on 2008-03-10
@ **gorcq**

Instead of packagename you put real name of package you want to locate,didn´t you.In your case 

```
locate wacom-kernel-source
```

or **cd /**

```
sudo find / -name  wacom-kernel-source
```


@** torer1**

```
sudo dpkg --configure -a
```

---

### Post by gorcq on 2008-03-10
zvacet: Yeah, I did that right.
Edit: Wait, now I tried locate again using sudo and I got a list of files. So I deleted them. Now the problem's gone. Thank you for your help.

---

