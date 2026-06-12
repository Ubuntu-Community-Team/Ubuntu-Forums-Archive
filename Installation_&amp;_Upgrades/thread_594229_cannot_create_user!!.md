---
title: "cannot create user!!"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by ixlam on 2007-10-27
I have installed Ubuntu Studio and fedora7 .
I am sharing the  /home partition between the 2 OSs.

when I log into Ubuntu I get this message when I enter user and password
>cannot access .gnome2 permission denied,error cannot create per-user config file

I understand that I need to change permissions of these folders/files from within Fedora but what do I set them to??

any help is muchly appreciated.thanks.

---

### Post by taurus on 2007-10-27
The problem could be that on Ubuntu, your user ID is 1000 while your user ID could be something like 500 on Fedora 7 even though you use the same username for both distros.  That's why it is complaining about wrong permissions or ownership of $HOME.

---

### Post by ixlam on 2007-10-27
You are %100 correct ... but the question is ... how do I fix this ?
re-create a user in fedora with UID 1000 ?
chmod or chwn those files ?

---

### Post by taurus on 2007-10-27
You can change the UID of your username for F7 to 1000.  Do you know what partition is / for F7 since you need to edit /etc/passwd (for F7 NOT Ubuntu)?

1.  Modify /etc/passwd of F7 and change whatever value for your username to 1000.

2.  Change ownership of /home/<user> to 1000.

---

### Post by ixlam on 2007-10-27
great thanx...
I just installed so i simply erased and recreated the user with those uids and it works fine.

---

