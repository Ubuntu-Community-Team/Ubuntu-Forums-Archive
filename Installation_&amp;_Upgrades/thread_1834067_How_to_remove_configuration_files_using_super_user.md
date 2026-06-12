---
title: "How to remove configuration files using super user privileges"
date: 2011-08-27
forum: Installation &amp; Upgrades
---

### Post by varunaub on 2011-08-27
when issued the command > dpkg -l | grep '^rc' | awk '{print $2}' | xargs dpkg --purgethe terminal messages that > dpkg: error: requested operation requires superuser privilegeWhen sudo is included > sudo dpkg -l | grep '^rc' | awk '{print $2}' | xargs dpkg --purge  the same message is given > dpkg: error: requested operation requires superuser privilege 1 Who is the superuser in Ubuntu isn't it the root?:confused:

2 How to remove Configuration files?:confused:

---

### Post by Mark Phelps on 2011-08-27
Instead of using sudo the way you are, you could login as root by entering "sudo -i" -- but bet AWARE, that you can then cause MAJOR damage to your install, especially if you removal becomes overly aggressive and damages system components.  Rememer, as ROOT, you can do ANYTHING -- even trash your install.

---

### Post by snowpine on 2011-08-27
sudo does not extend past the | or "pipe" symbol. So you need to use sudo for each part of your command. 

As mentioned above "sudo -i" will give you a root shell.

---

### Post by varunaub on 2011-08-28
What is a "root shell"?

---

### Post by snowpine on 2011-08-28
> **varunaub said:**
> What is a "root shell"?

"sudo -i" makes it so every command you type after that is "sudo" or root

When you are done you can type "exit" and you'll go back to regular user privileges.

If the thought of this makes you uncomfortable then don't use it.

> Special notes on sudo and shells

None of the methods below are suggested or supported by the designers of Ubuntu.

Please do not suggest this to others unless you personally are available 24/7 to support the user if they have issues as a result of running a shell as Root.

To start a root shell (i.e. a command window where you can run Root commands), starting Root's environment and login scripts, use:

sudo -i     (similar to sudo su - , gives you roots environment configuration)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Mark Phelps on 2011-08-28
You should notice the warnings that snowpine included ...

As I said earlier, using the root shell can cause MAJOR DAMAGE to your install.  So, if all you're trying to do is remove a few small config files -- you would really be better off leaving it alone.

---

### Post by ezio5285 on 2013-03-01
I got an error on terminal too..

ezio@ASUS-PC:~$ cd Desktop
ezio@ASUS-PC:~/Desktop$ dpkg -i '/root/Desktop/minidwep-gtk-30419-ubuntu-32bit.deb'
dpkg: error: requested operation requires superuser privilege

---

