---
title: "Please Help Me"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by uthturn on 2008-05-23
I'm having a problem that I can't seem to find a solution to. It started when i could not update. I can get to the point where I click install updates then nothing happens I have to xkill it. Well I can install updates if I go to a term and type sudo apt-get upgrade . But now I've also noticed that I can not open synaptic or the software sources under system/admin . When I click on either I get the circle mouse likes its going to open then nothing, I've tried running synaptic thru a term. It still does not start and gives no errors.

---

### Post by pytheas22 on 2008-05-23
Are you sure it doesn't say anything at all when you try to run Synaptic from the terminal?  If you get any output, please post it all here.  There are some known issues with segmentation faulting and Synaptic that may be related to your problem.

Also, for the future, you would probably get faster, more effective help if your thread titles contained information describing you problem instead of "Please Help Me."

---

### Post by uthturn on 2008-05-23
yeah i run gksu /usr/sbin/synaptic in terminal
it doesn't say anything i get the circle for the mouse but then nothing.

yeah i realized it was a bad thread title after posting :)

---

### Post by bwhite82 on 2008-05-23
> **uthturn said:**
> yeah i run gksu /usr/sbin/synaptic in terminal
it doesn't say anything i get the circle for the mouse but then nothing.

yeah i realized it was a bad thread title after posting :)

Try it with verbose output:

> gksu /usr/bin/synaptic -vvv

---

### Post by uthturn on 2008-05-28
tj@tj-desktop:~$ gksu /usr/bin/synaptic -vvv 
gksu: invalid option -- v
GKsu version 2.0.0

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

  --sudo-mode, -S
    Make GKSu use sudo instead of su, as if it had been
    run as "gksudo".
  --su-mode, -w
    Make GKSu use su, instead of using libgksu's
    default.

---

### Post by pytheas22 on 2008-05-29
> Try it with verbose output:

I don't think Synaptic has verbose output mode; its man page doesn't list any.

Try running these commands and please post the output:

```
sudo -s
synaptic
software-properties-gtk
```

My guess is that if apt-get seems to be working from the command line (as you say above), your problem lies with the GUI, which I think is based on python in the case of both Synaptic and the sources.list utility (although I could be wrong about that).  Hopefully this output will tell us why the GUIs won't start.

By the way, do you have any trouble running other graphical applications, particularly ones that use python-gtk?  Deluge is an example of such an application; you might want to try installing it (sudo apt-get install deluge-torrent) and see if it will start.

Also, just on the off-chance that the problem lies here, what is the output of:

```
cat /etc/apt/sources.list
```

---

