---
title: "My System is Up To Date???"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by rossjman1 on 2008-03-11
I have Ubuntu Dapper, and trying to update to Edgy. I am not going to use apt-get, because it seems that every time I try to upgrade manually apt-get breaks and wont let me install or uninstall anything. Anyway I typed this in the command line:
```

gksu "update-manager -c -d"

```
If I'm not mistaken, this should look for new updates. The "-c" option looks for distribution upgrades, which is what I want. However, update-manages says I have an up-to-date system. WTF???

---

### Post by Oldsoldier2003 on 2008-03-11
> **rossjman1 said:**
> I have Ubuntu Dapper, and trying to update to Edgy. I am not going to use apt-get, because it seems that every time I try to upgrade manually apt-get breaks and wont let me install or uninstall anything. Anyway I typed this in the command line:
```

gksu "update-manager -c -d"

```
If I'm not mistaken, this should look for new updates. The "-c" option looks for distribution upgrades, which is what I want. However, update-manages says I have an up-to-date system. WTF???
Try:
```
gksu update-manager --dist-upgrade
```

in the man page and -d is for dev release...

---

### Post by rossjman1 on 2008-03-11
```

jeff@ubuntu:~$ gksu update-manager --dist-upgrade
gksu: unrecognized option `--dist-upgrade'
GKsu version 1.3.7

Usage: gksu [-u <user>] [-k] [-l] <command>

  --always-ask-password, -a
    Do not try to check if a password is really
    needed for running the command, or if there
    are other means of obtaining it: simply ask for it.
  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.
  --disable-grab, -g
    Disable the "locking" of the keyboard, mouse,
    and focus done by the program when asking for
    password.
  --icon <icon>, -i <icon>
    Replace the default window icon with the argument.
  --message <message>, -m <message>
    Replace the standard message shown to ask for
    password for the argument passed to the option.
  --print-pass, -p
    Ask gksu to print the password to stdout, just
    like ssh-askpass. Useful to use in scripts with
    programs that accept receiving the password on
    stdin.
  --prompt, -P
    Ask the user if they want to have their keyboard
    and mouse grabbed before doing so.
  --ssh-fwd, -s
    Strip the host part of the $DISPLAY variable, so that
    GKSu will work on SSH X11 Forwarding.
  --sudo-mode, -S
    Make GKSu use sudo instead of su, as if it had been
    run as "gksudo".
  --title <title>, -t <title>
    Replace the default title with the argument.
  --user <user>, -u <user>
    Call <command> as the specified user.
  --desktop <file>, -D <file>
    Use a .desktop file to get the name of the application
    and the icon from.

  --preserve-env, -k
    Preserve the current environments, does not set $HOME
    nor $PATH, for example.
  --login, -l
    Make this a login shell. Beware this may cause
    problems with the Xauthority magic. Run xhost
    to allow the target user to open windows on your
    display!


jeff@ubuntu:~$ gksu "update-manager --dist-upgrade"
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
usage: update-manager [options]

update-manager: error: no such option: --dist-upgrade


```

---

### Post by Pumalite on 2008-03-11
You might also want to try this:

gksu sed -i 's/dapper/edgy/' /etc/apt/sources.list 

gksu apt-get update 

gksu apt-get dist-upgrade

---

### Post by rossjman1 on 2008-03-11
I would like to stay away from apt-get for now. This is my third time trying to upgrade, and the first two times I used apt-get and apt-get stopped working.

---

### Post by tekguy on 2008-03-11
Sorry I can't read...

---

### Post by Pumalite on 2008-03-11
> **Pumalite said:**
> You might also want to try this:

gksu sed -i 's/dapper/edgy/' /etc/apt/sources.list 

gksu apt-get update 

gksu apt-get dist-upgrade

Hi:

My command makes that your sources.list gets changed to Edgy first, so apt-get has no choice, but to upgrade.

---

