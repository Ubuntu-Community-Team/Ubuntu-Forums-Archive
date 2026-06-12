---
title: "Can I download software without installing it first?"
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by hackb0y294 on 2010-04-15
Is there a way to download software but not install it? I want to download the software on one computer that has internet access and install it on others that don't, but I don't want the software on the internet computer. I would like to be able to browse a repository like you can with the Package Manager, if possible. Any suggestions?

---

### Post by maybeway36 on 2010-04-15
The command:
```
sudo apt-get install -d somepackage
```
should download packages (to /var/cache/apt/archives) without actually installing any of them.
Also look into aptoncd, which puts packages onto a disc for you.

---

