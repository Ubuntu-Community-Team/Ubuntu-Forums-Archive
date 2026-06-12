---
title: "Where can PATH be set other than /etc/environment?"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by justanotherhandle on 2009-12-24
The path that is set in /etc/environment looks like this:

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```

But my path when I echo $PATH looks like this:

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/real/RealPlayer"
```

Where is the RealPlayer set? I've looked in my .bashrc and there is nothing that references RealPlayer and I don't have a .bash_profile.

Thanks.

---

### Post by SuperSonic4 on 2009-12-24
I suspect Realplayer installed it. You could remove the directory if the files aren't important (simply move it if they are) and then try again

---

### Post by justanotherhandle on 2009-12-24
Thanks. But where (when?) is the path being set? I only run RealPlayer at very specific instances and it's not running now ... at least it's not in the list of running processes. So how would (when) RealPlayer set a new path variable?

Thanks.

---

### Post by SuperSonic4 on 2009-12-24
I would guess that it did so during install. I've never installed realplayer so I can't be sure

---

### Post by justanotherhandle on 2009-12-24
Per the ubuntugeek.com entry on directory structures ([http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html](http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html))  ...

> /etc/profile.d contains scripts that are run by /etc/profile upon login. 

And in the /etc/profile.d/ directory there is the scripts that sets the RealAudio path.  

Whee!

---

