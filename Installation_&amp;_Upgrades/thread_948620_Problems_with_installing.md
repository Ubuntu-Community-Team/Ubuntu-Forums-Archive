---
title: "Problems with installing"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by Hydrothrax on 2008-10-15
Hi,

I'm having some problems with installing things, like firefox plugins. while trying to install Flash Player, I got:

E: ERROR: could not create configuration directory /home/root/.synaptic - mkdir (2 No such file or directory)

I'm still sorta new to Linux, and have had similar difficulties while installing other applications. Any help would be appreciated. thanks! :)

---

### Post by mssever on 2008-10-16
> **Hydrothrax said:**
> Hi,

I'm having some problems with installing things, like firefox plugins. while trying to install Flash Player, I got:

E: ERROR: could not create configuration directory /home/root/.synaptic - mkdir (2 No such file or directory)

I'm still sorta new to Linux, and have had similar difficulties while installing other applications. Any help would be appreciated. thanks! :)
Some questions: First, can you install from the command line? ```
sudo aptitude install packagename
``` That can help narrow down the problem.

Second, I'm wondering why you're getting an error about /home/root (which by default doesn't exist). Please post the line beginning "root" from /etc/passwd.

---

### Post by Hydrothrax on 2008-10-19
> **mssever said:**
> 
Second, I'm wondering why you're getting an error about /home/root (which by default doesn't exist). Please post the line beginning "root" from /etc/passwd.

..............um...what am I supposed to do? 

[sorry for being so stupid D8 I blame it on having used Windows for so long...]

EDIT: Nevermind, I think I solved the problem from here: [http://ubuntuforums.org/showthread.php?t=699130]("http://ubuntuforums.org/showthread.php?t=699130") Thanks anyway! ^^

---

