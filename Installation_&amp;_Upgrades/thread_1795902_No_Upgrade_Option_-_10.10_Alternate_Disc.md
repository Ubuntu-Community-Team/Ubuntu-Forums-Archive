---
title: "No Upgrade Option - 10.10 Alternate Disc"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by miserly-martyred on 2011-07-03
I followed the official Ubuntu instructions that tell you to do this when things don't just "give a pop up prompt"

[https://help.ubuntu.com/community/MaverickUpgrades]("https://help.ubuntu.com/community/MaverickUpgrades")

It told me to do this:

```
gksu "sh /media/cdrom/cdromupgrade"
```

and said that was in case:

"If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:"

Well, I did that and it said along the lines of this:

```
" /bin/sh, etc. sh not found" ... "gksu, command not found"
```

Is there a way around this or am I just friggin' insane?

---

### Post by miserly-martyred on 2011-07-03
I also just tried unplugging every single storage medium and hard drive from in/out of my computer.

When I booted up the Alternate CD it still did not detect the system, of just Ubuntu 10.04 on there.

I have also used the Rescue Mode on the Alternate CD and the standard "single user - recovery only" mode from the GRUB boot loader.

When I used those modes, I did this:

```
[as root]:  apt-get update && apt-get dist-upgrade

```
As I tried to do those, apparently my old sys. is set to use:

```
ftp.ussg.iu.edu:http
```

That situation is denied by my system and it says:

```
No such address found on that host.
```

Is there a way that I can use one of these terminal methods to do a net. install, successfully, by changing repositories?

I don't know how to switch repositories from command line...

---

### Post by dino99 on 2011-07-03
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by miserly-martyred on 2011-07-03
> **dino99 said:**
> [https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

I appreciate the tips, but I went alone and figured some stuff out and used the nano txt editor to mess with my sources.list file.

I have adjusted the mirror and reset things to a repository that actually works.  But then I am denied the ability to save cuz my file system says that it's read only.

I have done all of this other stuff while having ALREADY logged in to the console with root :(

Isn't there something one can do with the init file permissions to change this?  I'm trying to figure out what issue is triggering the denial of any write access.

Any ideas?

---

