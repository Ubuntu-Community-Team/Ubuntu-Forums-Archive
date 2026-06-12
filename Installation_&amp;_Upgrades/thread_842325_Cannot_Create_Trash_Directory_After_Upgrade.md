---
title: "Cannot Create Trash Directory After Upgrade"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by spimby on 2008-06-27
Hello,  

After upgrading from 7.10 to 8.04, I was unable to drag anything into the trash as I didn't have permission to create the "Trash" directory.  After looking around here on the forums, I found that the trash had moved to /home/username/.local/share/Trash

When I first tried to examine that directory, I didn't have permissions to go into .local.  I used a terminal and sudo to create the Trash directory.  Still unable to do anything.  It appears that Root was the sole owner of .local and all it's sub directories.

I have since changed the owner of /.local and /.local/share to myself (from root). I have also changed the permissions on both of those to 777.

The trash now works, but the icon doesn't update immediately when I put something in. I have to open and close the trash to see the full trash icon (?).

[COLOR="Green"]My question: Is that the permission set up on the normal, functioning installation? [/COLOR] The other directories in ~/.local/share are still owned by root and have **drwxr-xr-x **permissions (applicaions, desktop-directories, and now tracker).

Thanks!

---

### Post by Pumalite on 2008-06-27
This might help:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[http://ubuntuforums.org/showthread.php?t=589909](http://ubuntuforums.org/showthread.php?t=589909)

---

### Post by adam_kimber on 2008-06-27
> **spimby said:**
>  It appears that Root was the sole owner of .local and all it's sub directories.

I have since changed the owner of /.local and /.local/share to myself (from root). I have also changed the permissions on both of those to 777.

You could try changing the group too. I Will check this evening what group my trash folder belongs to. Also 777 is not that secure even its only trash :P

---

### Post by spimby on 2008-06-30
Ok, I modified the directory permissions of 

~/.local
~/.local/share
~/.local/share/Trash

All to  drwxrwx---  and with me as the owner and group.  It works fine now. :)

---

