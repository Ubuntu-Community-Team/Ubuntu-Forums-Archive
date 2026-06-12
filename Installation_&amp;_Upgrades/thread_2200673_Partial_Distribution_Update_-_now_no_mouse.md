---
title: "Partial Distribution Update - now no mouse"
date: 2014-01-20
forum: Installation &amp; Upgrades
---

### Post by b3XJPzC on 2014-01-20
I completed a partial distribution update today.  At first after restart go a low graphic only due to error.  I would need to fix myself.  I tried using the "use low level graphics once" and got a black screen.  Finally I was able to get into Ubuntu but do not have a mouse.  The mouse is functional but invisible.  

Any ideas how I can fix this.

Am using the latest version of Ubuntu and have had no real problems for a year.

---

### Post by Bashing-om on 2014-01-20
b3XJPzC; Hi ! Welcome to the forum .

Try this and advise results:
Boot to a terminal and run terminal codes:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
"update" syncs the system database with the mirror database;
"upgrade" updates all installed packages to current available versions;
"dist-upgrade" uses apt-get's "smart"mode to resolve problems, and install any held packages.

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
For proper submission of outputs.

[INDENT][INDENT]a tale will be told
[/INDENT][/INDENT]

---

### Post by ibjsb4 on 2014-01-20
About partial updates

[http://ubuntuforums.org/showthread.php?t=1859240](http://ubuntuforums.org/showthread.php?t=1859240)

---

### Post by b3XJPzC on 2014-01-21
Thanks for the help.

Have restored it to the previous settings and working well.

This weekend I will try you suggestions and let you know how it worked.

---

### Post by Bashing-om on 2014-01-21
b3XJPzC; Roger that !

Standing by, Let us know how it goes.
What works and the final outcome.

[INDENT][INDENT]we be stepp'n
[/INDENT][/INDENT]

---

### Post by b3XJPzC on 2014-01-21
I tried the terminal codes you suggested.  After it was all done, it looked great except for no mouse again.  The mouse worked but was invisible.  So I used timeshift again to restore the system.  Works great now.

Maybe I should just not update anything for a few weeks?

Any other suggestions?

And thanks both of you for your help.

---

### Post by Bashing-om on 2014-01-21
b3XJPzC; Yuk,

I can not imagine what updates would break the mouse interaction.
What mouse/type are you using ?
Take a look at the log file "/var/log/Xorg.0.log" and maybe older ones and see if there are any hints.

[INDENT][INDENT]for every cause
[INDENT][INDENT][INDENT]there is a reaction
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by b3XJPzC on 2014-01-24
Hello Bashing-om

could not find any logs called Xorg.0.log.  Maybe I was looking in the wrong place.  I look in /var/log/

Maybe what I need to do is to just update one file at a time until I find the bad one.

Remember the mouse still works.  But you can not see it.  It is as if the theme just made it invisible.

---

