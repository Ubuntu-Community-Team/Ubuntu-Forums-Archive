---
title: "X11 error"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by Mr G on 2007-06-07
**This post could be related to an Ubuntu bug filed at**: Mr G [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**Was loading Feisty on a different machine and I got the following X11 error:**

Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational: (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

(==) log file: "/var/log/xorg.0.log", Time: Mon Jun 4 18:48:38 2007

(==) using config file: "/etc/X11/xorg.conf"


**Absolute beginner, so what do I do to fix this error and proceed with installation?**

---

### Post by benanzo on 2007-06-07
That doesn't actually show an error.  That is just the *key* for the error log so you can search through it quickly and find errors or warnings etc.

Open a terminal **Applications -> Accessories -> Terminal** (if in a desktop session) and do this:
```
cat /var/log/Xorg.0.log | grep EE
```
otherwise just do it at a console if X wont start.
That will show you the actual errors.  Paste that info back here.

What kind of problem are you having?  Does your desktop session start up?

---

### Post by Mr G on 2007-06-07
No, the Desktop session won't even start.  Can I enter the commands that you suggested from one of the command lines that are available after the error message window closes?

---

### Post by NeoLithium on 2007-06-07
You bet you can :)

---

### Post by benanzo on 2007-06-07
It will be a little tricky for you to get the error messages out so you can paste them here, but I'll give you a quick run down on how to do that.

If you have an external USB thumbdrive or other disk (or if you have write access to the other system if it's dual-boot) you can copy the Xorg error log to that so you can post it up here.

If you plug in a USB thumb drive while at the console it will mount in **/media** so it might show up as **/media/disk**.

While at the console, change into the directory of that USB disk:
```
cd /media/disk #if that's where it's mounted
```
Then copy the Xorg error log to that disk:
```
cp /var/log/Xorg.0.log /media/disk
```
Or you can just copy the actual errors in the log:
```
cat /var/log/Xorg.0.log | grep EE > /media/disk/Xorg_errors.txt
```

Then get that text file off on a different system and post them here.

---

