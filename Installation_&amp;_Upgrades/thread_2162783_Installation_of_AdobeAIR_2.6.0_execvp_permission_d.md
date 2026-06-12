---
title: "Installation of AdobeAIR 2.6.0: execvp: permission denied"
date: 2013-07-15
forum: Installation &amp; Upgrades
---

### Post by zhangweiwu on 2013-07-15
Before I post, I read [Adobe's helpdesk document of how to install on 64-bit machines]("http://helpx.adobe.com/air/kb/install-air-2-64-bit.html") and [coomunity post on Ubuntu 12.04]("http://ooboontoo.blogspot.com/2012/04/how-to-install-adobe-air-26-in-ubuntu.html") and [ on Ubuntu 12.04 64-bit]("http://jeffhendricks.net/?p=68") and tried to follow their instruction as close as possible.

It do seems, the problem I found is unrelated to any of these instructions: these instruction assume it is easy to get a installer (text-based) user-interface and it is hard to go from there. The fact is I couldn't even run the installer:

```

(platform is Ubuntu 12.04 64-bit)
$ ls -lh ./AdobeAIRInstaller.bin 
-rwxrwxr-x 1 zhangweiwu users 16M Jul 16 10:24 ./AdobeAIRInstaller.bin
$ sudo ./AdobeAIRInstaller.bin 
execvp: Permission denied
$ file ./AdobeAIRInstaller.bin 
./AdobeAIRInstaller.bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.9, stripped

```

About 32-bit support libraries: I did install a bunch of them before even attempting the installer, and this error message is not what you typically would get if you don't have them.

Any ideas? Thanks.

---

### Post by zhangweiwu on 2013-07-15
Now I solved my problem on my own.

I mounted /tmp to tmpfs, to protect my SSD from wearing. For some reason, files on tmpfs are not executable, even if they are given such permission. What happened is Adobe's installer copied some files to /tmp/ and attempted to execute them there, and got Permission Denied.

The solution is to reboot the computer without /tmp/ on tmpfs, install Adobe Air. Now it works.

---

