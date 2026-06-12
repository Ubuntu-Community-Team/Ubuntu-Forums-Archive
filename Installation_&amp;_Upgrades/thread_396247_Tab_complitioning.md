---
title: "Tab complitioning"
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by christooss on 2007-03-29
I have seen working tab complitioning in right way. But it doesn't seem to work on my Ubuntu installation.

Let me refrase this.

sudo apt-get install fire<tab>
sudo apt-g<tab>

How can I make it work?

---

### Post by Hase on 2007-03-30
What *is* it doing when you press tab?  Nothing or something less-than-desirable?

---

### Post by christooss on 2007-03-30
It doesnt do nothing

---

### Post by yabbadabbadont on 2007-03-30
Edit /etc/bash.bashrc and uncomment the section for bash_completion.  Then logout and back in.

Edit:  This part:
```
# enable bash completion in interactive shells
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

```

---

### Post by christooss on 2007-04-05
Now when starting Terminal i get

enable: bash: not a shell builtin
bash: enable: completion: not a shell builtin
bash: enable: in: not a shell builtin
bash: enable: interactive: not a shell builtin
bash: enable: shells: not a shell builtin

---

### Post by yabbadabbadont on 2007-04-05
You removed the comment symbol "#" from the comment that is above the "if" statement....  put it back.  :D

It should look exactly like what I posted.

---

### Post by christooss on 2007-04-05
Ups

Thanks again for help

---

