---
title: "Installing things broke something"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by GamesForLinux on 2008-04-30
I installed a large number of programs at once through the package manager. After downloading them, it installed most of them, but crashed a while after saying the hard drive was 100% full (it's not). I tried to start the package manager again, and it failed with this message:> 

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

On using apt-get install -f, it said that openclipart-openoffice.org was partly installed, but still needs the dependency openclipart-png, and has the following error on trying to install:> 
Reading database ... 153021 files and directories currently installed.)
Unpacking openclipart-png (from .../openclipart-png_0.18+dfsg-4_all.deb) ...
dpkg: error processing /var/cache/apt/archives/openclipart-png_0.18+dfsg-4_all.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./usr/share/openclipart/png/people/man_head_mikhail_a.medve_01.png': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/openclipart-png_0.18+dfsg-4_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I can't use apt-get remove to get rid of openclipart-openoffice.org because that package is not installed.
Also, deleting the files from /var/cache/apt/archives doesn't help.
And I just realized this is probably the wrong place to post this. Sorry.

---

