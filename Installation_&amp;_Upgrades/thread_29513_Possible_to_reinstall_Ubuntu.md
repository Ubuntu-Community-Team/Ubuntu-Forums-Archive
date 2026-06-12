---
title: "Possible to reinstall Ubuntu?"
date: 2005-04-24
forum: Installation &amp; Upgrades
---

### Post by gingermark on 2005-04-24
Hello,

I have been using Ubuntu (the first Linux OS I have ever installed) for just under a month now, and feel I have gotten to grips with it quite well.

However, I probably didn't read everything I was supposed to when I started out, and quite fancy reinstalling Ubuntu, now that I "know what I am doing"...

Is there a way to reinstall it without losing the home directory? If I was to backup the home directory (including the hidden files and directories) and then just copied the relevant parts back once I had reinstalled the programs, is it likely I would run into any problems?

Thanks for any help you can give,
regards,
gingermark.

---

### Post by diebels on 2005-04-24
You could try to reinstall all packages you have installed with a command like this:
```
apt-get install --reinstall $(dpkg --get-selections | grep -v deinstall | cut -f 1)
```
If you really want to wipe out everything and keep home, use tar or file-roller, not a simple copy to back up.

---

### Post by gingermark on 2005-04-24
Thanks,

I had a look at the file roller site, and the program just seems to create compressed archives. If I may ask, why is this preferable to simply backing up the folder as it is?

Cheers.

---

### Post by alastair on 2005-04-24
This should not be a problem at all - assuming /home is on a separate partition.

If it is, on re-install in the partitioning, mount /dev/<whatever> on /home and "leave as is" (or however worded) i.e. do not "format" (make a filesystem).

---

### Post by gingermark on 2005-04-24
[QUOTE=alastair]This should not be a problem at all - assuming /home is on a separate partition.

If it is, on re-install in the partitioning, mount /dev/<whatever> on /home and "leave as is" (or however worded) i.e. do not "format" (make a filesystem).[/QUOTE]

I'm unsure whether this is the case or not. I installed 4.10 and then upgraded to 5.04 . During the original install I followed the defaults options.

The only partioning I did was to create a swap partition and a normal one.

---

### Post by nad on 2005-04-24
File-roller is a front end to tar (tape archive). It will create a compressed archive only upon request. The advantage of backing up to an archive is that your file structure and permissions remain intact. Copying files back and forth can create a permissions nightmare that will cause serious head and nerve damage. Okay, strange errors, especially in a desktop environment like gnome on ubuntu.

You also don't want to copy back gnome's configuration files. The archive will have this same problem. All the settings for your environment are stored in xml files that the gnome desktop integrates with global files into a virtual database of system and app settings. For this reason, there is a setting in this database to specify your home directory. Go to System Configuration -> Users and Groups.

What you need to do is a backup of your home directory, a reinstall, then copy back your personal data files, then import things like your bookmarks using the applications own features. An archive will have stored _all_ files in a particular location. Try copying your home directory elsewhere. You will notice that dozens of configuration files will not be included and the permissions will be all wrong (edit->) if you try to access it as your home directory. The mv command works, but there is no checkpoint this way.

---

