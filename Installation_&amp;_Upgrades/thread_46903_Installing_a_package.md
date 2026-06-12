---
title: "Installing a package"
date: 2005-07-06
forum: Installation &amp; Upgrades
---

### Post by Djeepy46234 on 2005-07-06
Hi

I just finished my installation of ubuntu but when I try to install a package with sumo 

```
sudo apt-get install kde
```

But when I enter the root password (the same I wrote during the installation) it's not working at all and now I can't do nothing because when I try to install one, i receive a "No Permission" message...

Is there a way to reset root password or something ?

Thanks

---

### Post by varunus on 2005-07-06
With sudo you're supposed to enter your own password.  I'm not sure if that's the problem, since with Ubuntu there shouldn't be a root password, just your own...

Can you post the exact output of the below command?  Also your /etc/sudoers file?

---

### Post by Djeepy46234 on 2005-07-06
I don't have access to the file because I'm not root...

When I try to do this :

```
sudo -u root *****
```

The terminal ask me for a password but I don't have this password so I try something randomly and it's not working and when after the 2 try I try again, i obtain :

```
djeepy46234 is not in the sudoers file. This incident will be reported.
```

So I can't do nothing, and Totem too is not working, i obtain this :

```
Resource busy or not available.
```

---

### Post by varunus on 2005-07-06
You did type your own password after the sudo prompt right?  (Sorry, its not clear from your post, since you said you typed something random...)

One way to do this would be to boot into recovery mode and add yourself to the /etc/sudoers file.  In recovery mode, you're automatically root.

Good luck.

---

### Post by Djeepy46234 on 2005-07-06
And how I go in recovery mode ?

And what am I suppose to do there ?

---

### Post by varunus on 2005-07-06
Recovery mode should be an option from the GRUB menu that you first see when you boot.  (If you don't see a menu, you should at least see an option to open a menu by hitting a key.)

Once in recovery mode, open up your sudoers file by typing:
```
nano /etc/sudoers
``` 

Make it look like this:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL
```

Good luck.  Post back here if that doesn't work.  This is really a strange error...

---

### Post by Djeepy46234 on 2005-07-06
I have the same but I don't have this part :

```
# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL
```

---

### Post by Djeepy46234 on 2005-07-07
Now, when I try to open something that require a login (Package Manager), I have a long long long loading and finaly, the program close, no login window ...

:(

---

### Post by varunus on 2005-07-07
What is the output of typing "gksudo synaptic" into a terminal window in GNOME?  What is the output of typing "sudo synaptic" into a terminal window?

This really is a strange error...

---

### Post by Djeepy46234 on 2005-07-07
[QUOTE=varunus]What is the output of typing "gksudo synaptic" into a terminal window in GNOME?  What is the output of typing "sudo synaptic" into a terminal window?

This really is a strange error...[/QUOTE]

Now it's working for this but for the root access, i set up :

djeepy46234 ALL=(ALL) ALL

Because but now I have root access....

---

