---
title: "Graveman - HELP!"
date: 2005-06-21
forum: Installation &amp; Upgrades
---

### Post by kona0197 on 2005-06-21
How do I get Graveman to burn a CD? Every time I try to dulicate it says "operation failed" - any ideas?

---

### Post by k4p0w3r on 2005-06-23
[QUOTE=kona0197]How do I get Graveman to burn a CD? Every time I try to dulicate it says "operation failed" - any ideas?[/QUOTE]
 Hello, I use graveman alot. It is fantastic and hope it will become part of the main distro.
Does the error occur only in "duplication" mode?
To see if you get any more specific error, start graveman from a terminal please.

It might be that you (as a user) only have read rights to the device or that the cdr/rw is corrupt.
Try to run graveman as root. Same error?

---

### Post by kona0197 on 2005-06-24
How do I run graveman as root?

---

### Post by kona0197 on 2005-06-28
Anyone know how I can run programs as root?

---

### Post by Joeb on 2005-06-29
[QUOTE=kona0197]How do I run graveman as root?[/QUOTE]


If you are wanting to run graveman with root priveledges, from the command line, you would type:

```
 sudo graveman 
``` and enter your password when prompted.  

This would also allow you to see any error messages that might be generated.  Once that works, you can change the command in the menu to be gksudo graveman.

---

