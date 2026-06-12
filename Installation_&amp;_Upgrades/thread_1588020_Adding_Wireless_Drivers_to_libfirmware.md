---
title: "Adding Wireless Drivers to lib/firmware"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by Vinster11569 on 2010-10-04
I have ubuntu and a Texet USB Wireless adaptor. I have a CD with Linux Drivers and I am supposed to be able to copy the folder into lib\firmware. Although I am an administrator and have added myself to the group root, I still can't do it, as it says I don't have permissions. I am thinking of trying to use CHMOD once i've read the manual, but wonderd if there's an easier way? The software source and Synaptic Package manager can't help me. Is it as simple as using CHMOD, or is there an easier/harder way?

---

### Post by snowpine on 2010-10-04
Welcome to the forums!

You need to use the 'sudo' command (and also note Linux uses forward slashes, not backslashes):

```
sudo cp /path/to/the/file.name /lib/firmware/
```

If you prefer a GUI file manager:

```
gksudo nautilus
```

More info on sudo:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Vinster11569 on 2010-10-04
cheers-a-plenty - I know about the slashes, just an old windows habit. I will try it when I get home tonight.

---

