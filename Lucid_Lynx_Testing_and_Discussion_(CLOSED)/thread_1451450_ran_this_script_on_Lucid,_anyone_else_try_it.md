---
title: "ran this script on Lucid, anyone else try it?"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2010-04-10
[http://www.webupd8.org/2010/04/ubuntu-1004-first-time-use-script-02.html](http://www.webupd8.org/2010/04/ubuntu-1004-first-time-use-script-02.html)

I tried it and it did fix the slow update manager problem where it downloads package information. It used to hang a very long time, now update manager zips.

---

### Post by RTrev on 2010-04-10
Can anyone explain how it works, and what potential side-effects it might have?

---

### Post by KegHead on 2010-04-10
Hi!

It cut the time by 90%.

KegHead

---

### Post by cariboo on 2010-04-10
I just tried the script, and only selected the fix chrome repository option, that solved the slow repository update problem.

Thanks

---

### Post by Anduu on 2010-04-10
I was having the same speed issues with Synaptic,Update-Manageer,Apt...etc so I downloaded the script and dug into it...

Here are the relevant bits I found:

This one stops Update-Notifier from autostarting.I just killed the process and tried Update manager again....no difference.
```
elif [ "$choicee" = "Fix the Update Manager" ]
                     then
                     sudo -u $ON_USER "DBUS_SESSION_BUS_ADDRESS="$DBUS_SESSION_BUS_ADDRESS gconftool -s --type bool /apps/update-notifier/auto_launch false

```

This next one made the difference for me.I am using the Google Chrome repository so I gave the command a shot and lo and behold no more delay :)

```
elif [ "$choicee" = "Fix 'apt-get update' delay for Google Chrome repository" ]
                     then
                     echo "Acquire::http::Pipeline-Depth "0";" | sudo tee -a /etc/apt/apt.conf.d/90localsettings
```

Anyway I am not sure exactly what it does but it woks.Maybe someone familiar with apt can elaborate?

As for the rest of the script it just enables some useful repositories and applies some desktop tweaks.

---

### Post by RTrev on 2010-04-10
Yes, it works great.  It was this line:

```

echo "Acquire::http::Pipeline-Depth "0";" | sudo tee -a /etc/apt/apt.conf.d/90localsettings

```

that I have no idea what it does.  Just running it manually did the trick, however, and as far as I can tell it hasn't broken anything else. :)

---

