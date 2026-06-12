---
title: "Reload configuration file without restart the computer (source command)"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by rpjanaka on 2007-07-20
i heart about "source" command which can reload a configuration file like .bashrc, without restarting the computer.
i am using Ubuntu 7.04

in my system the "man source" command does not work. so there were no way to get compleat description about this.

if anyone can please let me know how can i use this command, 
if it is possible, for which type of configuration files, it can do etc...


if i am incorrect with the task of the source command, pleas let me know what is the correct meaning of it

---

### Post by ddrichardson on 2007-07-20
.bashrc is read every time a terminal is opened, so no need to reboot.

[The Source Command]("http://learnlinux.tsf.org.za/courses/build/shell-scripting/ch10s02.html")

---

### Post by ppietryga on 2007-07-20
source is basically used to run a script without running new shell.

It can be used like you said to reread  .bashrc like this:
```
source .bashrc
```
or like this:
```
. .bashrc
```
if you made some changes to it and for some reason don't want to leave your terminal window or logout/-in.

I personally don't see any good reason for not leaving terminal window (or just runing new one, .bashrc is reread evry time a terminal is opend as said above). And if you want any application to reread it's configuration there are some other ways, like:
- restart your application
- use signals, like:
```
 killall -SIGUSR1 conky
```
or
```
killall -SIGUSR2 fluxbox
```
the using of <sigs> depends on wether:
- the developer impleneted the signals usage
- the developer deciding how the <sigs> are implemented (different <sigs> for conky and fluxbox and that's only 2 programs)

---

