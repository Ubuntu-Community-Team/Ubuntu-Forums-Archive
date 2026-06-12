---
title: "Error while installing Ubuntu"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by Delta62 on 2008-08-06
I recently tried to install ubuntu onto my laptop computer. After booting to the CD, I can see the ubuntu logo with the bouncing status bar. The progress bar will begin to fill, but as it is about to complete, I get a black screen with white text saying the following:

The programs included with the ubuntu system are free software;
the exact distribution terms for each program are described in the 
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with absolutely no warranty, to the extent permitted by applicable law.

To access official ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
To run a command as an administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

Then I get a prompt that looks very much like the prompt found in terminal, reading:

ubuntu@ubuntu:~$

I have run a memory test and checked the disk for problems, both tests turned up nothing suspicious.
I have also tried installing xubuntu, with the exact same results.

Thanks for any help in advance.

---

### Post by tuxxy on 2008-08-06
Have you tried starting the GUI

```
startx
```

---

### Post by Delta62 on 2008-08-06
If I run the startx command, I get an error message:

Fatal server error:
no screens found

waiting for x server to begin accepting connections
giving up
xinit: connection reset by peer (errno104): unable to connect to X server
xinit: no such process (errno 3): server error
ubuntu@ubuntu:~$

---

