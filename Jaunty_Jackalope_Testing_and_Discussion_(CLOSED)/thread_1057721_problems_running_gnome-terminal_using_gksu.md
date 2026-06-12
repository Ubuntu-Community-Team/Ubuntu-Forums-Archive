---
title: "problems running gnome-terminal using gksu"
date: 2009-02-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by maciu on 2009-02-02
Hi,

I have a problem running gnome-terminal using gksu here is the output:

```
maciu@monster:~$ gksu -d -S gnome-terminal
No ask_pass set, using default!
xauth: /tmp/libgksu-G23bwc/.Xauthority
STARTUP_ID: gksu/gnome-terminal/19666-0-monster_TIME2311338
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: gnome-terminal
buffer: -Failed to contact the GConf daemon; exiting.-
brute force GNOME_SUDO_PASS ended...
No password prompt found; we'll assume we don't need a password.
Failed to contact the GConf daemon; exiting.xauth: /tmp/libgksu-G23bwc/.Xauthority
xauth_env: /home/maciu/.Xauthority
dir: /tmp/libgksu-G23bwc
maciu@monster:~$ 

```

Ps. Other apps run fine with gksu, any ideas why it fails to contact the Gconf daemon ?

---

### Post by jfernyhough on 2009-02-02
I imagine it's because GConf isn't running for root.

However, why do you want to run gnome-terminal as root? What's wrong with 
$ sudo -i 
?

---

### Post by maciu on 2009-02-02
i have launchers is my dock for gnome-terminal, i need it as root :) and as mentioned above other apps *run fine* (for example xterm, terminator)

---

### Post by jfernyhough on 2009-02-02
So there's the problem: gnome-terminal for some reason wants to talk to GConf but the other applications don't.

I don't know why. :D

Therefore for now I'd use Terminator. ;)

---

### Post by ajgreeny on 2009-02-02
I don't know if this will help, as I think you want it to open without a password being entered, but ```
gksudo gnome-terminal
``` certainly opens a root terminal, though in your user folder, and you do need to enter the password.

---

### Post by jfernyhough on 2009-02-02
Actually I get the same problem on mine:

```
$ gksudo gnome-terminal
Failed to contact the GConf daemon; exiting.
```

I have a load of PPAs enabled, though...

---

### Post by marmuta on 2009-02-02
Doesn't work here either. How about```
gnome-terminal -e "sudo -i"
```

---

### Post by maciu on 2009-02-02
thats a temporary solution but it would be nice to have gksu work with gnome-terminal again, i have been using it since Hoary :)

---

