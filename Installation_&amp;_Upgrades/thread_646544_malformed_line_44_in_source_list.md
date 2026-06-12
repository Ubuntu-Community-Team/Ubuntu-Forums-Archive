---
title: "malformed line 44 in source list"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by arnicainthemembrane on 2007-12-21
I think I caused this in the process of installing codecs for mplayer. When I went to install updates I got this:

[I]An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 44 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'[/I]

And when I attempted to access synaptic:

[I]E: Malformed line 44 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.[/I]

Synaptic won't open, so I can't go to the repository dialog.

Any help, or pointers in the right direction, appreciated.

---

### Post by taurus on 2007-12-21
There is something wrong with line 44 in your /etc/apt/sources.list.  So, you need to edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and remove that line from it.  Then, save it and run

```
sudo apt-get update
sudo apt-get upgrade
```
Otherwise, just post it here.

```
cat /etc/apt/sources.list
```

---

### Post by arnicainthemembrane on 2007-12-21
i did remove line 44 and saved, but when i went to  update and upgrade I got the same error message I get when I try to install some codecs:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I don't know what process might be using it, and I don't know how to figure out so I typically turn off the computer then reboot to see if the error message is still there.

---

### Post by taurus on 2007-12-21
If you have synaptic or Add/Remove open, please shut it down first before you run those two commands from a terminal.

---

### Post by arnicainthemembrane on 2007-12-21
oh. duh. right. thanks. problem solved.

---

