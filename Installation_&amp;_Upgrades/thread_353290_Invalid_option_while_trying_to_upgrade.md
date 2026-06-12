---
title: "Invalid option while trying to upgrade"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by txtinman on 2007-02-04
I have version 6.06 and would like to upgrade to 6.10. When I issue the command "gksu update-manager -c" I get an error telling me that "c" is an invalid option. I just recently installed 6.06 and today updated the system. I'm thinking something is wrong with update-manager. Any help here?

Mike

---

### Post by Paerez on 2007-02-04
run it like this:
```
gksudo "update-manager -c"
```
when you run it as "gksudo update-manager -c" the "-c" option is for gksudo. When you run it like the above way in the box, the -c option is for update-manager, which is what you want.

So when I type it in on my computer, it looks like this:
```
nick@nite:~$ gksudo "update-manager -c"
```

Those darn ""s are confusing!

---

### Post by txtinman on 2007-02-04
> **Paerez said:**
> run it like this:
```
gksudo "update-manager -c"
```
when you run it as "gksudo update-manager -c" the "-c" option is for gksudo. When you run it like the above way in the box, the -c option is for update-manager, which is what you want.

So when I type it in on my computer, it looks like this:
```
nick@nite:~$ gksudo "update-manager -c"
```

Those darn ""s are confusing!

Yeah, I tried that. I get the same error.

---

### Post by Paerez on 2007-02-04
can you post exactly what the terminal says with the command you ran and everything?

---

### Post by txtinman on 2007-02-04
This is exatly what happens:

```

```mike@oz:~$ gksudo update-manager -c
gksudo: invalid option -- c
GKsu version 1.3.7

Usage: gksudo [-u <user>] [-k] [-l] <command>

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

---

### Post by Paerez on 2007-02-04
you are typing it wrong, look at the second box in my first post. You need to put quotes in.

---

### Post by txtinman on 2007-02-04
> **Paerez said:**
> you are typing it wrong, look at the second box in my first post. You need to put quotes in.

You were right Paerez, I just didn't think the quotes were part of the command. I'm not used to seeing that. Thanks for the help.

---

### Post by Paerez on 2007-02-04
Yeah it's very confusing since people usually put quotes on a command, which you normally remove, but in this case the quotes are supposed to be there.

Good luck with edgy.

---

