---
title: "After upgrade to 10.04: Respawning home folder window"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by lastchancetosee on 2010-05-05
Hi,
I just upgraded to 10.04 and everything is working flawlessly except:

When I log in a nautilus window showing my home folder opens automatically. When I close it, it closes but immediately starts up again.

When I kill the process via commandline, an ever growing number of windows appears in my taskbar (but not really, ALT+Tab still shows only one), if I close one, a new one appears but the multitude one by one vanishes.

Like this:
```
user@host:~$ ps ax | grep nautilus
16390 ?        S      0:00 nautilus --sm-client-id 107fdefa892a3e3bbf12728821387520300000016320031 --sm-client-state-file /home/user/.config/session-state/nautilus-1273062736.desktop
16834 ?        Sl     0:00 nautilus --sm-client-id 10f79548d6d696c391126925996719040700000303250032 --sm-client-state-file /home/user/.config/session-state/nautilus-1273062737.desktop

```

Then I kill one of them (killing the other is identical to closing the window: A new one with a new PID appears):
```
user@host:~$ kill 16390
user@host:~$ ps ax | grep nautilus
17128 ?        S      0:00 nautilus --sm-client-id 10f79548d6d696c391126925996719040700000303250032 --sm-client-state-file /home/user/.config/session-state/nautilus-1273062737.desktop
18494 ?        Zl     0:00 [nautilus] <defunct>
18500 ?        R      0:00 nautilus --sm-client-id 107fdefa892a3e3bbf12728821387520300000016320031 --sm-client-state-file /home/user/.config/session-state/nautilus-1273062736.desktop

```

Now I have more and more windows opening in the taskbar. Quick, kill them!

```
user@host:~$ kill 18494
bash: kill: (18494) - No such process
user@host:~$ kill 18500
bash: kill: (18500) - No such process
```

No effect. But:

```
user@host:~$ kill 17128
```

Caught the right one. The hundreds of windows in the taskbar disappear one by one, leaving one newly appeared home folder on my screen:

```
user@host:~$ ps ax | grep nautilus
19917 ?        S      0:00 nautilus --sm-client-id 107fdefa892a3e3bbf12728821387520300000016320031 --sm-client-state-file /home/user/.config/session-state/nautilus-1273062736.desktop
19918 ?        S      0:00 nautilus --sm-client-id 10f79548d6d696c391126925996719040700000303250032 --sm-client-state-file /home/user/.config/session-state/nautilus-1273062737.desktop
```

I guess it's here to stay.
Ideas, anyone?

---

### Post by lastchancetosee on 2010-05-06
Logout, reboot or deleting the session-state files referenced in the output of ps ax doesn't help, btw.
The error is completely reproducable.

---

### Post by tobler on 2010-05-11
Hi

I have same issue. When I login then Nautilus home folder is always 
opened. It has closed nicely when I clicked close button. Yesterday my 
MacMini hanged when I tried to put it suspend mode. And now Nautilus is 
respawning back just like you do.

I followed PPID and it is gnome-session which is respawning it. I don't 
know enough about gnome-session where it's reading configuration or 
programs to be respawned.

Perhaps old Gnome configuration is messing with current user account? I think if I rename my home folder and create new then I'll get completely new configuration. And then move back my original files, except .gnome* configurations.

---

