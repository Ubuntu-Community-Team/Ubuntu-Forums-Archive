---
title: "How To Change All File/Directory Permissions in Users Home Directory? [Resolved]"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by brisamrus on 2007-04-03
I've just installed Edgy over Dapper. User directories are all on a different Home partition. All the permissions for each user directory now seem to be a mess and are not accessible to users when they log in (if they can log in).

Here's my question? How can I change the permission for all files and directories in a given users home folder all at once so everything is assigned to that user? I've tried using nautilus but it won't seem to change all file AND directory permission. I've also tried Konqueror and Midnight Commander. I don't really know how to use either very well. Is there a way to get the job done?

---

### Post by NeoLithium on 2007-04-03
Well, the way I change it, is to do

sudo chown -hR username /directory

That changes the directory and all subdirectories/files to the username you input.

---

### Post by brisamrus on 2007-04-03
Sorry. I posted this in the wrong forum. Heading over to edgy.

---

### Post by brisamrus on 2007-04-03
And thanks for the help.

---

### Post by aysiu on 2007-04-03
Edgy has a forum?

No, this forum is fine, and you also got your answer. Stay here.

---

### Post by NeoLithium on 2007-04-03
No problemo :)

---

### Post by brisamrus on 2007-04-03
That's exacly what I needed. Thanks very much.

---

