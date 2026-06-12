---
title: "[SOLVED] Stuck at Password in new Hardy instalation"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by niceguy123 on 2008-06-04
I've upgraded one of my computers from 7.04 to 8.04 by way of a new installation on CD. I wrote down the new username and password on a piece of paper.  

But, I must have done something wrong. Now when I turn on the computer and fill in the user name and password I get an error message that they are not correct, I have tried using upper case and lowercase for the username first letter.

Is there a way around the password or a default password I can use or must I reinstall the OS again?

---

### Post by sisco311 on 2008-06-04
Reboot your computer and select Recovery Mode from the Grub menu.
When the computer first starts up, you have a few seconds to push esc to go into GRUB.

When the command prompt appears, issue the command:

```
ls /home
```

This command will print the home folders.(home folder name = user name)

Type:

```
passwd username
```

to change your password.

```
reboot
```

to reboot the computer.

---

### Post by iaculallad on 2008-06-04
Try doing [password recovery]("http://www.linuxconfig.org/Recover_-_Reset_forgotten_linux_root_password") (root) first. With successful recovery, try to change you're user's password afterwards. If all else fails, do your fresh install.

---

### Post by niceguy123 on 2008-06-04
Thank you so much

```
passwd username
```

In the stage am I to write ```
passwd newpassword username new username
```

or ```
newpassword newusername
```

---

### Post by sisco311 on 2008-06-04
> **iaculallad said:**
> Try doing [password recovery]("http://www.linuxconfig.org/Recover_-_Reset_forgotten_linux_root_password") (root) first. With successful recovery, try to change you're user's password afterwards. If all else fails, do your fresh install.

By default, the root account is disabled in ubuntu.
You can boot in Recovery mode (single user mode) to get a root session.

---

### Post by iaculallad on 2008-06-04
> **niceguy123 said:**
> Thank you so much

```
passwd username
```

In the stage am I to write ```
passwd newpassword username new username
```

or ```
newpassword newusername
```

Just input passwd username on the root shell (replacing "username" with the username you forgot it's password.

```
passwd username
```

You will be prompted with "New UNIX Password" phrase, just enter your NEW password and reenter it for confirmation. Password changed.

```
shutdown -r now
```

to restart.

---

### Post by sisco311 on 2008-06-04
> **niceguy123 said:**
> Thank you so much

```
passwd username
```In the stage am I to write ```
passwd newpassword username new username
```or ```
newpassword newusername
```

The *ls /home* command will list the home folders.
The name of your home folder is usually your user name.
So you don't need to create a new user, just change the password
of your user. The passwd **username** will ask you to type the new
password and to retype the new password.

EDIT: In Hardy you are not dropped automatically to the root shell. 
You need to choose the "Drop to root shell prompt" option from the menu.
After you changed the password type ***exit*** and select the "Resume normal boot"
(or something similar) option from the menu.

---

