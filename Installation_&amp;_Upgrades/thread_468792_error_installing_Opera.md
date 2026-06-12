---
title: "error installing Opera"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by brim4brim on 2007-06-09
I installed it from the opera_9.21-20070510.6-shared-qt_en_i386.deb file on the opera download page.

Now I get the following error:
```

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package opera needs to be reinstalled, but I can't find an archive for it.'
```

I think the problem is because I clicked open in Opera instead of save to disk so it can't find the package now.

I get the above error when starting any of the package managers.

I've also tried using dpkg to solve the problem with the following commands and outputs:
```

brian@brian-laptop:/tmp$ sudo dpkg -r opera --force-remove-reinstreq
dpkg: error processing opera (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
dpkg - warning: ignoring request to remove --force-remove-reinstreq which isn't installed.
Errors were encountered while processing:
 opera

brian@brian-laptop:/tmp$ sudo dpkg -i opera --force-remove-reinstreq
dpkg: error processing opera (--install):
 cannot access archive: No such file or directory
dpkg: error processing --force-remove-reinstreq (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 opera
 --force-remove-reinstreq
brian@brian-laptop:/tmp$ 

```

Please help!  I don't know what else to try.

---

### Post by brim4brim on 2007-06-11
Hey people, just thought I'd bump this thread as I've still not solved my problem.  Is this the right forum or should I post in General Help?

Anyway can anyone tell me how to solve the problem or if its solvable or what the story is?

---

### Post by brim4brim on 2007-06-11
Got this sorted.  I just added the Opera repositiories to my /etc/apt/sources.list file and ran sudo apt-get update.

I then just reinstalled it using sudo apt-get install Opera and it worked.

---

