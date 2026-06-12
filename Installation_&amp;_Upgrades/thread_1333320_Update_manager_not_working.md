---
title: "Update manager not working"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by David Steele on 2009-11-21
I'll settle for any fix on this.  re-install.  Format hard drive.  Anything.  I just want my lovely computer to work again!

I am having severe problems with update manager-

I get the message:

[B]Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
[/B]

Also, Synaptic gives the following message:

[B]E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.[/B]

Report?  Who to?  I love Ubuntu being free, but I wish there was a customer service department I could call for things like this!

---

### Post by mac9416 on 2009-11-21
Howdy, David,

A package list file must be corrupted. Try running these commands...

```
$ sudo rm -R /var/lib/apt/lists/*  # Clear out the APT lists cache
$ sudo apt-get update  # Fill it agai
```

Good luck!

---

### Post by David Steele on 2009-11-22
Thanks so much for helping.

I've managed the following so far:

(user name)@(computer name):~$ sudo rm -R /var/lib/apt/lists/*
[sudo] password for (username): 
(user name)@(computer name):~$ sudo apt-get update
E: Lists directory /var/lib/apt/lists/partial is missing.


I feel like I'm getting somewhere....  Just not sure where, yet !

---

### Post by Soul-Sing on 2009-11-22
hmm the list should be automat. (re)create by apt...

and this? : ```
sudo mkdir -p /var/lib/apt/lists/partial
```

---

### Post by mac9416 on 2009-11-22
Sorry, that was my bad, David. The command should have been 'sudo rm /var/lib/apt/lists/*'. I've never learned BASH like I know I should. leoquant's command will get you back on track though. Good luck!

---

### Post by David Steele on 2009-11-23
Wow.  That seems to have covered it.  All kinds of things are happening and the update manager has kicked in.

Magic.  Can I have next week's lottery numbers now please?

Thanks very much to both of you.

---

