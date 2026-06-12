---
title: "Kdm upstart pains.."
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hikaricore on 2009-10-08
I used to keep kdm disabled at startup for various reasons including making driver installations easier.
Now with upstart it's a pain the the *** to say the very least..
Aside from manually renaming /usr/bin/kdm I've found no way to properly disable it from starting automatically (i'd imagine that gdm is much the same).
To make matters worse whenever I try and stop it:

sudo kdm stop

The damn thing just restarts itself.
Killing X and kdm has the exact same result.

How in the annoying new world of upstart do I properly manage what I do and don't want to start? >.>
Also don't give me gruff about my driver install methods, I know what I'm doing and I'm set in my ways.  :p

---

### Post by Claus7 on 2009-10-08
Hello,

I'm not using kubuntu in the first place.
I capture your phrase about gdm and similarities between the two.
What it comes quickly to my mind is to issue the command:
/etc/init.d/g(k)dm stop 
in .bashrc

this might help you disabling the kdm thing that annoys you so much in startup.

Regards!

---

### Post by hikaricore on 2009-10-09
> **Claus7 said:**
> Hello,

I'm not using kubuntu in the first place.
I capture your phrase about gdm and similarities between the two.
What it comes quickly to my mind is to issue the command:
/etc/init.d/g(k)dm stop 
in .bashrc

this might help you disabling the kdm thing that annoys you so much in startup.

Regards!

I appreciate the reply but since upstart **gdm/kdm is no longer controlled from the init.d scripts**.
I don't think you quite understood my issue..

Next idea? ;p

---

### Post by slakkie on 2009-10-09
```

sudo mv /etc/init/kdm.conf /etc/init/kdm.whatever

```

upstart looks in /etc/init and only reads *.conf files, so renaming such a .conf file will make sure that it is not started automaticly. 

For more information:
```

man upstart
man 5 init

```

---

### Post by hikaricore on 2009-10-09
Sweet, I'll try this out on my next reboot. ^_^
Thanks for the help.

---

### Post by Ar(_Zer{} on 2009-10-09
```

sudo bash
[COLOR="Red"]_{password}_[/COLOR]
service kdm stop

```

---

### Post by hikaricore on 2009-10-09
> **Ar(_Zer{} said:**
> ```

sudo bash
[COLOR="Red"]_{password}_[/COLOR]
service kdm stop

```

Yea not so much:

```
[root@devistate:~]$ service kdm stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service kdm stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop kdm
```

I suspect slakkie's solution will work just fine.

They really screwed the damn pooch when they threw upstart in at the last minute.

---

### Post by xebian on 2009-10-09
> **hikaricore said:**
> ..
.. I try and stop it:

sudo kdm stop

The damn thing just restarts itself.
Killing X and kdm has the exact same result.

... :p

It should be [COLOR="Red"]stop kdm[/COLOR] not kdm stop.

---

### Post by hikaricore on 2009-10-09
> **xebian said:**
> It should be [COLOR="Red"]stop kdm[/COLOR] not kdm stop.

```
[root@devistate:~)]$ stop kdm
stop: Unknown job: kdm
```

You sure about that?  I've really tried this all and all variations of the kind.
Something is just fubared with the whole upstart system and has been so since it popped in at the last second.

---

### Post by Zorael on 2009-10-10
The only way I've been able to stop and start kdm lately is by manually doing **sudo kdm** and **sudo pkill kdm**. Neither the old **sudo service kdm start**/**stop** nor the new **start**/**stop kdm** commands seem to work.

---

