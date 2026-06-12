---
title: "Update Situation"
date: 2010-07-09
forum: Installation &amp; Upgrades
---

### Post by bigsmitty64 on 2010-07-09
10.04 Lucid 32bit desktop  
So.....I'm having THIS little problem with updates. Whenever I try and update, I get the message in pic #1 that leads to pic #2. Any help is greatly appreciated :)

---

### Post by davidmohammed on 2010-07-09
go to your software sources and other tab - untick the ppa in your message as well as medibuntu.  Try updating again.

---

### Post by wojox on 2010-07-09
Run these two commands in the terminal and it should fix it:

```

gpg --keyserver pgpkeys.mit.edu --recv-key  2EBC26B6OC25A783 
gpg -a --export 2EBC26B6OC25A783 | sudo apt-key add -

```

If I screwed up the numbers replace them with the one in your picture.

---

### Post by bigsmitty64 on 2010-07-09
Thanks davidmohammed, that worked. =D>

---

### Post by bigsmitty64 on 2010-07-09
> **wojox said:**
> Run these two commands in the terminal and it should fix it:

```

gpg --keyserver pgpkeys.mit.edu --recv-key  2EBC26B6OC25A783 
gpg -a --export 2EBC26B6OC25A783 | sudo apt-key add -

```If I screwed up the numbers replace them with the one in your picture.

should I do this instead? or also? or what? hahaha!

---

### Post by wojox on 2010-07-09
If you want medibuntu updated you should.

---

### Post by davidmohammed on 2010-07-09
wjox... beat me to it...

---

### Post by bigsmitty64 on 2010-07-09
o.k. thanks wojox , so I should **recheck** those, and then run the commands you gave?

---

### Post by wojox on 2010-07-09
> **bigsmitty64 said:**
> o.k. thanks wojox , so I should **recheck** those, and then run the commands you gave?

Give it a go.

---

### Post by bigsmitty64 on 2010-07-09
Thanks guys, got it with wojox's commands. I just had to tighten up the space between
```
key   2EBC26B6OC25A783
``` and then remove one number. But it worked. Again thanks for the quick replys!

---

