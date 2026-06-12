---
title: "A couple of questions regarding Mozilla Thunderbird..."
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by Quillz on 2007-03-03
[LIST]
[*]When is 1.5.0.10 going to be added to the repositories? It's been out for a few days now.
[*]I am interested in running Thunderbird 2.0 Beta 2, although my 1.5.0.9 is being managed by the package manager. Is it "safe" to overwrite the packaged installation, or will the overwrite keep the package manager from keeping track of updates and what not? Is it possible to install 2.0 Beta 2 separately from 1.5.0.9?[/LIST]

---

### Post by flossgeek on 2007-03-03
Of course, you can run the new version in your home directory,

---

### Post by mahy on 2007-03-03
Sigh! No insider ever answers such questions. It is almost as if they kept it purposefully secret. Judging from experience, allow 3 or 4 weeks.

---

### Post by Quillz on 2007-03-03
> **flossgeek said:**
> Of course, you can run the new version in your home directory,
Sorry, a bit lost here. Are you saying I can set up a new profile in the home directory, or I should install the entire Beta 2 into my home directory?

---

### Post by mahy on 2007-03-04
> **Quillz said:**
> Sorry, a bit lost here. Are you saying I can set up a new profile in the home directory, or I should install the entire Beta 2 into my home directory?

you can download the newest Thunderbird (.tar.gz format), unpack it somewhere to your home directory and run. Just don't forget to do

```
mv ~/.mozilla-thunderbird ~/.thunderbird
```

because the generic (i.e. not Ubuntu-ized) Thunderbird uses different default profile location. Cheers!

---

### Post by Quillz on 2007-03-07
> **mahy said:**
> you can download the newest Thunderbird (.tar.gz format), unpack it somewhere to your home directory and run. Just don't forget to do

```
mv ~/.mozilla-thunderbird ~/.thunderbird
```

because the generic (i.e. not Ubuntu-ized) Thunderbird uses different default profile location. Cheers!
I'll try this, thanks for the help.

---

