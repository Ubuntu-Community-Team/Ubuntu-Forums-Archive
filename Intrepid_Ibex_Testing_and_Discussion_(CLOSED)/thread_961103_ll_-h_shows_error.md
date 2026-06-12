---
title: "ll -h shows error"
date: 2008-10-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-10-28
Hi all, 
 I have enabled ll alias in my .bashrc 

```

# some more ls aliases
alias ll='ls -l'
alias la='ls -A'
#alias l='ls -CF'

```

And it was running fine till yesterday's updates 

now it gives error while running. 

```

$ ll *.torrent
ls: invalid option -- '_'
Try `ls --help' for more information.

```

So can anybody help

---

### Post by marmuta on 2008-10-28
Do any of your files happen to start with "-"?
Try if this works:
```
ll -- *.torrents
```

---

