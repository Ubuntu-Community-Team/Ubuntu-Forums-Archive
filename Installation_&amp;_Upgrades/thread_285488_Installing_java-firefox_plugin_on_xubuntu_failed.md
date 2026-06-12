---
title: "Installing java-firefox plugin on xubuntu failed"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by textguru on 2006-10-26
I am trying to install j2SE from the deb files that I have on the apt archives (see list on the code of these files that I've copied on my desktop). 

```
ubuntu@mypc:~/Desktop$ ls
libflashplayer.so                  sun-java5-jre_1.5.0-06-1_all.deb
sun-java5-bin_1.5.0-06-1_i386.deb  sun-java5-plugin_1.5.0-06-1_i386.deb

```

I've installed it thru dpkg (I have tried sudo dpkg -i sun*.deb before doing the command below due to error on firefox plugin)

```
ubuntu@mypc:~/Desktop$ sudo dpkg -i sun-java5-plugin_1.5.0-06-1_i386.deb
(Reading database ... 54283 files and directories currently installed.)
Preparing to replace sun-java5-plugin 1.5.0-06-1 (using sun-java5-plugin_1.5.0-06-1_i386.deb) ...
Unpacking replacement sun-java5-plugin ...
dpkg: dependency problems prevent configuration of sun-java5-plugin:
 sun-java5-plugin depends on sun-java5-bin (= 1.5.0-06-1); however:
  Package sun-java5-bin is not installed.
dpkg: error processing sun-java5-plugin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java5-plugin
ubuntu@mypc:~/Desktop$
```

What do I need to do to install java plugin in firefox

---

### Post by magicfab on 2006-10-26
It's rare you have to use any manually downloaded .debs ...

In Gnome (Ubuntu):

1. Open the "applications" menu
2. Open the "Add/remove" application
3. Search "Java" - the first result should be "Sun Java 5.0 plugin"
4. install it by checking the box, and clicking [OK]

---

### Post by textguru on 2006-10-27
> **magicfab said:**
> It's rare you have to use any manually downloaded .debs ...

In Gnome (Ubuntu):

1. Open the "applications" menu
2. Open the "Add/remove" application
3. Search "Java" - the first result should be "Sun Java 5.0 plugin"
4. install it by checking the box, and clicking [OK]

I am using xubuntu. I have synaptics. According to the Broken filters, I need to accept license agreement. How to do that on dpkg command?

---

### Post by magicfab on 2006-10-27
add/Remove is also in Xubuntu. Look for it in the menus.

dpkg will [prompt you if it needs any confirmations for licencing, etc, however you should be able to do this in synaptic, by searching for "java" in the package name.

---

### Post by Kelnoky on 2006-11-05
I have the same problem and synaptics is no good in this case. When it tries to install the package it wont move on and in the "details" window you can see that you have to accept the license but of course you cant click in there...

So what to do?

---

### Post by esaym on 2006-11-05
also remember that the java plugin has to be sym linked into the firefox plugin directory, you can not just copy the plug in into the directory like you can with the pdf and mplayer plugins.  Usually the install does all this for you though.  Looks like you are just having trouble getting the plugin, but once you got if it doesn't work, check what I have typed above :mrgreen:

---

### Post by textguru on 2006-11-05
I just resolved it bu using the --unpack option of dpkg command. It really works!

---

### Post by DavidMaas on 2006-11-17
You actually can install java on xubuntu using the Synaptic Package Manager
First select Sun Java Plugin
Second, when the terminal tells you that you have to accept licence then don't click!! but use arrows and enter-button

It should then install

Greetz, Dave

---

### Post by mattdt0 on 2006-12-28
> **DavidMaas said:**
> You actually can install java on xubuntu using the Synaptic Package Manager
First select Sun Java Plugin
Second, when the terminal tells you that you have to accept licence then don't click!! but use arrows and enter-button

It should then install

Greetz, Dave

Hello, 
  Newbie alert here.  I've been trying to get an install of linux to run on my old system.  Have Xubuntu up and running, but am having trouble getting Java installed.  I think I could do it if I could just get 'Sun Java Plugin' to actually show up in Synaptic Package manager. ](*,) 

If someone could tell me how to do that, I'd be appreciative...

Matt

---

