---
title: "Installing a package without its dependencies"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by victor.zamanian on 2010-03-10
Hello!

I have git (the source code management tool) installed from source, because I like to keep it updated more frequently than the repositories are.

So now I hear of this new program called 'giggle', which depends on git-core. But, I already have git installed from source, but I'm assuming that doesn't show up in the apt database. So how can I install this giggle package, or any package for that matter, without installing its dependency *packages*. I mean I already have git, you know?

Will I be forced to install giggle from source as well?

---

### Post by mechro on 2010-03-10
Well, you could install the debian package direct from the Ubuntu package list. It's then up to you to install dependencies...

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

giggle for karmic...

[http://packages.ubuntu.com/karmic/giggle](http://packages.ubuntu.com/karmic/giggle)

---

### Post by victor.zamanian on 2010-03-10
Ah, thank you very much! I didn't think of that. What I finally did was:

```
$ sudo aptitude download giggle
$ sudo dpkg -i /var/cache/apt/archives/giggle[...].deb
```

And that's it! It gave me some warnings while installing, which is fine. However, when I ran giggle, giggle gave me a warning regarding not being able to find /usr/bin/git. Since I have installed git from source, i put git in /usr/local/bin/, so my solution to this was to also:

```
$ sudo ln -s $(which git) /usr/bin/
```
alternatively
```
$ sudo ln -s /usr/local/bin/git /usr/bin/
```

Thanks again!

---

### Post by victor.zamanian on 2010-03-10
I apologise for being so whimsical, but there's a big problem now with the apt database.

After installing giggle as in my previous post, now every time I want to use aptitude to install/remove anything, it keeps bugging me about fixing this "broken" package that is giggle. Its first suggestion for a fix is to remove the package, but none of the other suggestions I like either.

What can I do about this? :\

---

### Post by mechro on 2010-03-10
As long as you're aware that breaking packages/dependencies can cause you no end of trouble then this might help...

[http://ubuntuforums.org/showthread.php?t=187293](http://ubuntuforums.org/showthread.php?t=187293)

---

### Post by victor.zamanian on 2010-03-12
mechro,

That worked. The only problem is that giggle now for some reason thinks it has an update:

"giggle could be upgraded to version 0.4.95-0ubuntu1~ppa0, but it is being held at version 0.4.95-0ubuntu1~ppa0."

Same version or am I blind? :D And upon upgrading it it still requires git-core.

It's mostly nice to have a package manager, but as soon as you want to customize a little it breaks... I would rather compile everything myself (a la gentoo) but I don't have the patience to wait for the compilations to finish. ;)

---

### Post by mechro on 2010-03-13
I can't give you the relevant command (I'm more comfortable with GUI's) but if giggle is listed as installed in Synaptic Package Manager you can do **Package > Lock Version** from the menu and it might stop the upgrade/update notices.

---

### Post by victor.zamanian on 2010-03-13
mechro, yeah that's true!

You can start up aptitude without arguments:

$ sudo aptitude

then search the database, using the "/" key, for "giggle". Upon having the... shall we call it "cursor"? on the giggle package, press the "=" key to hold the package from updating.

Otherwise one can also just do:
$ sudo aptitude hold giggle

Thanks for the tip! (Although I won't be able to receive updates for this package now, it does solve some problems. :)

---

