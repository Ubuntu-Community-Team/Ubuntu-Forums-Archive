---
title: "where is the .vim folder?"
date: 2011-01-19
forum: Installation &amp; Upgrades
---

### Post by karpay on 2011-01-19
Hi,

I installed the vim in my computer and now I'm looking for the

~/.vim

folder and no such folder exists.

where is this folder?

---

### Post by Tipo on 2011-01-19
The ~ or 'tilde' character is used as a shortcut for identifying your home folder.

So, if your home directory is located in /home, then your .vim folder will be located in /home/username/.vim

The '.' in front of 'vim' also denotes that that particular folder is hidden (from things like nautilus). You can view it by using options with ls in the terminal:

```
$ ls -al
```

---

