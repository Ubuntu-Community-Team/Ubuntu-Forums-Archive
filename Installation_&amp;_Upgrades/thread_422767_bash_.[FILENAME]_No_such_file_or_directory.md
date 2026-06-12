---
title: "bash: ./[FILENAME]: No such file or directory"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by jsym on 2007-04-25
Hello ladies and gents,

I tried slogging through the upgrade chain from Hoary to Feisty, but everything crashed part way through.  I formatted all my hard drives and started from a fresh install.  Everything is working perfectly EXCEPT the most important part--I cannot install the stats program that I built the computer to run in conjunction with a simulation for my thesis.  Here's how far I can get:

```

$ mkdir splus
$ cd splus
~/splus$ zcat /media/cdrom/SPLUS.TZ | tar xvf -

<Insert a whole lot of files unpacking here>
<Insert a whole lot of files unpacking here>
<Insert a whole lot of files unpacking here>

~/splus$ ./HOSTINFO

~/splus$ bash: ./HOSTINFO: No such file or directory
 
```

It's not just HOSTINFO that has the problem, but ANY executable that comes with the package.  This error does not occurs with scripts that came with the package or with executables that did *not* come with the package (It works for those I create myself and those that come with other programs).  I am confident that all my permissions are properly set.  It happens if I install as root or if I try to run it as root.  I have installed this program before on this computer (and it worked ) and I have installed it on different computers (and it worked there too).

I can SEE the file.  I can TOUCH the file.  Why can't I USE the file? 

:confused: 

Any help would be greatly appreciated.

---

### Post by jsym on 2007-04-25
This may be an issue with my 64-bit machine missing some 32-bit libraries (see [http://ubuntuforums.org/showthread.php?p=2535759]("http://ubuntuforums.org/showthread.php?p=2535759") ).

I will see about installing these libraries (whatever they are) and report back.

Suggestions about what libraries to install are welcome!

---

### Post by jsym on 2007-04-25
SOLVED! \\:D/ 

The missing libraries are part of the Linux Standard Base (see [http://www.linux-foundation.org/en/LSB]("http://www.linux-foundation.org/en/LSB")) and can be installed simply by choosing **lsb-core** in synaptic.

Hope this helps someone out.

---

### Post by mystuff on 2008-04-24
And if that doesn't work (it didn't for me) then try:

```
sudo apt-get install ia32-libs
```

---

