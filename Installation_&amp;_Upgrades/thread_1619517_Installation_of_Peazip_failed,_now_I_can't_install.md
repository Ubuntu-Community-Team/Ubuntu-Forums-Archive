---
title: "Installation of Peazip failed, now I can't install anything."
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by Habeouscorpus on 2010-11-11
I was trying to install a RAR extractor called Peazip ([http://peazip.sourceforge.net/](http://peazip.sourceforge.net/)) I selected the 64-bit package (I run Lucid) and went for it. Everything extracted ok, and the package met all requirements. However, during the installation process, it hung. No movement. I closed out of the installation, and restarted, to attempt a second try. 

Now, when I try to install anything: 

```
<username>@ubuntu:~$ sudo apt-get install cheese
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

Assistance?


(Only been running this OS for, oh, what, a week? And I already hosed it up! :P)

---

### Post by sikander3786 on 2010-11-12
Close any other programs like Software Center, Synaptic or Update Manger. They can't be run simultaneously.

The error might have disappeared till now due to a reboot :-)

---

### Post by Giorgio tani on 2010-11-16
I'm afraid, I've tried to replicate the problem on my test machines without luck, it seems the installation systems of your machine had had some sort of problem.

My PeaZip's DEB is a general purpose package that is intended to work on a wide pool of DEB based systems and it is not targeted to a specific distribution or version, so it uses only most basic features of DEB package system (it does nothing more than copying program's files and shortcuts in standard paths, and deleting them is enough for removing PeaZip).

If some of you is aware of a third part package for DEB systems, the suggestion is very welcome, I'll link them in PeaZip's homepage as more narrow-targeted packages would be a good choice for users.

By the way, the binaries in my packages are compiled for 32 bit so requires ia32-libs to run (as reported in homepage).
64 bit executables can be compiled from sources; it is written with Lazarus/FPC, requires latest stable bersion 0.9.28.2 to be compiled (it works or 0.9.28 too).
Please note that also underlying engines (p7zip, freearc, *paq etc) are compiled for 32 bit so they will need ia32-libs anyway, or to be recompiled (sources are available from respective authors).

---

### Post by Habeouscorpus on 2010-11-16
Hey, thanks! I tried that, and it worked. I'll keep that piece of advice in mind for next time.

---

