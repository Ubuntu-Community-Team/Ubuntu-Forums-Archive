---
title: "Proftpd problem"
date: 2008-08-08
forum: Installation &amp; Upgrades
---

### Post by heyman12 on 2008-08-08
I threw some things in my a few subforums in my home directory, now I want to delete them, I drag them to the trash, and with a few folders, I get this message, and they wont delete:

[IMG]http://i178.photobucket.com/albums/w276/tenshi_admin_shipo/error-2.png[/IMG]

---

### Post by iaculallad on 2008-08-08
Try the command below on your terminal:

```
gksudo nautilus
```

When your nautilus window open, browse that folder - right-click on it and delete/move to trash.

---

### Post by heyman12 on 2008-08-08
I dont have that instlled.

let me see if that works once it done

---

### Post by iaculallad on 2008-08-08
> **heyman12 said:**
> I dont have that instlled.

Had you tried **sudo rm**? That will give you the privilege to delete a file/folder.

*You don't have nautilus installed? You just posted a graphical error message.

---

### Post by heyman12 on 2008-08-08
I'm using SSH from my vista computer.

---

### Post by heyman12 on 2008-08-08
> **iaculallad said:**
> Had you tried **sudo rm**? That will give you the privilege to delete a file/folder.

*You don't have nautilus installed? You just posted a graphical error message.

sudo rm wont delete directories, and although it says its not empty, there are no files in these directories visible, and as I said before, I'm using SSH and FTP.

---

### Post by iaculallad on 2008-08-08
> **heyman12 said:**
> I'm using SSH from my vista computer.

I see. Once logged on your Ubuntu server via SSH, you could issue the command:

```
rm /directory/filename.ext
```

or

```
rm -rf /directory/directory-to-be-deleted
```

EDIT: Try the -rf switch with your **sudo rm**.

---

### Post by heyman12 on 2008-08-08
thanks, that worked.

---

