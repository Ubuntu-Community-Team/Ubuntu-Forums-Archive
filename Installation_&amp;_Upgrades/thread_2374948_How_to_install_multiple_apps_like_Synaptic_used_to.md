---
title: "How to install multiple apps like Synaptic used to?"
date: 2017-10-20
forum: Installation &amp; Upgrades
---

### Post by The Bright Side on 2017-10-20
Hey guys! I heard Synaptic won't run anymore in 17.10 due to Wayland.

Whenever I set up a new system, I install Synaptic first. With it, I can just tick all the apps I want on my PC, start the installation, grab a cup of tea and when I'm back, all my apps are installed.

How do I do this now that Synaptic will no longer work? I thought about doing it via *sudo apt install package1 package 2 etc.*, but I have trouble finding out the names of all the packages. For instance, the package name for mkvtoolnix is called, "mkvtoolnix-gui". Do you know the quickest way to find all those package names?

Alternately, can you think of any package manager that lets me tick apps like Synaptic did?

P.S.: bonus question... I also heard gparted won't run on Wayland. What do you guys propose to use instead? Also, NVidia drivers seem to be a problem as well. Bit frustrating when new Ubuntu versions break stuff we've been using... I'm not sure I even wanna update now :-/

---

### Post by ajgreeny on 2017-10-20
Synaptic will run fine in wayland but it does need a bit of a workround to get it running.

See [https://ubuntuforums.org/showthread.php?t=2367294&highlight=synaptic+wayland](https://ubuntuforums.org/showthread.php?t=2367294&highlight=synaptic+wayland) for a way round this.
I am already using synaptic without a problem after adding that mentioned command to a script and adding it to the session autostart list.

---

### Post by The Bright Side on 2017-10-20
Ah, that's great news. Thanks for clarifying, much appreciated! When I get around to installing 17.10, it'll be good to know I have that option. I will mark this thread as SOLVED until then.

---

### Post by kurt18947 on 2017-10-20
I have two accounts, one user and one with sudo privileges that I use only for administrative purposes. I have different wallpapers on each account so I can tell which is which. Ubuntu 17.10 has a means to select Wayland or Xorg. I have the sudo account set to default to Xorg, the user account defaults to Wayland. Synaptic seems to work fine using Xorg. Logging out or user switching both seem stable.

---

