---
title: "New kernel to customized Xubuntu live cd"
date: 2006-10-24
forum: Installation &amp; Upgrades
---

### Post by Xirkka on 2006-10-24
Hello world!

For some time I have customizing Xubuntu live cd and my project is almost complete. But cd is s-l-o-w so I need to optimize it. To do that I need to patch kernel with openlog-pacth. Well I patched kernel and used [http://ubuntuforums.org/showthread.php?t=84174&highlight=kernel+vanilla](http://ubuntuforums.org/showthread.php?t=84174&highlight=kernel+vanilla) as my guide to compile kernel. So far so good, but after I installed brand new kernel to live cd and tried to run it with Qemu, loading suddenly stops and this text came up:

```
WARNING: Couldn't open directory /lib/modules/2.6.15-26-386: No such file or directory
FATAL: Could not open /lib/modules/2.6.15-26-386/modules.dep.temp for writing: No such file or directory
0

BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
#
```

It has something to do with old kernel because the new kernel was version 2.6.16... but what? What should I do to fix problem?

I'm just a newbie with Linux and I know that this is big challenge to me but I have decided to do this and I'm also going to do this ;)

---

### Post by Xirkka on 2006-10-26
OK it looks like reply button works so the question or timing or my karma must be bad...

Actually I did take one step forward in this project yesterday: now the error message is almost same but kernel has changed to new one. modules.dep.temp is still missing and I checked, it's really missing.

I don't know what to do so (R2-D2 starts showing blueish picture of me) help me Ubuntu Forums people, you are my only help. ;)

---

