---
title: "problems with sudo.help!"
date: 2005-06-12
forum: Installation &amp; Upgrades
---

### Post by pronvit on 2005-06-12
installed latest ubuntu today. after this i can't run any program that requres sudo.

eg. trying to run synaptic and it says (after pressing enter in password prompt) 'child process exited with error code 1'.

---

### Post by nemin on 2005-06-12
[QUOTE=pronvit]installed latest ubuntu today. after this i can't run any program that requres sudo.[/QUOTE]
What do you mean with "latest ubuntu"? Breezy?

---

### Post by pronvit on 2005-06-12
no:) i mean 5.04

i fixed problem by enabling root account from another linux system (editing config files). sudo still doesn't work however i can su to root and do what i need

but it's very strange that such problem appears after installation of stable release

---

### Post by mingus on 2005-06-12
have you made the necessary entry in /etc/sudoers?

---

### Post by pronvit on 2005-06-12
what entry?

---

### Post by mingus on 2005-06-12
Do:

#visudo

This is a secured wrapper on nano to edit the /etc/sudoers file.  This the file which controls sudo permissions for users, using the familiar user and/or group structure.  You will see an entry for root.  You should see another line for the user you created, to the right of the = sign it should show which permssions you have.  Or there is an entry for a group (which your user should belong to) and its permissions.  

There is a HowTo on this, and help in the Starter Guide as well.

---

### Post by Xian on 2005-06-12
```
# User privilege specification
root	         ALL=(ALL) ALL
username     ALL=(ALL) ALL
```

---

### Post by pronvit on 2005-06-12
before I manually enabled root (from another linux system) I was unable to run visudo (permission denied)
now I see my gorup (adm) there but sudo doesn't work.

now I'm going to reinstall ubuntu one more time and will see if this problem will repeat

---

### Post by mingus on 2005-06-12
Try using the syntax that Xian provides above.  Be sure in the installation to set up root and the root password.  (Note:  I once had a problem similar to yours when I said yes to using the "shadow password" feature, but I really don't know if that caused the problem.)

If you need to, you can log in to a shell with root (rather than into gnome) and change the sudoers file there.  You can also change the gdm control file to permit you to log in to gnome as root.

---

### Post by pronvit on 2005-06-12
I modified sudoers as Xian proposed... but nothing changed. if trying from console sudo just returns w/o any message and any action

---

### Post by desdinova on 2005-06-12
[QUOTE=pronvit]I modified sudoers as Xian proposed... but nothing changed. if trying from console sudo just returns w/o any message and any action[/QUOTE]
 try 

strace sudo

to see if it offers any more clues?

---

### Post by Xian on 2005-06-12
Are you able to go into the User and Groups module and check to see if your username is set to get Administrative Priviledges?

---

