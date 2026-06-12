---
title: "lost &quot;default system session&quot; and &quot;Gnome&quot;...."
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by tajreed on 2006-08-04
and can only get a good desktop with Gnome failsafe. I even reinstalled Dapper and the same problem occurs. "default system session" and "gnome" provide unuseable desktops. Also "default system session" "not installed on this machine". How do I recover these?

Thanks

---

### Post by tseliot on 2006-08-05
Try adding a new account (i.e. username):

1) Boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).


2) Type:
```
addusr new_username
```

**NOTE: replace "new_username" with your new username (which must be different from the one you already have**

```
passwd new_username_password
```

**NOTE: replace "new_username_password" with the password for your new username**

3) Add your new username to the sudoers list (otherwise you won't be ablet o use sudo)

Type:
```
visudo
```

and look for these lines:
```
# User privilege specification
root    ALL=(ALL) ALL[CODE]

Add your new username so as to make it look like this:

[CODE]# User privilege specification
root    ALL=(ALL) ALL
**new_username ALL=(ALL) ALL**
```

**NOTE: replace "new_username" with your new username**

After you did that type: 
```
:wq
```

and press ENTER in order to save


4) Restart your computer. Type:
```
reboot
```

5) Boot Ubuntu as usual and log in using your new username

---

### Post by tajreed on 2006-08-05
I was able to enable new name and password per your instructions but still had config problems when rebooting. However, your insight gave the clue as to how solve the problem. I reinstalled using a new screen name and password and all is well. I did not reformat my /home so I was able to save all my files. Everything is in great shape after, of course, the 160 updates. 

Thanks for your efforts. Fortunate for us that are new to Linux that you are available on the forums. 

Now I may try Automatixbleeder again with XGL/compiz after I get back from a few days in the north country.

Thanks again

---

