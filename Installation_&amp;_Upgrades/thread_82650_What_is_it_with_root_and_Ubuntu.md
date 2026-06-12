---
title: "What is it with root and Ubuntu?"
date: 2005-10-26
forum: Installation &amp; Upgrades
---

### Post by YenningComity on 2005-10-26
I do not understand what ubuntu's deal with root is. It is so frustrating not having a root account while working on the system itself. Not only that but it still locks you out of areas while using the gui. To top things off in order to shutdown you must use your password which while it might make sense for say old time mainframes with terminals but I thought Ubuntu was for HUMANS?

Sorry blowing off some steam I guess I just switched back and well the power you have over gentoo is nice even if it is a bit too time consuming.

---

### Post by Psquared on 2005-10-26
have you tried sudo su?

---

### Post by dbott67 on 2005-10-26
You can enable a root password by typing:
```
sudo passwd root
```
and remove the root password by typing:
```
sudo passwd -l root
```
-Dave

---

### Post by aysiu on 2005-10-26
First of all, read this:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

You may not *agree* with the reasons for using sudo, but there *are* reasons. Also, once you get used to sudo, there's nothing stopping you from using the GUI for things. In Gnome, there's ```
gksudo nautilus
``` and in KDE, there's ```
kdesu konqueror
``` And I don't know where you're getting this needing a password to shut down. Are you using XFCE or something? Are you not using a GUI at all (are you shutting down from the terminal?)?

---

