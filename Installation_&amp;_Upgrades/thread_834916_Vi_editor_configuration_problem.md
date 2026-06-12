---
title: "Vi editor configuration problem"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by kiranbhalgat on 2008-06-19
Hi,
 I am using ubuntu 6.06 version and i have problem related to vi editor.
when i am in insert mode and i try to up and down arrow keys its print "A" or "D" letters.
 I try to reinstall vim editor, also set default but its not work.
Ayy Hint?

-Thank in advance,
Kiran

---

### Post by p_quarles on 2008-06-20
How are you initializing the application? With the command "vi" or "vim"? It makes a difference.

---

### Post by wormser on 2008-06-20
I had that [problem]("http://ubuntuforums.org/showthread.php?t=424480&highlight=vim") before.  You need to install the full version of vi.  The vi command will now work.  I think it links to vim.

```
sudo apt-get install vim-full
```

---

