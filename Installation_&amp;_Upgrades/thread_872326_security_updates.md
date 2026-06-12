---
title: "security updates ?"
date: 2008-07-27
forum: Installation &amp; Upgrades
---

### Post by jnvta on 2008-07-27
[FONT="Courier New"][/FONT]newbie here: how do i get security updates ? I have a fresh install of 7.10, and that bubble is there saying 365 updates available...but clicking that caused problems on the last 2 installs, 7.10 is working fine right now, so i only want  important updates, don't care for any software updates at this time. thanks

---

### Post by iaculallad on 2008-07-27
> **jnvta said:**
> [FONT="Courier New"][/FONT]newbie here: how do i get security updates ? I have a fresh install of 7.10, and that bubble is there saying 365 updates available...but clicking that caused problems on the last 2 installs, 7.10 is working fine right now, so i only want  important updates, don't care for any software updates at this time. thanks

Navigate to Applications->Accessories->Terminal to open your gnome-terminal and input the following command below to do the manual update:

```
sudo apt-get install && sudo apt-get update
```

EDIT: This operation will ask your password. Just enter your user password even if you don't see it being echoed. That's just normal.

---

### Post by vpsville on 2008-07-28
From the command line:

sudo apt-get update
sudo apt-get dist-upgrade

That will update everything to the latest version, even the kernel.

---

### Post by zvacet on 2008-07-28
> so i only want important updates, don't care for any software updates at this time. thanks

If that is what you want then 

```
gksudo gedit /etc/apt/sources.list
```

and put # sign in front of every line exept security lines.Save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

---

