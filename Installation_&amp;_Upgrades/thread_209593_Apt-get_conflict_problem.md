---
title: "Apt-get conflict problem"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by Hanj on 2006-07-05
I was trying to install kvim, and found an ubuntu deb for it, which I downloaded and tried to install. The installation failed with some error message I can't remember, and now I can't run vim or gvim anymore as the binaries seem to have disappeared. Synaptic still claims both vim and vim-gtk are installed though. When I try apt-get upgrade I get this:
```

Setting up vim (6.4-006+2ubuntu6) ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/bin/vim to /usr/bin/vim.org by vim'
  found `diversion of /usr/bin/vim to /usr/bin/vim.org by kvim'
dpkg: error processing vim (--configure):
 subprocess post-installation script returned error exit status 2
Setting up vim-gnome (6.4-006+2ubuntu6) ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/bin/vim to /usr/bin/vim.org by vim-gnome'
  found `diversion of /usr/bin/vim to /usr/bin/vim.org by kvim'
dpkg: error processing vim-gnome (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 vim
 vim-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How do I get out of this mess and get my precious vim back?

---

### Post by zhoux on 2006-07-05
perhaps a reinstall of vim would work?

---

### Post by Hanj on 2006-07-05
Tried it already, and it gives me the same error messages.

---

### Post by Hanj on 2006-07-08
No one? Please?

EDIT: solved it by removing /usr/bin/vim.org

---

