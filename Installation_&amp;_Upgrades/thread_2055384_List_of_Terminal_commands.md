---
title: "List of Terminal commands"
date: 2012-09-09
forum: Installation &amp; Upgrades
---

### Post by Danpeters on 2012-09-09
I want to have the list of all terminal commands and what they do.

---

### Post by raja.genupula on 2012-09-09
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---

### Post by Danihan on 2012-09-09
[http://linuxpoison.blogspot.com/2008/10/useful-commands-in-ubuntu.html](http://linuxpoison.blogspot.com/2008/10/useful-commands-in-ubuntu.html)

---

### Post by Lars Noodén on 2012-09-09
You can generate a list of what's on your machine:

```

for j in $(ls /usr/local/bin/ /usr/bin/ /bin/ /usr/local/sbin /usr/sbin /sbin | sort -u );do man $j | head -n 7 | grep ' - ';done 2>/dev/null | less

```

---

### Post by jerrrys on 2012-09-09
[Terminal commands]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=terminal+commands&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F")

---

### Post by oldos2er on 2012-09-09
> **Danpeters said:**
> I want to have the list of all terminal commands and what they do.

Hit the Tab key twice. Most commands have a manual entry, so to get help with the 'ls' command, for example, you'd enter ```
man ls
```

---

