---
title: "Failed update-grub - /usr is broken!?"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by fredp on 2009-10-10
update-grub hangs saying that my /usr is broken:
```
$ sudo update-grub
Your /usr is broken, please fix it before call this wrapper!

```
What does this mean?
An effect is that new kernels are not added anymore to grub menu.

Some more testing based on what I found on the net about that message:
```
fredp@notebuc:~$ which update-grub
/sbin/update-grub
fredp@notebuc:~$ file /usr/sbin/update-grub
/usr/sbin/update-grub: ERROR: cannot open `/usr/sbin/update-grub' (No such file or directory)

```
I read that the script is looking for update-grub in /usr/sbin, but I don't have that. Is it provided by a specific package?

I'm running a "virgin" Karmic beta (i.e. I installed it from scratch from the iso - updates are only from beta onwards). Things went ok until last kernel update (2.6.31-13) - honestly I don't remember if it was a partial upgrade.

---

### Post by philinux on 2009-10-10
Read the sticky re partial updates. It could have removed something vital. 

You could check via synaptic to see what went on under File>History.

---

### Post by french on 2009-10-10
this morning the same problem to solved this problem paste/copy in the terminal
```
sudo apt-get install grub2
``` and ```
sudo update-grub
```Reboot your system and it,s just working fine :)

---

### Post by fredp on 2009-10-10
> **philinux said:**
> Read the sticky re partial updates. It could have removed something vital. 

You could check via synaptic to see what went on under File>History.

Is there an option to see also what has been done by update-manager? In synaptic I can only see what I manually installed/removed.

Installing grub2 results in removing grub and startup-manager, is this safe?

---

### Post by ranch hand on 2009-10-10
Did you click on "file" in the upper right corner of synaptic?  That is where history is located.

The contents of my /usr/sbin/update-grub;
```

#!/bin/sh -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"

```
It is allowed to be executed.

Slap that bugger in and see what happens.

You should not have grub or startup-manager installed if you are really running on grub2 so I can't see removing them to get grub2 installed right would be a problem.

There, now you have all the information you need to have a complete set of new problems.  This one is getting old, you need a new one.

---

### Post by philinux on 2009-10-10
> **fredp said:**
> Is there an option to see also what has been done by update-manager? In synaptic I can only see what I manually installed/removed.



```
sudo cat /var/log/apt/term.log
```

---

