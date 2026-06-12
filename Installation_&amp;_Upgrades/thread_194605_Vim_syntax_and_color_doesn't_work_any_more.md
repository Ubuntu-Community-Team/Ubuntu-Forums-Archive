---
title: "Vim syntax and color doesn't work any more"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by washman on 2006-06-11
Hi all,

I updated my ubuntu to 6.06 last night, everything went well except that the new vim can not highlight syntax and show colorscheme.

I have "syntax on" and "colorscheme desert" command in /etc/vim/vimrc, they work fine for the old version. Now when I try to open vim, it showed: "can not find desert color scheme". Can anybody help me to resolve this problem? Thank you in advance.

---

### Post by kabus on 2006-06-11
I don't know what causes the problem, but the easiest way to fix it would probably be to create a ~/.vim/colors directory if it doesn't exist, then [download the desert theme]("http://www.vim.org/scripts/script.php?script_id=105") and save it there.

---

### Post by washman on 2006-06-14
thanks, I resolved the problem by installing  vim7 from source, 
but I still wonder why that problem occurred.

---

