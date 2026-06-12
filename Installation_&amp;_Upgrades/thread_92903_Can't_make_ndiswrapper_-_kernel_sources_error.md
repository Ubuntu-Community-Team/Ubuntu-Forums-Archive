---
title: "Can't make ndiswrapper - kernel sources error"
date: 2005-11-20
forum: Installation &amp; Upgrades
---

### Post by joshuaxls on 2005-11-20
I have been running Ubuntu 5.10 on my laptop and I just installed it on my desktop computer also. Everything went fine, and now I am working on getting the wireless networking working. I have no wired network, so it is essential that I get wireless working.

Anyway, I have a D-Link DWL-G510 which requires a newer version of ndiswrapper than is available on the CD repositories. So, after installing ndiswrapper-utils, I uninstalled ndiswrapper-utils, removed configuration directories, and moved the source tarball of the newest ndiswrapper (1.5) to my desktop using a USB drive.

I have installed the linux-headers and build-essentials packages. However, when I try to run "sudo make" in the ndiswrapper directory (after I unzipped the tarball) I get the following error:

```
joshuaxls@solusek:~/ndiswrapper-1.5$ sudo make
make -C driver
make[1]: Entering directory '/home/joshuaxls/ndiswrapper-1.5/driver'
Can't find kernel sources in /lib/modules/2.6.12-9-386/build;
   give the path to kernel sources with KSRC=<path> arguement to make
make[1]: *** [prereq_check] Error 1
```

There's more after that, but it's just more of make bailing out.

I tried putting KSRC=/usr/src/linux-headers-2.6.12-9/ but that gave me another error (this is edited... I only put down the lines that I thought were important):

```
/bin/sh: /usr/src/linux-headers-2.6.12-9/scripts/gcc-version.sh: No such file or directory
make[2]: gcc-3.4: Command not found
make[2]: Entering directory '/usr/src/linux-headers-2.6.12-9'

   WARNING: Symbol version dump /usr/src/linux-headers-2.6.12-9/Module.symvers
                  is missing; modules will have no dependencies and modversions.

make[3]: scripts/Makefile.build: No such file or directory
make[3]: *** No rule to make target 'scripts/Makefile.build'.   Stop.
```

Can anyone help?

---

### Post by ofek on 2005-11-20
From what I saw I dont think you got gcc which means u need to type this in terminal:```
sudo apt-get install build-essential
```
I also think I saw that you don't have your kernel source which means that you need to find out which kernel you got and to install it through synaptics. There should be an howto for that.

---

### Post by joshuaxls on 2005-11-20
I did install build-essentials and the kernel sources. As for my first problem, I forget to create a link between /lib/modules/VERSION/build and /usr/src/linux-2.6.12-9. I am still having the gcc problem, however. I think that gcc-3.0 and gcc-4.0 and gcc are all valid commands on my system. How can I tell ndiswrapper to use one of those instead of gcc-3.4?

*EDIT:* I guess I could just create a symlink between gcc-4.0 and gcc-3.4. I'll try that.

---

### Post by joshuaxls on 2005-11-22
Any ideas?

I think it has to do with this line:
```
/bin/sh: /usr/src/linux-headers-2.6.12-9/scripts/gcc-version.sh: No such file or directory
```

Creating a symlink didn't work.

---

### Post by Colli on 2005-11-23
I had the same problem.

I just installed gcc-3.4 and gcc-3.4-base with the synaptic tool in ubuntu.  It seems to work even when the 4.0 version is installed.

---

### Post by az on 2005-11-23
I think you only need the most recent version of the windows driver (INF file) but you do not have to recompile ndiswrapper.  The one in Breezy works fine.

---

### Post by az on 2005-11-23
I think you only need the latest version of the windows driver (INF file) and not ndiswrapper.  The version in Breezy works fine.

---

### Post by joshuaxls on 2005-11-23
Well, I solved it. You're right, I needed gcc-3.4 since the Ubuntu kernel was compiled with gcc-3.4. I think it's kind of silly to compile the kernel with gcc-3.4 but not provide gcc-3.4 on the Installation CD. Basically, I have a laptop with the exact same kernel as my desktop, so I got gcc-3.4 on my laptop and made a .deb package of the ndiswrapper-1.5 sources. Then I moved the .debs to my dekstop and installed -- everything worked.

I needed ndiswrapper-1.3 or greater because my card did not work under ndiswrapper-1.1. Also, I didn't have a network connection on my desktop, so I couldn't just install gcc-3.4 on it.

Thanks for replying.

---

