---
title: "Gnome-terminal new tab/ new terminal"
date: 2009-08-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by taavikko on 2009-08-14
Anyone else noticed that when first opening a new gnome-terminal,
And selecting via menu -> new tab or new terminal

It opens in /

Seems like a little bug on setting the $PWD

---

### Post by phenest on 2009-08-14
Not getting this but I am using a custom .bashrc if that's anything to do with it. I don't have the old one to test.

---

### Post by taavikko on 2009-08-14
LOL
```
lakka:~$ gedit .bashrc
-bash: gedit: command not found
taavikko@lakka:~$ sudo aptitude -f install

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for taavikko: 


```

Then I realized that, that was on my remote shell...
enough OFFTOPIC,

running pretty stock .bashrc, only aliases enabled and GPGKEY added
that shouldn't affect on anything.

But this issue happens when the terminal is started for the first time after login.
Can't reproduce after that...

---

### Post by nperry on 2009-08-14
> **taavikko said:**
> Anyone else noticed that when first opening a new gnome-terminal,
And selecting via menu -> new tab or new terminal

It opens in /

Seems like a little bug on setting the $PWD

Standard .bashrc, but not having this problem.

---

### Post by taavikko on 2009-08-22
Just did a clean install of alpha4,
 Even formatted $HOME

This problem still persist.
After logging in, opening terminal -> open new tab -> result:
$PWD is / instead of $HOME or same as previous tab.

Only tweak to .bashrc is enabling .bash_aliases

---

### Post by VMC on 2009-08-22
What does "id" reveal. Wondering if somehow your linked to root.

---

### Post by terry_gardener on 2009-08-22
when i do this it opens the new tab or terminal at home not /

---

### Post by taavikko on 2009-08-22
> **VMC said:**
> What does "id" reveal. Wondering if somehow your linked to root.

Nothing special in here:
```
tta@dv5:~$ id
uid=1000(tta) gid=1000(tta) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),115(admin),120(sambashare),1000(tta)
```

But maybe I would be better off reporting this in LP in case somebody is affected.

---

### Post by taavikko on 2009-08-24
Somehow this was solved by upgrade of bash to version 4.
and then copying the /etc/skel/.bashrc to ~/

Thanks anyway to all participants.

---

