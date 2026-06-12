---
title: "Root passwrord upon installation"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by teilhk on 2007-05-20
Hello:

I just made an unattended installation of Kubuntu, as far as it can go, and everything went well, except that I was not given the option to define my root password. I thought to log as root, I just had to hit "enter" to the password request because it is (?) empty, but it is not so. Now I am lost, what is my root password or how do I choose it?

Teilhard

---

### Post by lotheac on 2007-05-20
The root account in ubuntu is locked by default, you can use sudo when you need superuser permissions. If you absolutely -must- get the root account to work, you can do so by executing 'sudo passwd', but I would recommend just using sudo and keeping the root account locked.

---

### Post by yapel on 2007-05-20
You may wish to try the following:

System > administration > Users & Groups

Enter with YOUR (not ROOT) password. Highlight the "ROOT" account and click "Properties" button. You may now set the password (and confirmation)!

Good luck!

---

### Post by aysiu on 2007-05-20
> **yapel said:**
> You may wish to try the following:

System > administration > Users & Groups

Enter with YOUR (not ROOT) password. Highlight the "ROOT" account and click "Properties" button. You may now set the password (and confirmation)!

Good luck!
There's no need to do that, though.

1. Any regular admin task you perform will automatically prompt you for your user password to temporarily assume root privileges.

2. Any command you enter that you want root privileges for can be prefaced with the word *sudo*: ```
**sudo** apt-get update
```

3. If you have a series of commands you want to run as root but don't want to retype *sudo* four times, you can "log in as root" by typing ```
sudo -i
```

4. If you want a root-privileged file browser window within your session, you can press Alt-F2 and type ```
kdesu konqueror
``` If you find yourself using that a lot, you can create a keyboard shortcut or launcher for the command. There is even in Konqueror an "edit as root" context menu item for files.

None of the above (1-4) requires setting up a root login or root password.

**You do not need an active root login in Ubuntu or Kubuntu**.

Read more here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

