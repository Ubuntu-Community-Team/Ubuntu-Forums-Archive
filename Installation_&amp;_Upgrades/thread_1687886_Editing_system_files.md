---
title: "Editing system files"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by TimmyK. on 2011-02-14
Hello. I am trying to change some of my system files, for instance, Celestia textures, icons, and screensavers. However, I do not have permission to edit any system files, despite the fact that I am the system administrator. Isn't any Linux OS supposed to be all open-source and editable? How can I get around this? Thanks in advance.

---

### Post by col48 on 2011-02-14
Timmy

You are two people (users) on the machine and only one has the admin permissions.  This is not Windows!

When you login normally you do not have the permissions to change system files - this is a protection not just from typing mishaps but also from malevalent programs which might masquerade as you after you are logged in [not that I have heard of any for Linux].

The second user (known as root) who has the admin permissions is normally invoked one command at a time in command-line style in the Terminal application by prefixing the command with sudo or one of its variants.  You are then prompted for the password (same as your own) to validate the request before the command is executed.

EG to list files in the current folder you might do
```
dir -al

```
and to do the same thing as root you would do
```
sudo dir -al

```

Hope that helps.

---

### Post by presence1960 on 2011-02-14
Open a terminal and run ```
gksu nautilus
``` or ```
gksu <whatever your file browser is>
```

Now navigate to those file(s) and make changes. be careful as you will have root permissions.

---

### Post by kn0w-b1nary on 2011-02-15
I would just like to add that DO NOT create any files in your /home/ directory that you want to edit later as yourself as they will be owned by root. of course this can be fixed by typing in terminal:

```
sudo chown your_username filename
```

Hope this helps!

---

### Post by TimmyK. on 2011-02-15
OK, thanks, now I can edit my system files. However, now, all my folders such as Documents, Downloads, Music and Pictures are invisible. What I am trying to do at the moment is add some textures in the downloads folder to the Celestia textures folder. However, downloads is invisible, so how can I do this?

---

### Post by kn0w-b1nary on 2011-02-15
I don't know the proper way, but you can probably use a USB as the middle man.

---

### Post by TimmyK. on 2011-02-15
You mean a USB external device (flash drive or hard drive)?

---

### Post by kn0w-b1nary on 2011-02-15
> **TimmyK. said:**
> You mean a USB external device (flash drive or hard drive)?

Correct.

---

### Post by TimmyK. on 2011-02-15
Got it. Once again, the geniuses on the Ubuntu forum save the day! Thank you.

---

### Post by kn0w-b1nary on 2011-02-16
You're welcome! :D

---

