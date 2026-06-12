---
title: "The basic computer information script .1"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by mini_g on 2008-06-10
I wasn't sure as to where to place this, so here I am!

I found this neat script over in the [Regnum fora]("http://www.regnumonline.com.ar/forum/showpost.php?p=386908&postcount=2"), and decided to translate it and expand upon it (Haven't gotten this far, but am working on getting hardware acceleration support detection incorporated).

What it does is gather the basic information of the computer that runs it, and places all of the general information into one neat file (~/Desktop/diag.txt). I am thinking about this being centered for IRC troubleshooting purposes and such, where it'd be easier to easily pastebin the basic information of ones computer.

It also makes use of the package lm-sensors (but isn't required), so the temperature and such are posted if possible.

```
clear && echo "The basic computer information script .1" && echo "" && echo "++++++CPU+++++" > pp && cat /proc/cpuinfo | grep model >> pp && cat /proc/cpuinfo | grep 'cpu MHz' >> pp && cat /proc/cpuinfo | grep 'cache size' >> pp && echo "++++++DISTRO+++++" >> pp && uname -a >> pp && cat /etc/`ls /etc/ | grep version` >> pp && ls /etc/ | grep version >> pp && cat /etc/issue | grep -m1 "" | cut -d\\ -f1 >> pp && uptime >> pp && echo "++++++VIDEO CARD INFO+++++" >> pp && `locate lspci | grep -m1 'n/lspci'` | grep VGA >> pp && glxinfo | grep direct >> pp && glxinfo | grep OpenGL >> pp && glxinfo | grep s3tc >> pp && echo "++++++MODULES++++++" >> pp && cat /etc/X11/xorg.conf | grep Load >> pp && echo "++++++RAM+++++" >> pp && cat /proc/meminfo | grep MemTotal >> pp && echo "++++++SENSORS+++++" >> pp && sensors >> pp || echo "There are no sensors detected" >> pp && mv pp $HOME/Desktop/diag.txt && echo "Information has been gathered." && echo "Now pasting..." && cat $HOME/Desktop/diag.txt
```

Here's the output from my computer:

=.=.=.=.=.=.=.=.=.=.=.=.=.=.=.=.=.=.=.=

The basic computer information script .1

Information has been gathered.
Now pasting...
++++++CPU+++++
model           : 76
model name      : Mobile AMD Sempron(tm) Processor 3400+
cpu MHz         : 1800.000
cache size      : 256 KB
++++++DISTRO+++++
Linux redux 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux
lenny/sid
debian_version
Ubuntu 8.04 
 02:04:40 up  2:45,  2 users,  load average: 2.56, 2.19, 2.08
++++++VIDEO CARD INFO+++++
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
direct rendering: Yes
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7412 Release
OpenGL extensions:
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
++++++MODULES++++++
	Load		"glx"
++++++RAM+++++
MemTotal:      1424124 kB
++++++SENSORS+++++
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +68.0°C 
Core1 Temp:  +68.0°C

=.=.=.=.=.=.=.=.=.=.=.=.=.=.=.=.=.=.=.=

***Any thoughts? Ideas? Questions?***

~I am thinking about finding a way to run this so that sudo can unobtrusively enable access the hardware make/model information for easy make & model Q/A for laptops.

~lspci output?

~Break into multiple smaller scripts for one-line irc posting?

---

### Post by K.Mandla on 2008-06-10
Moved to Installation and Upgrades.

---

### Post by Vivaldi Gloria on 2008-06-10
mini_g,

See also

[http://ubuntuforums.org/showthread.php?t=792639](http://ubuntuforums.org/showthread.php?t=792639)

---

### Post by mini_g on 2008-06-10
> **Vivaldi Gloria said:**
> mini_g,
 
See also
 
[http://ubuntuforums.org/showthread.php?t=792639](http://ubuntuforums.org/showthread.php?t=792639)
 
Ah, silly me.  Should've thought to search before posting... ](*,)
 
Will check it out once I get back into my 'nix haven.

---

### Post by mini_g on 2008-06-11
Ok, I just looked over the scripts that Vivaldi Gloria mentioned. I really like them, but was thinking about this one being more centered for IRC troubleshooting purposes and such, where it'd be easier to easily pastebin the (somewhat) generic information of ones computer.  Sorry for not being entirely clear in my initial post.

:popcorn:

---

### Post by sidran on 2008-06-11
I love projects like these.  I don't know why, but scripting is just fun for me.  So while I understand the fun in this project, I still have to ask:

Why not just use hwinfo? :p

---

### Post by mini_g on 2008-06-11
> **sidran said:**
> I love projects like these.  I don't know why, but scripting is just fun for me.  So while I understand the fun in this project, I still have to ask:

Why not just use hwinfo? :p

Good point.  :) Well, hwinfo doesn't come with vanilla Ubuntu, so this allows anyone pretty much anyone with a standard Distro (at the time being) to obtain basic info about the computer.

*(Thanks for the tip on this program.  I like the thoroughness that it gives.)*

---

### Post by sidran on 2008-06-11
> **mini_g said:**
> Good point.  :) Well, hwinfo doesn't come with vanilla Ubuntu, so this allows anyone pretty much anyone with a standard Distro (at the time being) to obtain basic info about the computer.

*(Thanks for the tip on this program.  I like the thoroughness that it gives.)*

Fair enough.  And no problem.  It is a pretty handy tool.  :)

---

