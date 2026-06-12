---
title: "How does one update over the network?"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by Dev'olution on 2008-10-20
Hey Guys,

I have a network of 1 laptop, 1 desktop and 1 server, and I wonder if its possible at all to update the laptop from 8.04 to 8.10 beta over the network, as my desktop is currently running the 8.10 beta.

Any help will be greatly welcomed.

Thanks,
Kris

---

### Post by pytheas22 on 2008-10-20
Just open a terminal and type:
```

sudo update-manager -d
```

and the update manager will open with an option to upgrade to Intrepid beta.

---

### Post by Dev'olution on 2008-10-20
> **pytheas22 said:**
> Just open a terminal and type:
```

sudo update-manager -d
```

and the update manager will open with an option to upgrade to Intrepid beta.

I know this much. What I want to do is use the updates from another PC on the network.

---

### Post by Partyboi2 on 2008-10-20
You could try [[COLOR=Blue]this [/COLOR]]("http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/")

---

### Post by Dev'olution on 2008-10-20
It's all good guys.

Thanks for the help, I think i'll just update to Intrepid.

Cheers,
Kris

---

### Post by sethvath on 2008-10-20
If you plan to make your server as a mirror for ubuntu updates then yes. But if your desktop is just running 8.10 and you want to update your laptop via the home network I doubt its feasible. You have to look up instructions on mirroring ubuntu update, thats how most schools/companies update all their systems at the same time. 

Why do you want to update over network when you can install from the same cd you used to install on your desktop.

---

### Post by Dev'olution on 2008-10-20
> **sethvath said:**
> Why do you want to update over network when you can install from the same cd you used to install on your desktop.

I updated to Intrepid on the desktop using the update-manager.

---

### Post by MJWitter on 2008-10-21
The way i have been doing it(as my internet usage is limited) is to copy the files from /var/cache/apt/archives on one pc(excluding the "lock" file) to the same folder on the pc to be updated. Then do the update and those files won't need to be updated.

---

