---
title: "upstart can't read from console"
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by fabelkey on 2010-04-08
I have installed the new (K)Ubuntu 10.04 Lucid.
So far everythings works fine and very fast.

Now I have a problem reading a passphrase in a custom script from the console.

The script has to be executed before I login.

So far it is no problem making other tasks wait for my script:
I have added it to the "start on" conditions:

e.g. kdm.conf:
start on (filesystem and stopped open-encrypted ....

This makes the tasks wait for my task.

The problem is, that no input can be read from the console. From the upstart documentation I thought that the "console output" stanza I used meant read and write to/from the console, but I cannot type anything. The Boot process just stops at this moment.

---

### Post by mrand on 2010-04-20
> **fabelkey said:**
> I have installed the new (K)Ubuntu 10.04 Lucid.
So far everythings works fine and very fast.

Now I have a problem reading a passphrase in a custom script from the console.

The script has to be executed before I login.

So far it is no problem making other tasks wait for my script:
I have added it to the "start on" conditions:

e.g. kdm.conf:
start on (filesystem and stopped open-encrypted ....

This makes the tasks wait for my task.

The problem is, that no input can be read from the console. From the upstart documentation I thought that the "console output" stanza I used meant read and write to/from the console, but I cannot type anything. The Boot process just stops at this moment.Random idea: I wonder if console refers to the console on <ctrl-alt-f1>

[INDENT]Marc[/INDENT]

---

### Post by clayreiche on 2010-05-08
Any answer to this? I'm trying the same thing but I see no input prompt during boot. (on any tty's)

---

### Post by clayreiche on 2010-05-09
This might help... Haven't tried it yet but it looks promising.

[http://ubuntuforums.org/showthread.php?t=1409392](http://ubuntuforums.org/showthread.php?t=1409392)

---

