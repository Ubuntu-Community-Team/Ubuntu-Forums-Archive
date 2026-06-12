---
title: "Unable to apt-get update"
date: 2012-06-29
forum: Installation &amp; Upgrades
---

### Post by Ertai87 on 2012-06-29
I haven't run system updates in a couple days, and I just now decided to see if there was anything.  However, I appear to be unable to run apt-get update.  Here's the error I'm getting:

```
[UN]@[CN]:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
```

I've gotten this error before, but usually I've just run it again and it worked.  I've now run it a few times, and I can't seem to get it to work.  What should I do?  Thanks.

---

### Post by drmrgd on 2012-06-29
Try running this to clear out the apt lock:

```
sudo rm /var/lib/apt/lists/lock
```

That should get you going again.

Oh, I should also point out that one cause of this error (not that I'm saying this is definitely the problem here) is if you're trying to use something like the Software Center and running an apt command in the terminal at the same time.  Be sure you're not trying to manage your packages with two different tools at the same time.

---

### Post by Ertai87 on 2012-06-29
It ended up resolving itself.  Thanks.

---

