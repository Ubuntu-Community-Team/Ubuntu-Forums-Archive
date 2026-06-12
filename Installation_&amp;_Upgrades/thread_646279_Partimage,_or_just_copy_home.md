---
title: "Partimage, or just copy /home?"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by ryantmer on 2007-12-21
I'm trying to figure out the best way to transfer my install from a 7 year old computer to a two year old one (needless to say, they have very different hardware). For Windows, I'd just Ghost it, and do a repair install, which would usually work. But I hate Windows, so I won't be doing that.

Anywho, is partimage worth using, or should I just copy my /home directory to an external drive, install Xubuntu on the other system, and then use a LiveCD to copy my /home on the external drive to the new install? I don't really mind losing programs and such, it's mainly just files and settings that I would like to keep.

Thanks in advance :)

---

### Post by jpkotta on 2007-12-21
That should work.  I've done it before, and never had an issue.  Remember to use the -a option to cp.
```
sudo cp -a $HOME /external
```

Also, make sure that your user has access to the files after they're copied.  The numeric userid might be different on the new system.
```
sudo chown -R username:username /home/username
```

---

### Post by ryantmer on 2007-12-22
Excellent, thanks :)

One other question, though:

When I copy my old /home to the new installation, and then reinstall all the programs I have, will reinstalling the programs on the new installation overwrite the settings files I have copied? Or should I do the new install, install all the programs I need, and _then_ copy my /home?

Thanks again

---

### Post by jpkotta on 2007-12-23
You should copy /home first.  Most programs will write the config files in ~ only if they don't exist already.  If one does overwrite something (unlikely), you will still have the backup.

---

### Post by ryantmer on 2007-12-24
Thanks for the help :)

The process didn't go overly smoothly, mostly due to myself overlooking several factors. But finally, it worked!

Thanks again.

---

