---
title: "Redirect output of apt-get update"
date: 2019-04-03
forum: Installation &amp; Upgrades
---

### Post by huff2 on 2019-04-03
I would like to redirect the output that I normally see in the terminal when using the apt-get update command to a text file.

Ex. sudo apt-get update > exampleFile.txt (I would like to do the same with upgrade)

I get this warning: WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

Anyone care to enlighten a newbie as to exactly what I'm being warned about and why?

Thanks!

---

### Post by TheFu on 2019-04-03
**apt-get** is fine in scripts.
**apt** is constantly changing as they figure out the right level for ease of use vs complexity.

As for redirections, this is helpful: [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line)
You'll learn lots in there, including simple redirection of stderr and stdout file descriptors.

---

### Post by huff2 on 2019-04-03
@TheFu Nice! Thanks! I really appreciate the link.

---

