---
title: "How to install .linux file?"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by shadowofblood on 2010-11-26
Running Ubuntu 10.10

I set the permissions on cacaoweb.linux to allow executing as a program.

When I use the command:
```
/home/user/cacaoweb.linux &
```I get an error saying:
> [1] 3478
user@ubuntu:~$ bash: /home/user/cacaoweb.linux: No such file or directory

[1]+  Exit 127                /home/user/cacaoweb.linux
However, the file is there and the name is correct.  Any ideas?

UPDATE: When running the command with "Sudo", I get the following:
> sudo /home/user/cacaoweb.linux &
[1] 6308What does that mean?

---

### Post by Cheesehead on 2010-11-26
See [http://forum.cacaoweb.org/index.php?topic=64.0]("http://forum.cacaoweb.org/index.php?topic=64.0")

When running as sudo, the returned number is the PID number, which means it's running.

---

### Post by shadowofblood on 2010-11-26
That's what I thought, but it doesn't show up under the system monitor.

And when I try to visit "http://127.0.0.1:4001/index.html", I get an error saying:
"Firefox can't establish a connection to the server at 127.0.0.1:4001."

Also, I get the "No such file or directory" error stated in the first post.

---

### Post by zsiggatron on 2013-02-15
Alternately, try these steps :

  1) open "Terminal Emulator" *

  2) navigate to the containing folder **

  3) type "sudo chmod 777 cacaoweb.linux" ***

  4) enter your superuser password if prompted

  5) type "gksu thunar" ****

  6) right click on "cacaoweb.linux"

  7) click "execute"

  8) open link [http://127.0.0.1:4001/index.html](http://127.0.0.1:4001/index.html) in your preferred browser

If interested in details and explanation related to the steps, surf on related sites :

* [http://bitaffair.com/2012/01/xubuntu-quickly-opening-a-terminal-window-without-using-the-mouse/](http://bitaffair.com/2012/01/xubuntu-quickly-opening-a-terminal-window-without-using-the-mouse/)

** [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

*** [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

**** [http://ubuntuforums.org/showthread.php?t=898727](http://ubuntuforums.org/showthread.php?t=898727)

---

### Post by oldos2er on 2013-02-15
Old thread closed.

---

