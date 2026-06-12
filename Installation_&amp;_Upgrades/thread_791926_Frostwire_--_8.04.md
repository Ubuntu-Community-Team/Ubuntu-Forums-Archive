---
title: "Frostwire? -- 8.04"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by tardiaf on 2008-05-12
why wont my frostwire work with this new updated version of ubuntu 8.04? what should i do to fix this?

---

### Post by domness on 2008-05-12
I'm getting the same thing.

I click on the icon and it just doesn't start. I've not restarted since installing and this may be the problem.. but we shall see.

---

### Post by atomkarinca on 2008-05-12
First install sun-jre (if you haven't), open up a terminal (Applications > Accessories > Terminal) then type this:

```
sudo apt-get install sun-java6-jre
```

Then select sun-jre from installed java versions

```
sudo update-alternatives --config java
```

---

### Post by Tom--d on 2008-05-12
Frostwire worked for me when I installed it. (had sun-java6-jre installed)

but now use torrents.

---

### Post by tardiaf on 2008-05-13
> **atomkarinca said:**
> First install sun-jre (if you haven't), open up a terminal (Applications > Accessories > Terminal) then type this:

```
sudo apt-get install sun-java6-jre
```

Then select sun-jre from installed java versions

```
sudo update-alternatives --config java
```

thank you soo much! this somehow worked for me! i was gon be lost wit out it. gnutella sux, an torrents are too much work for when i only want a single song. i use torrents more for albums and movies. thanks again!!

---

### Post by atomkarinca on 2008-05-13
> **tardiaf said:**
> thank you soo much! this somehow worked for me! i was gon be lost wit out it. gnutella sux, an torrents are too much work for when i only want a single song. i use torrents more for albums and movies. thanks again!!

No problem.

---

### Post by Nero147 on 2008-07-07
This also helped me immensely. Also I would like to thank you for the succinctness of your reply.

---

