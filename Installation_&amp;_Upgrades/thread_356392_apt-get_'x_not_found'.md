---
title: "apt-get 'x not found'"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by digm on 2007-02-08
Greetings! 

I'm having issues with apt.  Certain packages are not found even though I know they should exist...

> joe@server:~$ sudo apt-get install rcconf
> Reading package lists... Done
> Building dependency tree... Done
> E: Couldn't find package rcconf

So far I haven't been able to install rcconf or wput, but I'm sure there are more...

Any idea how I can correct this?

If it matters, it's a 6.06 server install off the alternate cd...

Thanks!

---

### Post by taurus on 2007-02-08
Have you enabled both universe & multiverse in /etc/apt/sources.list?  Try removing the # in front of all the lines with deb.

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
sudo nano -w /etc/apt/sources.list
```
Save the changes and run

```
sudo apt-get update
```
Now, see if you can install that package again.

---

### Post by digm on 2007-02-08
That did it.  Thanks so much!

---

