---
title: "How do I set Eterm as default terminal?"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by Daergeth on 2006-10-29
Like the title suggests Im trying to get eterm to be default, I already have it all downloaded. Thanks :)

Nevermind I just figured it out ](*,)

---

### Post by Bachstelze on 2006-10-29
What do you mean "default" ?

---

### Post by LxP on 2006-11-11
I believe the original poster wanted to adjust the program associated with x-terminal-emulator (i.e. what GNOME runs when 'Run in terminal' is ticked).

For anyone else who might be interested in this, it can be done by visiting **System** > **Preferences** > **Preferred Applications** > **System** and entering the details of another terminal emulator (or selecting one from the menu).

There is also a way to do this via the command line itself:

```
sudo update-alternatives --config x-terminal-emulator
```

Here's an example of what will be displayed:

```
alex@callisto:~$ sudo update-alternatives --config x-terminal-emulator
Password:

There are 5 alternatives which provide `x-terminal-emulator'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/xterm
          2    /usr/bin/uxterm
          3    /usr/bin/koi8rxterm
          4    /usr/bin/lxterm
*+        5    /usr/bin/gnome-terminal.wrapper

Press enter to keep the default[*], or type selection number: 1
Using `/usr/bin/xterm' to provide `x-terminal-emulator'.
alex@callisto:~$
```

**Edit:** Daergeth, when you work out a solution to your own problem please don't hesitate to post that solution.  Others may come across your thread when they have the exact same problem (as I did) and an actual solution is always more useful. :-D

---

