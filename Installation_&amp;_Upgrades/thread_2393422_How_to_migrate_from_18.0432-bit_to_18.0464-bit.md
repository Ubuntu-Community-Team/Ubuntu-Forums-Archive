---
title: "How to migrate from 18.04/32-bit to 18.04/64-bit?"
date: 2018-06-03
forum: Installation &amp; Upgrades
---

### Post by claus on 2018-06-03
Hi,

a few weeks ago, I updated from 16.04 LTS to 18.04 LTS. Both are 32-bit versions. I erroneously believed that my processor wouldn't support a 64-bit OS. I do 3D rendering with Blender/Cycles, and today I found out that the processor of my PC *does* support 64-bit. Now my question: Can I move from 32-bit to 64-bit via online upgrade, or do I need to burn a DVD and install from there?

TIA,

Claus

---

### Post by Autodave on 2018-06-03
You are going to have to do a clean install.  But before that, do you have a dual core processor or is your processor simply one that claims it will do dual core work?  I have run into a few of those machines claiming that they are dual core but are actually only single core. (I believe Dell was one of them, but I am not certain about that.)

How about some specs on your machine or give us the model and we can look it up.

---

### Post by #&amp;thj^% on 2018-06-03
I agree with Autodave show the below code:
```
uname -m && inxi -xxx -C
```
```
**[COLOR="#FF0000"]uname -m && inxi -xxx -C[/COLOR]**
x86_64
CPU:
  Topology: Quad Core model: Intel Core i5-6400 bits: 64 type: MCP 
  arch: Skylake-S rev: 3 L2 cache: 6144 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 21704 
  Speed: 1758 MHz min/max: 800/3300 MHz Core speeds (MHz): 1: 1303 2: 1306 
  3: 1307 4: 1294 

```
You may want to install inxi first:
```
sudo apt-get install inxi
```
Or even just plain:
```
lscpu
```

---

### Post by claus on 2018-06-03
> **Autodave said:**
> You are going to have to do a clean install.  But before that, do you have a dual core processor or is your processor simply one that claims it will do dual core work?  I have run into a few of those machines claiming that they are dual core but are actually only single core. (I believe Dell was one of them, but I am not certain about that.)

How about some specs on your machine or give us the model and we can look it up.

Ok, here's the info from Ubuntu:

[IMG]https://blenderartists.org/uploads/default/original/4X/b/0/0/b0019edcfe6541daa009f8a0326d25ebe8bde3e7.png[/IMG]

I'm not that knowledgeable about PC specs, but some guy over at Blender Artists looked the processor up, and it's supposed to run 64-bit OSes.

And 'uname -m && inxi -xxx -C' resulted in:

CPU:    Dual core Intel Core2 Duo E8400 (-MCP-) 
           arch: Penryn rev.10 cache: 6144 KB
           flags: (lm nx pae sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 11999
           clock speeds: min/max: 2000/3000 MHz 1: 1999 MHz 2: 1

According to the info at Intel  the processor does support 64-bit: [https://ark.intel.com/products/33910/Intel-Core2-Duo-Processor-E8400-6M-Cache-3_00-GHz-1333-MHz-FSB]("https://ark.intel.com/products/33910/Intel-Core2-Duo-Processor-E8400-6M-Cache-3_00-GHz-1333-MHz-FSB")

---

### Post by #&amp;thj^% on 2018-06-03
That should be suitable to handle a 64bit OS then, and the 4Gigs of ram as well.
Enjoy! :)

---

### Post by oldfred on 2018-06-03
Make sure you have a good backup.
When I converted my dual core system from 32  bit to 64 bit back in 2009, I did not know to export list of installed apps. I did install into a new / (root) partition so I could go back and get info, but exporting & reinstalling list of apps would have been a lot easier.  I now include that as part of my regular backup.

       My backup includes this also. The dpkg list is a very long text list of all applications and the dependencies. 
If upgrading, you may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade
#IF you get this error:
dpkg: warning: package not in database
sudo apt-get install dselect
sudo dselect 
   -> Update
   -> Install

---

### Post by claus on 2018-06-04
> **oldfred said:**
> Make sure you have a good backup. [ ... ]

I make regular backups of my /home partition on an external harddrive, using the built-in backup feature of Ubuntu. Is this sufficient? 

Claus

---

### Post by oldfred on 2018-06-04
That will not backup the list of apps installs. It does backup your data for those apps and your configurations & all your other data.
If you have done any system changes, you may have edited a configuration file in /etc. And If running server software like web or database for testing or development, you may have other folders with data in / (root).

---

### Post by ubfan1 on 2018-06-04
To produce the list of what You installed, try  
comm -23 <(apt-mark showmanual | sort -u) <(gzip -dc /var/log/installer/initial-status.gz | sed -n 's/^Package: //p' | sort -u)

The dpkg --get-selections  includes package updates also, so it too big.

---

