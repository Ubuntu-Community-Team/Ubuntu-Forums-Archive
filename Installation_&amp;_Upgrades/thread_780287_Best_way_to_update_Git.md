---
title: "Best way to update Git?"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by macaholic on 2008-05-03
I recently downloaded WebKit via git with ```
git clone git://git.webkit.org/WebKit.git WebKit
```
My question is, what is the best way to update this Git without downloading the entire thing over again? I download and compile compiz-fusion and a bunch of plugins via git, but I use a script that I mostly didn't write, so I'm not sure how it does it. Any help would be appreciated.

---

### Post by engla on 2008-05-03
To simply get the latest changes in webkit's upstream repository, and update your working copy to those changes you just run _git pull_ in the local repository directory ("WebKit")

If you have changed any files or committed to your local git repository there might be a conflict with the changes done upstream.. (however that seems unlikely here).

---

### Post by macaholic on 2008-05-03
Thanks, that's exactly what I wanted to do, I assummed it was something with git-pull, but I was adding unnecessary options it seems. I am currently testing the latest Epiphany SVN code with the latest webkit GIT code. Webkit sure is fast, and it's fun to score a perfect on the acid3 test, but their are other issues. Javascript is all funky, probably a 64-bit issue, and flash doesn't really work, but that's why I'm testing it.

---

### Post by engla on 2008-05-04
Git pull works without options, since it assumes you mean the 'origin' remote if you don't specify it. And the repository it was initially cloned from is always saved as 'origin'. You can do many other things, like using 'git fetch' to download the remote changes, and have a chance to look at them before deciding to merge them / implement them in your working directory.

I've seen this about flash on webkit:

swfdec:
[http://blogs.gnome.org/otte/2008/05/02/webkit-time/](http://blogs.gnome.org/otte/2008/05/02/webkit-time/)

nonfree flash:
[http://www.barisione.org/blog.html/p=128](http://www.barisione.org/blog.html/p=128)

---

### Post by longit7 on 2008-12-10
Sometime I "git pull" but can't update source code. How can I update.

EX: I have 2 project A & B
I standing on project A
step: 
git checkout B
git pull
message display update successful

But git pull not update project B, git pull update to project A but git branch you see on project B, Please answer for me reason??? I don't know how update exactly?????

Thanks,:confused:

---

### Post by longit7 on 2008-12-11
I have reason. Dev after finished not push to origin.

---

