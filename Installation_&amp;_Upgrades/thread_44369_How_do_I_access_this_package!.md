---
title: "How do I access this package?!"
date: 2005-06-25
forum: Installation &amp; Upgrades
---

### Post by arjun on 2005-06-25
Hi, I'm new to Ubuntu and linux in general.  I installed the VIM editor for gnome via synaptic but i don't know how to get into it now.  Every other program i installed conveniently went into my applications menu; can someone please tell me how i can get VIM in the applications menu.  Thanks

---

### Post by alastair on 2005-06-25
Maybe type "gvim"? Else, "vim".

---

### Post by arjun on 2005-06-25
both 'gvim' and 'vim' take me to a help document.

---

### Post by Xian on 2005-06-25
Vim is a command line editor. It won't open like a GUI package.
You access it from a teminal.

Here's a link to a Vim help page: [Vim Online Doc](http://vimdoc.sourceforge.net/vimfaq.html) & [Running Vim For The First Time](http://vimdoc.sourceforge.net/htmldoc/usr_02.html#02.1).

EDIT: For example here's how you can edit a text file in vim.
Just open a terminal and issue this command:
```
$ sudo vim /etc/fstab
```

---

