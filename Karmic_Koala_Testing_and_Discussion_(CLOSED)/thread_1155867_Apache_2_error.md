---
title: "Apache 2 error"
date: 2009-05-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by coutts99 on 2009-05-11
```
* Restarting web server apache2 
/usr/sbin/apache2: error while loading shared libraries: /usr/lib/libaprutil-1.so.0: file too short
```

Any ideas anyone?

---

### Post by bigboy_pdb on 2009-05-11
I'm not positive about how that error message can be fixed, but more details might help. For example, have you modified any configuration files or is does this appear after a default installation?

You can try to reinstall the library (libaprutil1) or even Apache. If you've modified any configuration files or other files that are used by Apache, you can try removing the changes (or using a default setup) to see if one of them caused the problem.

---

### Post by coutts99 on 2009-05-11
Re-installing libaprutil1 has fixed this.

I did have to hard reset my machine this morning, so that maybe caused something odd?

---

### Post by bigboy_pdb on 2009-05-11
Granted that there's no reason for library files to be overwritten by the OS, it could be if file system information was being updated for some reason and the file size was listed as being different from the actual file size. However, I'm just speculating.

Regardless of what the case of the problem was it appears that the file was corrupted. Someone else might have a better idea of what did it.

It would probably be a good idea to mark your thread as being solved since other people get this error message for different files (and based my searches it didn't look as though many people knew the solution to the problem).

---

### Post by coutts99 on 2009-05-11
How do I change the thread topic to show [solved] ???

---

### Post by bigboy_pdb on 2009-05-11
You should be able to do it using the red "Thread Tools" link near the top of the page.

---

### Post by coutts99 on 2009-05-11
Nope :)

Just got options such as email, printable version, add poll, and something else.

I've often tried to work out how to do this and always failed :)

---

### Post by bigboy_pdb on 2009-05-11
As far as I know, that's always been the way to mark threads as solved, but I've only posted one thread and it was a long time ago. Perhaps you can't mark it as solved because of the section you posted it to (a community discussion section).

Maybe someone else can explain why it cannot be marked as solved.

(if you can't mark it as solved, it's not a big deal)

---

### Post by davideotape on 2009-05-11
I think that feature has been absent from the forums for a while (about 6 months) now. I just edit the title and add "[SOLVED]" at the beginning :D

---

