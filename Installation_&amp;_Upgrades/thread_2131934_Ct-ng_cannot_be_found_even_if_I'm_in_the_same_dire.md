---
title: "Ct-ng cannot be found even if I'm in the same directory... :("
date: 2013-04-03
forum: Installation &amp; Upgrades
---

### Post by Flo89 on 2013-04-03
Hello Ubuntu-Friends,


I'm trying to get CrossTool NG working. 
So I did the three steps 
```
./configure --prefix=$HOME/somepath
To get this step running I had to install some packages, but all done.
make
make install
export PATH="${PATH}:/somepath/bin"

```
Also I added the Path above to /etc/environment

In the bin directory there is a file "ct-ng". But even if I switch to this directory with the terminal, I cannot run it because he tells me "ct-ng: command not found." or something like that (I'm using the german Version, so don't know whats the exact text in english)

What can I do to fix this?

Thanks for your time and help!
Florian

---

### Post by Flo89 on 2013-04-03
Oh, ./ does the thing :)

---

