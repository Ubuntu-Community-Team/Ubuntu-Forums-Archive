---
title: "Taking things slowly..."
date: 2005-10-25
forum: Installation &amp; Upgrades
---

### Post by catastrophee on 2005-10-25
Im having a total nightmare getting things working on my new system here. Nothing works damnit!!!

Anyway I think my problem is the extra repositories! I believe so because I cannot get java runtime installed and when i open synaptic i get this error message. I can still use synaptic and after i added the repositorys using the guide it shows more download options. 

The following problems were found on your system :

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)

So the first step here is to ensure my extra repositories are added correctly.... then installing jre-1_5_0_05-linux-i586.bin

Feel free to check my previous threads if ya wanna see what problems im currently dealing with... I got no further replies to my other threads.

---

### Post by catastrophee on 2005-10-25
Also when trying to apt-get things such as the JRE and Amule in the terminal i got these error messages.

root@ubuntu:/home/ubuntu # sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package sun-j2re1.5
root@ubuntu:/home/ubuntu # java -version
bash: java: command not found


After running apt-get update I get the same error!

W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by TristanMike on 2005-10-26
Do not fret my friend. Two things, your repositories look off, "mirrormax" is no longer used...you must replace the mirrormax ones. For a really nicely laid out sources.list with all the essentials, see [here.](http://paste.ubuntulinux.nl/969) You will need to uncomment the appropriate lines or just replace the bacports, either way, this is current. Don't forget to save and ```
sudo apt-get update
```

Now for java, it's been removed for legal reasons so you have two choices. You can grab the .deb [here](http://giannaros.org/public/hoarydebs/) (that would be the j2re one and not the sdk one, unless you're a developer in which case...anyway, I digress) and a simple ```
sudo dpkg -i foo.deb
```Where "foo.deb" is the complete package name. Or, you could have some fun and install it manually by following the instructions [here.](https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca)

Then when all that's done, a```
sudo apt-get install amule
```should give you that one.

Note, it might be a good idea to only keep the "extra's" repository enabled only when you're going to use something from it. A list of all packages for the base/universe/mulitverse and official backports can be found [here.](http://packages.ubuntu.com/)

EDIT: I just noticed you had tried installing the bin, if you check the manual install link I posted above, it will tell you how to install the .bin file.

---

