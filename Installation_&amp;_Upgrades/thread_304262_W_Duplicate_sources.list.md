---
title: "W: Duplicate sources.list"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by helmeteye on 2006-11-21
What does this mean?  what is the solution?

A newer version of flash was down loaded and not installed.

---

### Post by dbott67 on 2006-11-21
It generally means that you have a duplicate entry in your Synaptic Repositories (aka sources.list file).

Can you post the output of your sources.list file?

```
cat /etc/apt/sources.list
```

---

### Post by aysiu on 2006-11-21
> **helmeteye said:**
> What does this mean?  what is the solution?

A newer version of flash was down loaded and not installed.
It means you have two of the same online source in your repositories list.

If you have no idea what I just said, read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

To solve the problem, paste this command in the terminal: ```
sudo nano -B /etc/apt/sources.list
``` delete (Control-K) the duplicate line(s) and then save (Control-X, Y, Enter) and finally ```
sudo aptitude update
```

---

