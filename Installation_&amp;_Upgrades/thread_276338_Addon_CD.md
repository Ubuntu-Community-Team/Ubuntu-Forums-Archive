---
title: "Addon CD"
date: 2006-10-12
forum: Installation &amp; Upgrades
---

### Post by artinla on 2006-10-12
The addon CD for breezy was great for people that have no internet connection, but the latest one for Dapper (done by a different person) has no install script.  It is just a repository CD, which means that I have to manually install each package, and that stuff like flash7 and java are nearly impossible to get configured and working.

Is there an install script that goes along with this CD? Is there another project similar to the old addon cd by mrbass?  I really truly miss his CD's.

I really need something that will just plug in and install the most popular stuff without requiring a net connection.  Can anyone suggest something?

Thanks,

Art

---

### Post by aysiu on 2006-10-12
If it's a repository CD, can't you just add it as a repository? ```
sudo apt-cdrom add
```

---

### Post by artinla on 2006-10-12
I can, but there are hundreds of packages on it and I would have to install each one, one at a time.  A few of them I don't want, such as the ipod software.. and some of them such as java and flash require more work than just installing the .deb

The old CD had a script that you ran and it just installed everything for me.  I am not knowledgeable enough to know each specific packages dependencies and what order they need to be installed in.  I am sure I am not the only one who misses the ease of mrbass's CD.

---

### Post by aysiu on 2006-10-12
If you add the CD as a repository, you don't have to know which packages to install and in which order.

You can just fire up Synaptic Package Manager or Adept and select the packages you want. The package manager will take care of all the dependencies for you--that's what it's there for; that's why it's called a *manager*.

If you don't know how to use Synaptic, read this:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by artinla on 2006-10-13
I know how to use Synaptic.

Re-read my original post and you will see that I am looking for a script or CD that eliminates the NEED for selecting hundreds of packages in synaptic.

Art

---

### Post by aysiu on 2006-10-13
> **artinla said:**
> I know how to use Synaptic.

Re-read my original post and you will see that I am looking for a script or CD that eliminates the NEED for selecting hundreds of packages in synaptic.

Art
The fact that you wrote this > I am not knowledgeable enough to know each specific packages dependencies and what order they need to be installed in.  leads me to believe you **don't** know how to use Synaptic, seeing as how Synaptic takes care of all the package dependencies. You do not need to know the package dependencies.

Just mark Flash for installation, and if there are dependencies for it, those dependencies will also be installed.

---

