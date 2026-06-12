---
title: "How do I install anything?"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by projectgonewrong on 2007-03-08
Im gonna sound dumb asking this but I can't figured out how to install anything (other than with the Add/Remove Applications thing).  I tried installing Blender with the add/reomve apps thing and it did not work.  So i downloaded "blender_2.37a-1ubuntu1.diff.gz" and I have no clue how to install it.  What do I do with that file to install it?

---

### Post by bruenig on 2007-03-08
> **projectgonewrong said:**
> Im gonna sound dumb asking this but I can't figured out how to install anything (other than with the Add/Remove Applications thing).  I tried installing Blender with the add/reomve apps thing and it did not work.  So i downloaded "blender_2.37a-1ubuntu1.diff.gz" and I have no clue how to install it.  What do I do with that file to install it?

A .diff.gz won't ever install.

Do
```
sudo apt-get install blender
```

and if that doesn't work, paste what the problem is.

---

### Post by aysiu on 2007-03-08
Blender isn't in Add/Remove programs by default. It's in a separate (community-maintained) set of repositories called the Universe repositories. More on what repositories are here:
[http://www.ubuntu.com/ubuntu/components](http://www.ubuntu.com/ubuntu/components)

**First** you need to enable the Universe repositories. You can do by following these instructions:
[http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories](http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories)

**Second**, you can use Synaptic to install Blender--it lists all available applications, unlike Add/Remove Programs:
[http://monkeyblog.org/ubuntu/installing/#installing_with_synaptic](http://monkeyblog.org/ubuntu/installing/#installing_with_synaptic)

You may also want to read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by projectgonewrong on 2007-03-08
Reading package lists... Done
Building dependency tree... Done
Package blender is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package blender has no installation candidate

is the problem from that terminal thing

---

### Post by Kateikyoushi on 2007-03-08
You need to enable the universe reppositories, can do it in System > Administration > Software sources.

---

### Post by Ptero-4 on 2007-03-09
or you can wait a bit more until the final release of feisty comes out, feisty have the universe repos enabled by default.

---

### Post by aysiu on 2007-03-09
> **Ptero-4 said:**
> or you can wait a bit more until the final release of feisty comes out, feisty have the universe repos enabled by default.
While that's true...

Look at these choices:

1. Wait four weeks to upgrade to a new version of Ubuntu or do a clean reinstall of Ubuntu in order to easily install Blender.

2. Click a few buttons or copy and paste a few commands to get the Universe repositories enabled, and then easily install Blender now.

I'd say it's no contest.

---

### Post by bruenig on 2007-03-09
> **projectgonewrong said:**
> Reading package lists... Done
Building dependency tree... Done
Package blender is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package blender has no installation candidate

is the problem from that terminal thing

Alright, do this then.

```
sudo sed 's/# deb/deb/g' -i.backup /etc/apt/sources.list
sudo apt-get update 
sudo apt-get install blender
```

Just copy and paste them one by one.

---

