---
title: "Problem with lock from dpkg , how to solve it ?"
date: 2019-02-08
forum: Installation &amp; Upgrades
---

### Post by maks88 on 2019-02-08
First of all i want to say that i tried everything that should be help with mine issue . 
Removing the locks according to answers on the internet : 

rm /var/lib/dpkg/lock

rm /var/cache/apt/archives/lock

After removing i tired to run -> sudo dpkg --configure -a

Then i tried to run :

apt-get install software-center

apt upgrade

And i got always the same error .. 

E: Could not get lock /var/lib/dpkg/lock-frontend - open (11: Resource temporarily unavailable)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?

Can i delete the lock-frontend ? 
Can you explain to me , what exactly i solve with the deletion process ?

---

### Post by CatKiller on 2019-02-08
> **maks88 said:**
> Can i delete the lock-frontend ? 

If nothing else - for example, your desktop environment's update manager - is using it.

>  Can you explain to me , what exactly i solve with the deletion process ?

[https://en.wikipedia.org/wiki/File_locking](https://en.wikipedia.org/wiki/File_locking)

There are processes where it would be bad for two things to be modifying the same files at the same time. To stop that happening, when one thing accesses those files it sets a lock. When it's finished, it releases the lock. Then the next thing is free to set the lock and modify the files, and then release the lock. And so on.

Should one of those processes crash, you can be left with the lock in place even when there is nothing actually accessing the files, since the process was never able to release the lock. Under those circumstances, and those circumstances only, it is appropriate to manually remove the lock. Then the next process will be able to set its own lock and things can proceed as normal.

---

### Post by dmnur on 2019-02-08
To check who holds the lock:
```
sudo lsof /var/lib/dpkg/lock-frontend
```

There will be the **PID** column, and for e.g. PID 1234 you could get additional info (like the full command line) with:
```
ps -f 1234
```

---

### Post by Frogs Hair on 2019-02-08
Try the following with all package managers closed.

```
sudo fuser -vki /var/lib/dpkg/lock; sudo dpkg --configure -a
``` ```
sudo apt update
```

---

