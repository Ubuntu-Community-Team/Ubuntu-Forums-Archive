---
title: "copying files thrue ssh with preserved rights and ownership"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by Azyx on 2007-09-25
Hi. I want to copy my e-mail and firefox from one coputers /home to another, with preserved rights and ownership. How do I do it true ssh? I want to know both how i do with GUI-ssh but also how I do in the text-based ssh?

cp -P i think is right, but I don't now how I tell to copy to another machine.

In GUI-ssh I don't know how I tell ssh to copy with preserved right and owner-ship.

I'm the user on booth the machine.

---

### Post by Jussi Kukkonen on 2007-09-25
```
scp -p files remote_username@remote_machine:/path/to/copy/to
```

the files will be owned by remote_username as far as I know -- you can't really preserve ownership in this case... 

If you really want to preserve ownership you could tar everything up, scp the tar-file over and then untar it into place. That might work *but only if the actual user ids match*, not just usernames. Don't try this with system files if you don't know what you're doing...

---

### Post by Azyx on 2007-09-25
I have doing it before with tar, but i thougt it could be faster to copy directly. I tried it for .mozilla, but  scp say it was not a regular file.

---

### Post by Jussi Kukkonen on 2007-09-25
See *"man scp"* for help on scp -- the switch you're looking for is "-r" (for recursive copy).

---

### Post by jimcooncat on 2007-09-25
> **Jussi Kukkonen said:**
> If you really want to preserve ownership you could tar everything up, scp the tar-file over and then untar it into place. That might work *but only if the actual user ids match*, not just usernames. Don't try this with system files if you don't know what you're doing...

Same idea only faster.
-------
from [http://www.mcnabbs.org/andrew/linux/shellhacks/]("http://www.mcnabbs.org/andrew/linux/shellhacks/")

(cd /orig/dir; tar cf - .) | (cd /targ/dir; tar xpf -)
    Copying with a cp -R will mangle stuff sometimes. If you want to completely copy a tree, this command is the best way to do it. Additional tar options, like --same-owner, will let you keep things even more intact. Another way to do this is: "tar cfC - /orig/dir . |tar xpfC - /targ/dir". They should both do exactly the same thing, though the original example is perhaps a little easier to remember.

tar cf - . |ssh remotehost "cd /targ/dir; tar xf -"
    This is logically exactly the same as the tar pipe above, except that this time ssh allows our pipe to cross system boundaries.

---

### Post by Azyx on 2007-09-25
> **Jussi Kukkonen said:**
> See *"man scp"* for help on scp -- the switch you're looking for is "-r" (for recursive copy).

Thanx. It worked fine.

---

