---
title: "New install; multiple examples of 'unable to open file '/etc/dconf/db/site'' -why?"
date: 2021-10-08
forum: Installation &amp; Upgrades
---

### Post by greatbridge on 2021-10-08
On my new install of Ubuntu Studio 21.04 when I used the Konsole I am finding many instances of the error message "unable to open file '/etc/dconf/db/site'" - and, indeed, that file does not exist. I do not understand what this file does or why it is missing. Since this is my first attempt to install and use Ubuntu Studio, I assume this is a user error. Any advice?

---

### Post by ActionParsnip on 2021-10-09
What is the output of
```

lsb_release -a
uname -a
apt-cache policy konsole

```

---

### Post by greatbridge on 2021-10-10
Thanks for the reply - I was finding so many errors - all of which I assume to be my fault - that I am trying a clean re-install.

---

