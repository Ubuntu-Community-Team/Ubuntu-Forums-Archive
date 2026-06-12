---
title: "Getting files from old password protected accounts"
date: 2005-05-23
forum: Installation &amp; Upgrades
---

### Post by cinematography on 2005-05-23
Installation was a success! I'm now using Ubuntu. One last problem remains... I can't access the files in my Mandrake accounts. The folders are locked to me. Does anyone know how I can enter those accounts, or where I can enter a password so I can access those accounts? 

NOTE: I am somewhat of a newbie.

---

### Post by JonahRowley on 2005-05-23
You're going to have to mount the filesystem these files are on.  After that, if the file permissions don't allow world to read them, you might have to copy them to your Ubuntu permission with sudo.

Or do you mean the filesystem is mounted, and the files are encrypted?  If so, this is going to be a little harder..

---

### Post by cinematography on 2005-05-23
[QUOTE=JonahRowley]You're going to have to mount the filesystem these files are on.  After that, if the file permissions don't allow world to read them, you might have to copy them to your Ubuntu permission with sudo.

Or do you mean the filesystem is mounted, and the files are encrypted?  If so, this is going to be a little harder..[/QUOTE]
I can see the folders. There actually in my Home directory. I just can't access them because they belong to my old OS, Mandrake.

---

### Post by Pitbull11188 on 2005-05-24
I'm not sure the exact command but a quick chown -775 computer name:user /file path should allow you to access the file. You will have to repeatthis process for each file. Hope it helps.

---

