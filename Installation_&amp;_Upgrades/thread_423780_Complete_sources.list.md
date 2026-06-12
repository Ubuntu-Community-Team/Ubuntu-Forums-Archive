---
title: "Complete sources.list"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by FuzZy2006 on 2007-04-26
I didn't use ubuntu for the latest 5 months as I switched to sabayon. But now, because portage and its dependencies problems started to annoy me, i decided to switch back to ubuntu. Can anybody post a complete sources.list with some extra repositoriesfor feisty? From trevinho's repository to wine and all the others.

---

### Post by chakkaradeep on 2007-04-26
> **FuzZy2006 said:**
> I didn't use ubuntu for the latest 5 months as I switched to sabayon. But now, because portage and its dependencies problems started to annoy me, i decided to switch back to ubuntu. Can anybody post a complete sources.list with some extra repositoriesfor feisty? From trevinho's repository to wine and all the others.

Generate the sources.list [here]("http://www.ubuntu-nl.org/source-o-matic/") for your ubuntu release and enjoy :guitar:

---

### Post by FuzZy2006 on 2007-04-26
I'm talking about the repositories that are not maintained by ubuntu. Example trevinhos repository.

---

### Post by zvacet on 2007-04-26
[http://www.ubuntugeek.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html#more-87]("http://www.ubuntugeek.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html#more-87")

Replace Edgy with Feisty 


```
 sudo sed -e 's/\sedgy/ feisty/g' -i /etc/apt/sources.list 
```

---

