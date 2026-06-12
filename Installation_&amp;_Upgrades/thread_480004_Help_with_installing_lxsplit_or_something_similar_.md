---
title: "Help with installing lxsplit or something similar PLEASE!"
date: 2007-06-20
forum: Installation &amp; Upgrades
---

### Post by Shichao on 2007-06-20
I'm trying to get something similar to HJsplit on Ubuntu, and I found lxsplit but i can't install it correctly. This is what I did:

I first found a place to download it from.

Then, I used Gdebi Package Installer to install it.

Finally, I look for it but its not there!

PLEASE HELP!!!!!!!!!!!!!

---

### Post by 5-HT on 2007-06-20
It's a console app, you can add a menu entry for it using Alacarte if you wish.
To confirm:
```
which lxsplit
```will print out the path the the executable if it's installed.

FWIW: lxsplit really isn't necessary, you can always use 'cat' to concatenate files (and it's already installed as part of the coreutils package)

---

### Post by goonies on 2007-07-19
> **5-HT said:**
> It's a console app, you can add a menu entry for it using Alacarte if you wish.
To confirm:
```
which lxsplit
```will print out the path the the executable if it's installed.

FWIW: lxsplit really isn't necessary, you can always use 'cat' to concatenate files (and it's already installed as part of the coreutils package)

how do u use cat to merge the files?

---

### Post by 5-HT on 2007-07-20
> **goonies said:**
> how do u use cat to merge the files?

```
cat part1 part2 part3 > joined_file_name
```

---

