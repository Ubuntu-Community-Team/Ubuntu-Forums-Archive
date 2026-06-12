---
title: "Forcing an earlier package version?"
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by mdognrdog on 2006-11-29
Hello, everyone.

The network-manager that ships with Edgy is--at least on my machine--a significant step backward from the one I had with Dapper.  It drops connections every few minutes, and doesn't have an option (like the old one) to force it to stick with a given connection until told otherwise.

So I want to go back to the sweet wireless nirvana I once knew and loved.  Is there any way I can tell apt-get or Synaptic to force a given package, regardless of the systemwide repository settings?  I don't want to roll everything back, just that.

---

### Post by K.Mandla on 2006-11-29
Try checking the man pages for apt-get. There's an option for *install *that allows you to target a specific version of a package without interfering with the rest of the system. 

[http://www.die.net/doc/linux/man/man8/apt-get.8.html](http://www.die.net/doc/linux/man/man8/apt-get.8.html)

Look under *install*. 

[QUOTE=man pages]A specific version of a package can be selected for installation by following the package name with an equals and the version of the package to select.[/QUOTE]
Unless I'm mistaken, it will look something like *sudo apt-get install package_name=versionnumber* ... or something to that effect. 

There's also an [apt-preferences function]("http://www.die.net/doc/linux/man/man5/apt_preferences.5.html"), but I haven't used that.

---

### Post by mdognrdog on 2006-11-29
So I wouldn't set a repository, but a version number?  Do you know whether I have to remove the existing package and then install the new one?

---

### Post by mdognrdog on 2006-11-29
Hmm.  It looks like either

> 
sudo apt-get install package_name=version_number

sudo apt-get install package_name/Dapper


should work.  Will report once the attempt succeeds or fails...

---

### Post by mdognrdog on 2006-11-30
Nope.  I ran both

> sudo apt-get install network-manager/dapper

sudo apt-get install network-manager=0.6.2-0ubuntu7

And it told me that the release 'dapper' wasn't found for the package, and the version number wasn't found for the package.  This also happened after I re-added dapper repositories, and did an 'apt-get update'.

---

### Post by mdognrdog on 2006-11-30
Suggestions, anyone?

---

### Post by dcstar on 2006-12-01
> **mdognrdog said:**
> Hello, everyone.

The network-manager that ships with Edgy is--at least on my machine--a significant step backward from the one I had with Dapper.  It drops connections every few minutes, and doesn't have an option (like the old one) to force it to stick with a given connection until told otherwise.

So I want to go back to the sweet wireless nirvana I once knew and loved.  Is there any way I can tell apt-get or Synaptic to force a given package, regardless of the systemwide repository settings?  I don't want to roll everything back, just that.

Synaptic has a built in "Force Version" feature, just select the package and see what versions are available for it.

BTW, the previous version of a package **not** listed in the current repositories are most likely not going to work, you may be better off recompiling that package in your Edgy environment from the source (and even that may not go).

---

