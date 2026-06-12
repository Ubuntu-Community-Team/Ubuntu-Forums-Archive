---
title: "Cannot install ia32-libs in Ubuntu 12.04"
date: 2014-02-11
forum: Installation &amp; Upgrades
---

### Post by aitor2 on 2014-02-11
I use Ubuntu 12.04 on a 64-bit computer. I have installed Eclipse to develop Android applications, but when I try to run a project, I get this error:
```

[2014-02-11 17:54:33 - adb] Unexpected exception 'Cannot run program "/home/aitor/adt-bundle-linux-x86_64-20131030/sdk/platform-tools/adb": error=2, No existe el archivo o el directorio' while attempting to get adb version from '/home/aitor/adt-bundle-linux-x86_64-20131030/sdk/platform-tools/adb'

```

When I googled for the solution, everyone said that the ia32-libs package is missing (since my computer is 64-bit). So I tried to install it and this is what I got:

```

$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
E: Unable to correct problems, you have held broken packages.

```

I have tried everything related to apt-get:
```

$ sudo apt-get install -f
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get autoremove
$ sudo apt-get clean
$ sudo apt-get autoclean

```

and every other "solution" I found on several forums. I also tried removing two PPA repositories from the list.

Synaptic says I don't have broken packages but when I try to install something, it finds unmet dependencies.

Finally, I am not allowed to make a distribution upgrade for work reasons.

What is going on with the packages? Can you help me?

If you need any other information, let me know.

Thanks in advance.

---

### Post by ubfan1 on 2014-02-11
Try installing the ia32-libs-multiarch package too.  I usually install both togehter with no problems.

---

### Post by aitor2 on 2014-02-12
I tried, but also gives an error:
```

$ sudo apt-get install ia32-libs-multiarch ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 ia32-libs-multiarch:i386 : Depends: gstreamer0.10-plugins-good:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by shantiq on 2014-02-12
hi aitor had this situation 3 days ago


this does the same as ia32 apparently

> [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get  install openjdk-7-jre:i386[/FONT][/COLOR][COLOR=#000000][B][RIGHT][/RIGHT]
[/B][/COLOR]


---

