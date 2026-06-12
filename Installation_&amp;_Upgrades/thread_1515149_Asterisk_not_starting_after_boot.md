---
title: "Asterisk not starting after boot"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by luc_roy99 on 2010-06-21
[COLOR=black][FONT=Verdana]Ok I just installed the latest copy of Asterisk and Freepbx on Ubuntu 10.4 and I am trying to make it auto start on boot. I have attempted everything I could think of or find on line and nothing seems to work. I am not sure if this is caused by the new versions or I am just missing something.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Anyone encountered this yet?[/FONT][/COLOR]

---

### Post by Rubi1200 on 2010-06-22
Not sure if this will work, but it might be worth trying:

Go to System > Preferences > Startup Applications > Add

a dialog box will come up and there you add the name of the program and the command, which means e.g. /usr/bin/asterix or whatever the correct path to your program happens to be. Then click Add and you should be good to go.

Hope this helps.

---

### Post by luc_roy99 on 2010-06-22
that did not work.

the command I need ran when the system boots is 'amportal restart"

---

### Post by Rubi1200 on 2010-06-22
Did you try amportal restart in the command field?

Then just give it a name and Add.

---

### Post by luc_roy99 on 2010-06-22
that is what I put it but it did not work.

---

### Post by Rubi1200 on 2010-06-23
Hmm; I am sorry to hear it has not worked for you.

Unfortunately, I don't have any other suggestions.

Hopefully, someone else here on the forums will have an idea for you.

Good luck!

:-)

---

### Post by SATA on 2011-09-18
The above suggestion will not work, as amportal needs to be run as root.

Here is how I do it.
Switch to root privileges:
```

sudo -s

```then run the following commands
```

cd /etc/init.d
ln -s /usr/local/bin/amportal /etc/init.d/amportal
update-rc.d amportal defaults

```If this doesnt work, I suggest doing the following
```

sudo gedit /etc/rc.local

```In that file, put in 
```

amportal start

```Put that just above the exit 0 line.

---

