---
title: "LXDE (lxdm) how to add users that can be visible in the login screen?"
date: 2012-03-08
forum: Installation &amp; Upgrades
---

### Post by phibuntu on 2012-03-08
Hi all

I have newly installed "ubuntu server" together with "lxde" on my laptop.

I added some users using the "useradd" command in the shell, which works fine (I can switch to their profile using "su <username>" in the bash).

In the login-screen however they do not appear. More: When I enter those user names and passwords, the system seams not to know those users. It only accepts me (as installer of the system or as administrator, or or ???).

Any Ideas how to add a user in lxde to the graphical login manager?

thanks in advance

---

### Post by papibe on 2012-03-08
I would recommend using 'adduser' instead of 'useradd'.

'adduser' does the complete job of creating an user.

Regards.

---

### Post by phibuntu on 2012-03-09
Thanks for your prompt reply, but this was probably only one mistake of several.

I removed the old users (those which I generatet wich "userad") using "userdel". After that I generated them newly with "adduser". 

There are still only the following "users" in the graphical login dialog:

* syslog
* <my - own - admin - username>
* usbmux daemon

Any other Ideas?

---

### Post by phibuntu on 2012-03-09
I have just tried the menu item "Preferences -> users and groups" It generates the users also, but remains the same problem in the login screen.

---

### Post by sudodus on 2012-03-09
Maybe they will appear after rebooting the computer.

---

### Post by phibuntu on 2012-03-09
Nope, I restarted several Times. But thanks for the hint.

Does anyone know the exact boot process of ubuntu-sever edidion together with lxde?

---

### Post by sudodus on 2012-03-09
I don't know any graphical interface to add and edit users for lxde. But for xfce there is one, so maybe you can install xfce.

```
sudo apt-get install xubuntu-desktop
```

It is ```
users-admin
``` which actually belongs to gnome and will be installed with
```
sudo apt-get install gnome-system-tools
``` so it should work if you 'only' install that one. I think that, as long as you don't run gnome, it will not slow down your computer, it only occupies space on the HDD.

And finally, I have recently installed a desktop system with xfce, added lxde and added a user. That user showed up at login after using ***users-admin*** to create it.

---

### Post by phibuntu on 2012-03-09
Thanks, but I already have users-admin installed.
If I ad the users using "adduser" or with the tool "user-admin" does not make a difference in the login screen.

It is NOT a problem of adding users. This works fine. They get a home directory, a password which I tested using "su" and "whoami". Everything great. 

The only problem is, that the login screen shows not that what I want. I want to show up the users in the login screen, which are also presentet with "user-admin". But at the moment only myself (admin) and two absolutely nonsense users "syslog" and some "deamon" are in the list.

Other Ideas?

---

### Post by sudodus on 2012-03-10
I see. This behaviour is different from the desktop flavours.

- Maybe some little program or setting (file or entry in file) is missing, and I have no more ideas, what to do.

- Or maybe a security issue, that regular users are not supposed to log in to the server via the console.

[COLOR="Red"]Let us hope that someone running Ubuntu Server with LXDE will read this and suggest what to do.[/COLOR]

---

### Post by phibuntu on 2012-03-10
Yes.

And probably the tiltel of this thread schould read something like this>

Ubuntu Server edition. LXDE-Login-Screen shows **wired** users.

I will sort out the login procedure of the server edidion. The displayed user-list MUST be stored somewhere....

---

### Post by phibuntu on 2012-03-11
I have found the two following bug reporting pages, which braught me further, but not to the end:

[https://bugs.launchpad.net/ubuntu/+source/lxdm/+bug/881669]("https://bugs.launchpad.net/ubuntu/+source/lxdm/+bug/881669")
and
[https://bugs.launchpad.net/ubuntu/+source/lubuntu-artwork/+bug/666590]("https://bugs.launchpad.net/ubuntu/+source/lubuntu-artwork/+bug/666590")

So I added "usbmux ntp and syslog" to the blacklist in /etc/lxdm/default.conf.

This brings the desired users to the list, but login is still only possible whith myself (admin, root). The other logins accept no password at all (empty, "1234567890", ...). What do I have to do/add, that other users can also login to my computer (my wife, children, ...?)

Any Ideas?

---

### Post by phibuntu on 2012-03-11
SOLVED

Taken last step.

After the blacklisting of "usbmux" and "syslog". The last problem was my own, because the user directries of the other users hat the wrong owner (I copied them from an old linux version as super user).

Now, everything works as expected.

Thanks everyone.

---

### Post by sudodus on 2012-03-12
> **phibuntu said:**
> SOLVED

Taken last step.

After the blacklisting of "usbmux" and "syslog". The last problem was my own, because the user directries of the other users hat the wrong owner (I copied them from an old linux version as super user).

Now, everything works as expected.

Thanks everyone.
Well, I could not help much, I think you solved the problem yourself.

Congratulations :KS

Finally, please mark this thread SOLVED

---

### Post by phibuntu on 2012-03-12
How can I mark it as solved?

---

### Post by sudodus on 2012-03-12
> **phibuntu said:**
> How can I mark it as solved?
Click on _**[COLOR=Red]Thread Tools[/COLOR]**_ at the top of the page and select 'Mark this thread as SOLVED'

---

### Post by phibuntu on 2012-03-12
I will do.

And thanks again for your help. Even if you didn't solve it directly, your tips gave me many hints on the wohle problem solving process.

---

