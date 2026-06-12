---
title: "OS migration: user data and programs"
date: 2016-12-11
forum: Installation &amp; Upgrades
---

### Post by erotavlas on 2016-12-11
Hi,
I'm going to buy a new SSD for my notebook. At the moment, I'm using ubuntu 16.04 lts 64 bit and I'm going to install ubuntu mate 16.04 lts 64 bit on the SSD.
I would like to migrate all the user data and the program. For the first, it should be enough to copy the /home/user with cp --preserve=mode. For the second I found different, but similar ways:
In the source machine:
```

sudo dpkg --get-selections > ~/pkglist

```
In the destination machine:
```

sudo dpkg --set-selections < ~/pkglist && sudo apt-get --show-upgraded dselect-upgrade

```

or in the source machine:
```

sudo dpkg --get-selections | sed "s/.*deinstall//" | sed "s/install$//g" > ~/pkglist

```

and in the destination machine:
```

sudo dpkg --set-selections < ~/pkglist && sudo apt-get --show-upgraded dselect-upgrade

```

They should solve the same task by reinstalling in the destination machine only the programs effectively installed in the source machine.
Is there any preferred way?
Moreover, since the source machine is ubuntu with gnome-session-fallback and the destination machine is ubuntu mate, could be some differences on installed packages?
Is there any software that manage this task?

Thank you

---

### Post by oldos2er on 2016-12-11
I would prefer to use rsync rather than cp for your /home/user data. Rsync can more easily recover from any interruptions, so it's somewhat safer.

If you're using any PPAs, make sure you enable them on the destination machine before running the dpkg commands.

Any modified files in /etc ?

---

### Post by oldfred on 2016-12-11
I think if you normally houseclean old install and run the sudo apt-get autoremove, there will not be any packages that do not say install.
I use the one without grep but quickly review list. Since I usually am installing in a newer version, I remove any old kernels and sometimes find some other things I really did not want. It is just a text file, but long.
I sometimes have issues getting the reinstall to work, some sort of error, but eventually it does work.

Because I typically have multiple installs, and usually not the same configuration, I keep /home inside my / (root) but have all my data in a large data partition. Then I can mount data in all installs without worrying about configuration setting issues.

---

### Post by ian-weisser on 2016-12-11
I simply start using the new DE's default install, installing other applications as needed.
get-selections/set-selections will drag in the entire old DE, which I did not want.

---

### Post by erotavlas on 2016-12-12
> **oldos2er said:**
> I would prefer to use rsync rather than cp for your /home/user data. Rsync can more easily recover from any interruptions, so it's somewhat safer.

If you're using any PPAs, make sure you enable them on the destination machine before running the dpkg commands.

Any modified files in /etc ?

You are right is better to use rsync with option -p. Yes, I also copy /etc/apt/sources.list and /etc/apt/sources.list.d/ and any other files in opt. Is there any clever way to find which files I change in /etc?

> **oldfred said:**
> I think if you normally houseclean old install and run the sudo apt-get autoremove, there will not be any packages that do not say install.
I use the one without grep but quickly review list. Since I usually am installing in a newer version, I remove any old kernels and sometimes find some other things I really did not want. It is just a text file, but long.
I sometimes have issues getting the reinstall to work, some sort of error, but eventually it does work.

Because I typically have multiple installs, and usually not the same configuration, I keep /home inside my / (root) but have all my data in a large data partition. Then I can mount data in all installs without worrying about configuration setting issues.

My fear is that moving from different GUI (same OS) and using the generate file from sudo dpkg --get-selections > ~/pkglist, even if I use sudo apt-get autoremove, will install unnecessary software.
What do you think about this fact?

> **ian-weisser said:**
> I simply start using the new DE's default install, installing other applications as needed.
get-selections/set-selections will drag in the entire old DE, which I did not want.

So, do not you recommend to do this? What do you suggest in order to speed up the process?

Thank you

---

### Post by oldfred on 2016-12-12
I also use an install script that installs the main applications that I want. So if testing in another install, I may not install all the apps from my export, but just those that I use a lot that are in my script.

---

### Post by oldos2er on 2016-12-12
> Is there any clever way to find which files I change in /etc?

Possibly, but I'm not a bash scripting guru so I can't give you a clever command to run. Assuming you haven't kept a list of changed files? Depending on how far back your bash history extends, you could run ```
history | grep /etc
``` which will show every command containing "/etc". If you worked in a GUI this is moot.

---

### Post by erotavlas on 2016-12-13
> **oldfred said:**
> I also use an install script that installs the main applications that I want. So if testing in another install, I may not install all the apps from my export, but just those that I use a lot that are in my script.

Yes, I also use this [install script.]("https://gist.githubusercontent.com/erotavlas85/4fcce697d3bfcba62af7/raw/38ec1993c3f4b33728ea76febe4fb8a9fe9adfe4/update_ubuntu.sh") I would like to know if exists any way to list all installed software in clever way.

---

### Post by erotavlas on 2016-12-13
> **oldos2er said:**
> Possibly, but I'm not a bash scripting guru so I can't give you a clever command to run. Assuming you haven't kept a list of changed files? Depending on how far back your bash history extends, you could run ```
history | grep /etc
``` which will show every command containing "/etc". If you worked in a GUI this is moot.

Thank for the hint, but it is not a viable option.

---

