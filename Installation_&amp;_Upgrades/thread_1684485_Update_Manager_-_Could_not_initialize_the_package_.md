---
title: "Update Manager - Could not initialize the package information"
date: 2011-02-09
forum: Installation &amp; Upgrades
---

### Post by Ramot on 2011-02-09
Hi all,

My Update Manager and Synaptic Package Manager are showing me the following massage when I try to open them:

[INDENT][I][B]Could not initialize the package information
An unresolvable problem occurred while initializing the package information.
Please report this bug against the 'update-manager' package and include the following error message:
'E:Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list, E:The list of sources could not be read.'[/B][/I][/INDENT]

Any idea how to solve this issue?

---

### Post by zvacet on 2011-02-09
In terminal type

```
gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
```

Copy and paste output here.

---

### Post by Ramot on 2011-02-09
This is the output:
[B][I]deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) lucid main
n[/I][/B]

---

### Post by zvacet on 2011-02-09
It should be 

> deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) lucid main

So  type in terminal

```
sudo gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
```

and delete **n**.Save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Ramot on 2011-02-10
So simple. So nice. So grateful.
Thnx **zvacet**, it is working perfect now.

---

### Post by vmguru007 on 2011-06-15
Hi,

In case for anyone the above fix did not work, I have found an article that helped me fix the same problem a bit differently. It can be found at:

[http://www.linux2aix.com/linux/ubuntu/ubuntu-1104-update-manager-could-not-initialize-the-package-information.html](http://www.linux2aix.com/linux/ubuntu/ubuntu-1104-update-manager-could-not-initialize-the-package-information.html)

Please confirm the error exactly match the error screenshot on the article before proceeding with the fix, as mine was an exact match.

Enjoy,
Erick
[http://www.TSMGuru.com](http://www.TSMGuru.com)

---

### Post by adityaghante on 2011-10-06
gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list

is not working for me it just opens up a blank text editor

---

