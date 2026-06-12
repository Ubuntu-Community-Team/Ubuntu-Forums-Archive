---
title: "Problem in upgrading from Etch to Feisty beta"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by abhitux on 2007-04-15
When I  type out the following command in the terminal
[U]gksu &#8220;update-manager -c -d&#8221; 
[/U]
**this is the output I get on the screen:**
gksu: invalid option -- c
GKsu version 1.9.3

Usage: gksu [-u <user>] [options] <command>

  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.

  --user <user>, -u <user>
    Call <command> as the specified user.

  --disable-grab, -g
    Disable the "locking" of the keyboard, mouse,
    and focus done by the program when asking for
    password.
  --prompt, -P
    Ask the user if they want to have their keyboard
    and mouse grabbed before doing so.
  --preserve-env, -k
    Preserve the current environments, does not set $HOME
    nor $PATH, for example.
  --login, -l
    Make this a login shell. Beware this may cause
    problems with the Xauthority magic. Run xhost
    to allow the target user to open windows on your
    display!

  --description <description|file>, -D <description|file>
    Provide a descriptive name for the command to
    be used in the default message, making it nicer.
    You can also provide the absolute path for a
    .desktop file. The Name key for will be used in
    this case.
  --message <message>, -m <message>
    Replace the standard message shown to ask for
    password for the argument passed to the option.
    Only use this if --description does not suffice.

  --print-pass, -p
    Ask gksu to print the password to stdout, just
    like ssh-askpass. Useful to use in scripts with
    programs that accept receiving the password on
    stdin.

Manually starting up the Update manager does not indicate the availability of Feisty beta at all. What needs to be done here so that I could upgrade? :(

---

### Post by Jussi Kukkonen on 2007-04-15
Use ordinary double-quotes:
```
gksudo "update-manager -c -d"
```

---

### Post by abhitux on 2007-04-15
It works! Thanks a ton.

---

### Post by ccooksey on 2007-04-19
abhitux,

Could you enlighten me as to your whole process of upgrading etch to Feisty?  Or point me in the right direction.

Thanks,

Cory

---

### Post by abhitux on 2007-04-19
> **ccooksey said:**
> abhitux,

Could you enlighten me as to your whole process of upgrading etch to Feisty?  Or point me in the right direction.

Thanks,

Cory

This link should help you with enough screenshots
[http://onlyubuntu.blogspot.com/2007/03/upgrade-ubuntu-610-edgy-eft-to-ubuntu.html](http://onlyubuntu.blogspot.com/2007/03/upgrade-ubuntu-610-edgy-eft-to-ubuntu.html)

I hope this helps. Upgrading is painless and in case you face any problems, the forums are always there! Cheers and welcome to freedom!:guitar:

---

### Post by truck87bp on 2007-04-19
Problem:Software index is broken

Don't know what to do....can't install any updates

---

### Post by Qew on 2007-04-19
Maybe it'd be better to change the title to "Edgy", because "Etch" is the latest Debian install. :)

---

