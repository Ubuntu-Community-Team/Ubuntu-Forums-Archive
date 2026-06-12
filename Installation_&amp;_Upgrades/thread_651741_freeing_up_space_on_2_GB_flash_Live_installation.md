---
title: "freeing up space on 2 GB flash Live installation"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by basicbill on 2007-12-27
Hi,
Ubuntu newbie here.
I have been using 7.1 on a 2GB drive that I created according to instructions on this site.

Nice distro.

Recently, I have been getting some error messages like 'no space left on device' and I can't use Evolution anymore. It won't even let me clear out the Trash folder due to 'no space left on device'.

Where are the files located in .evolution? Perhaps, I could delete them manually.

Also, I have uninstalled OpenOffice to free up more space.

Any other suggestions to free up space?

thanks in advance for all suggestions.

bb

---

### Post by jken146 on 2007-12-27
.evolution is in your home directory.  I don't see why you wouldn't be able to clear the trash (it's at ~/.trash or ~/.Trash -- I can't remember which).

---

### Post by Herman on 2007-12-28
If you have received updates and installed any added software, which is most likely, there will be copies of the packages stored in /var/cache/apt/archives.

You can easily delete all of those packages with this command,
```
sudo apt-get clean
``` If you want you can copy the 'calendar', 'addressbook', 'mail', 'memos' and 'tasks' folders out of your .evolution directory and save them somewhere on some other media for restoring when you install Ubuntu in a hard disk someday. Then you can just open Evolution and delete all your email. 

Both of those ideas should probably clear some space in your disk. 

Regards, Herman :)

---

