---
title: "Problem with add/remove programs"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by NeonWrath on 2008-06-26
While using ubuntu with gnome, whenever I try to install anything using the add/remove programs program, I get this error message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

The solution appears to be simple. However I need to access a root terminal to do the above command. But the only way I know to do that is through the program in which I have this error, so I can't do it that way.

There has to be something I'm missing here.

---

### Post by dominiquec on 2008-06-26
Press Ctrl-F1 to get a console terminal.  Then run the command.

---

### Post by ibutho on 2008-06-26
Hi.

You need to do Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
```

---

### Post by dominiquec on 2008-06-26
By the way: press Ctrl-F7 to get back to graphic mode.

---

### Post by iaculallad on 2008-06-26
Get in your terminal and issue the command below (that's with sudo):

```
sudo dpkg --configure -a
```

---

### Post by iaculallad on 2008-06-26
> **dominiquec said:**
> Press Ctrl-F1 to get a console terminal.  Then run the command.

BTW: Ctrl+F1 would not pop your terminal.

That should be Ctrl+Alt+F1 to bring you to your virtual terminal.

---

### Post by dominiquec on 2008-06-27
I stand corrected.  Thanks iac.

---

