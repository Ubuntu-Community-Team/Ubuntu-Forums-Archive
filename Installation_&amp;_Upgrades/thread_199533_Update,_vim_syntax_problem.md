---
title: "Update, vim syntax problem"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by paulur on 2006-06-18
After the update, vim syntax on doesn't work, and show the following errors:

Error detected while processing /usr/share/vim/vim64/syntax/syntax.vim:
line   42:
E216: No such group or event: filetypedetect BufRead


Many thanks!

Paul

---

### Post by ijsje on 2006-06-19
Same problem here, I solved it by editing **/etc/vim/vimrc** :

At the second line, change **/usr/share/vim/vim63** to [B]/usr/share/vim/vim64
[/B]

---

