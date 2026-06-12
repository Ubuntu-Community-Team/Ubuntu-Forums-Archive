---
title: "getting dependency relations"
date: 2018-05-28
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2018-05-28
is there a way to get all the dependency relations of either all packages that are installed or all packages in all my source repositories?

---

### Post by TheFu on 2018-05-28
Yes there is.```

$ sudo apt-cache rdepends packagename
```

---

### Post by Skaperen on 2018-05-28
wow!  that's going to be a lot of commands to do!  this only gets the relations for one package.  i wanted them for all packages.    well, i can always do this to get them for *installed* packages:

```
dpkg -l | awk '{if($1=="ii")print "apt-cache rdepends",$2;}' | sh
```

and _sudo_ is not actually needed for these commands.

---

### Post by TheFu on 2018-05-28
I got error 13 with out sudo on my 16.04 system.
There are at least 5 other methods using other tools. Google found them easily for me.

---

### Post by Skaperen on 2018-05-29
which command(s) got the error 13?  maybe some status about the non-root user is checked by the command.  all my laptop users have access to run _sudo_ (though i didn't use it).  maybe i need to make some wimpy users  to try things on.

---

### Post by TheFu on 2018-05-30
The command in #2 above.

---

### Post by Skaperen on 2018-05-30
that command just reveals information cached from the repositories.  sure, it could tell a user if the admin has kept the cache updated or flushed it.  but i see no reason for it to need escalated privileges if it has the programmed means to decide.

---

