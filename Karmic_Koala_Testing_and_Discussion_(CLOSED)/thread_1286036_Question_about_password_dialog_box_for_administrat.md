---
title: "Question about password dialog box for administrator functions"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ROFLcannon on 2009-10-08
I am testing the karmic beta 1 and I download some updates a few days ago. After I downloaded the updates I noticed when ever I open synaptic package manager, updates, and the other applications that require an administrator password the root password that you created was used to get into the applications. Instead of the regular user password being able to be used for those applications but now with the latest updates the user password is being used still to access those applications. Is there a way to change it to where the root password is used to access those applications.

---

### Post by Tibuda on 2009-10-08
Ubuntu don't have a root password. There's only the user password. What are you talking about?

---

### Post by ROFLcannon on 2009-10-08
After you are logged into your computer with the user password. Where you right click on the fast user switch applet. Then you click on edit users and groups then you click the unlock button at the bottom on the user settings box. Then the root account that was grayed out will become visible then you click on root and then click properties. Then under the account tab under the password section where it says set password by hand. After you put a password in and click ok. Then you will have a root password. So then when you open up a terminal window and then type in su you would then type in the password that you created.

---

### Post by jeremyswalker on 2009-10-08
I am at work, so I am not on my linux box at the moment. However, you can enable the root account by setting a password for it. Open a terminal window, and enter:
```
sudo su
passwd
```
This will prompt you to enter a password and re-enter the same password.
Then, enter:
```
visudo
```
Once inside this editor, I believe there is an entry that will accomplish your task. It is probably commented out. If you do not find it, I will look when I get home. I know I did this on my son's netbook, so I do have your answer.

---

### Post by anders_c_ on 2009-10-08
are you saying you have one password for user login, and another to get superuser priveliges? I have seen lots of people asking for that, but never seen a solution, thanks!:)

---

### Post by jeremyswalker on 2009-10-08
I know that my 7 year old son was dying to be able to add users to his netbook. Although I knew he could screw things up by deleting an account or changing the root password, I stumbled across the setting to prompt for the root password instead of the user password for admin privileges. So, I just enabled that setting and the root account.

---

### Post by ROFLcannon on 2009-10-08
@jeremyswalker: I have no idea which one it could be. I found user privilege specifications and members of the admin group may gain root privileges. But after I uncommented the members of the admin group may gain root privileges but then synaptic did not load at all and the update manager loaded without prompting for a password.

@anders_c_: yes you have the user password, then the root password that you create that allows you to login in from the gdm screen as root.

---

### Post by jeremyswalker on 2009-10-08
Actually, I found the setting in the sudoers man page. The key is to add "Defaults   rootpw" to the sudoers file (which is accomplished using visudo). This causes sudo, gksu, etc to prompt for the root password instead of the user password. So, the sudoers file should look something like this:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Defaults override
Defaults	rootpw

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

Let me know how you make out.

---

