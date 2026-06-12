---
title: "Problem with nvidia drivers..."
date: 2008-10-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mmcmonster on 2008-10-28
A fresh install of Intrepid worked fine. I upgraded to the nvidia drivers (the one that was recommended by System->Administration->Hardware Drivers).

On reboot, I just get a horizontal line a few pixels high at the top of the screen.

What now?

I can drop to the CLI with ctrl-alt-<F1>, but don't know which package to uninstall.

Hopefully this will be fixed by Friday?

---

### Post by dabl on 2008-10-28
> **mmcmonster said:**
> 

I can drop to the CLI with ctrl-alt-<F1>, but don't know which package to uninstall.




Assuming the default Intrepid repositories are enabled, in the CLI do this:

```
sudo /etc/init.d/kdm stop
```

```
sudo apt-get update
```

```
sudo apt-get install envyng-core
```

and following installation,
```

sudo envyng -t
```

then choose #1 "Install Nvidia Driver", followed by #5 "Restart X Server".

:)

---

### Post by taavikko on 2008-10-28
> **dabl said:**
> Assuming the default Intrepid repositories are enabled, in the CLI do this:

```
sudo /etc/init.d/kdm stop
```

:)

```
sudo /etc/init.d/gdm stop
```
If running gnome

---

### Post by mmcmonster on 2008-10-28
Will give it a try tonight.  Thanks.

---

### Post by Manasia on 2008-10-28
If you are using Nvidia legacy drivers, as of today your X server is going to be broken for a while. 

I have not found anything that resolves the issue with Nvidia legacy drivers and X server 1.5, I am running a Geforce3.

---

### Post by yoasif on 2008-10-28
dabl, i tried your solution even before I came upon this thread, and it doesn't work. 

I think the problem is with the nvidia drivers. It may be time to file a bug report soon...

---

