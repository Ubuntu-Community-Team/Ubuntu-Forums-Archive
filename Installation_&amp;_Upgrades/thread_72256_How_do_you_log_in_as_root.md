---
title: "How do you log in as root?"
date: 2005-10-05
forum: Installation &amp; Upgrades
---

### Post by XtremeGamer99 on 2005-10-05
I've already checked the box at System > Admin > Login Screen Setup to allow root login, but it always says that the password/username is invaild. I need to get into root to do something with my regular user.

---

### Post by DJ_Max on 2005-10-05
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by XtremeGamer99 on 2005-10-05
That didn't help at all.

Okay, a little more detail: I mounted a Windows partition using this:

sudo mount /dev/hda1 /media/Windows/ -t ntfs

Now, when I try to access it, it says that I do not have permission to Read that directory. I looked in the Properties of it, and the owner is root, and I cannot change any of the permissions.

I know there is a way to log in as root, because I have done it before on my other Ubuntu on my other hrard disk before I had to swipe it and start clean.

---

### Post by darkmatter on 2005-10-05
XtremeGamer99, to log in as root, just do the following.

1> Set root password

In a terminal, ener the following
```
sudo passwd root
```

you will be prompted for your USER password, enter it.

Next, you will be prompted to create a root password and then once again to confirm the password. Do so.

2>Enable root login.

Go to System -> Administration -> Login Screen Setup

You will be prompted for your password (user password for sudo)

Under the Security tab in the Setup GUI, check 'Allow root to login with GDM'

After you have done this, log out of your account and log in as root with tthe username 'root' (obviously) and the password you had created for the root account.

That's all that is needed to login as root.

---

### Post by XtremeGamer99 on 2005-10-05
>_> Apparently, the only step I was missing was setting it - I had thought that when you first install Ubuntu, it takes the password you entered for your user and applies it to root. Anyways, thanks! =)

---

### Post by Dolphin on 2005-10-05
Better way would have been to log in as su and change the permissions on the HD

---

### Post by lvaleriav on 2005-10-07
hello, i tried using System/Administration/login screen setup, but it just stays in the "working" icon and after 20-30 seconds it returns to de desktop and does nothing. When I installed ubuntu I think I created the root account and password (in a terminal I can login as root). One other thing, from a terminal (login in as root or user) every time i use sudo i get a message:

unable to lookup ubuntu via gethostname()
Enter new UNIX password: postdrop: warning: unable to lookup public/pickup: no such file or directory

this happened after the "sudo passwd root" command.
Any help will be appreciated
Thanks

---

### Post by aysiu on 2005-10-07
[QUOTE=XtremeGamer99]That didn't help at all.[/quote] Actually, it did, because your original question was how to log in as root.

> 
Okay, a little more detail: I mounted a Windows partition using this:

sudo mount /dev/hda1 /media/Windows/ -t ntfs

Now, when I try to access it, it says that I do not have permission to Read that directory. I looked in the Properties of it, and the owner is root, and I cannot change any of the permissions. You don't need to log in as root to mount Windows partitions. Just follow the directions here: [http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

