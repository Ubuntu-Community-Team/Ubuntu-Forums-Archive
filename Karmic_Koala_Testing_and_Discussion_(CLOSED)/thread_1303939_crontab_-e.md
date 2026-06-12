---
title: "crontab -e"
date: 2009-10-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Primefalcon on 2009-10-28
I seem to have a problem with crontab....

when I issue the command ```
crontab -e
``` it opens up the cron file in nano, I have tried both export and setting EDITOR=vim in my .bashrc file and neither is actually making any difference

---

### Post by Barriehie on 2009-10-28
> **Primefalcon said:**
> I seem to have a problem with crontab....

when I issue the command ```
crontab -e
``` it opens up the cron file in nano, I have tried both export and setting EDITOR=vim in my .bashrc file and neither is actually making any difference

Try 
```

export EDITOR=<whatever>

```
Barrie

---

### Post by Primefalcon on 2009-10-28
> **Barriehie said:**
> Try 
```

export EDITOR=<whatever>

```
Barrie
that works for the terminal session, but still the basic .bashrc EDITOR  variable is not being recognised like it used to in jaunty, in this a bug or is it a change?

---

### Post by bribera on 2009-10-28
I have:
```
export EDITOR=emacs
```

In my .bashrc and it works just fine... maybe you shouldn't use vim. :twisted:

Joking, joking!

---

### Post by slakkie on 2009-10-28
> **Primefalcon said:**
> that works for the terminal session, but still the basic .bashrc EDITOR  variable is not being recognised like it used to in jaunty, in this a bug or is it a change?

you should export it in your .bashrc

---

### Post by utnubuuser on 2009-10-28
isn't it the .profile file?

---

### Post by slakkie on 2009-10-29
> **utnubuuser said:**
> isn't it the .profile file?
Also possible.

---

