---
title: "Enabling &quot;Universe&quot; at the install stage"
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by gavinbeatty on 2007-08-02
Hello,

I'm indirectly associated to a group of fellows installing edubuntu (not sure which version) en masse and they'd like to have the "Universe" repository enabled by default.

What would be the best way to do this?

Thanks,
Gavin

---

### Post by Seisen on 2007-08-02
It's not enable by default because they Ubuntu doesn't provide security updates or and support for it. They can add the Universe Repository either by using Synaptic or by edit the source list.

Synaptic:
Go to System>Administration>Synaptic Package Manager. Then click on Settings<Repositories then check the box that says Community Maintained Open Source software (universe). After you make that change close it out and hit reload.

Using text editor:
In a terminal
```
sudo text editor /etc/apt/sources.list
``` change text editor to which every one you like using and if it gedit or kay change** sudo **to** gksudo**. Then add this line

```
 deb http://us.archive.ubuntu.com/ubuntu/ Feisty universe 

```
If they are using the Edgy than change Feisty to Edgy. Save the file and then run

```
sudo apt-get update
```

---

### Post by gavinbeatty on 2007-08-02
I already understand. "Universe" is not an official Canonical-supported repos, at least in some sense. This is fine.

I also understand how to add the repos to sources.list.

What I would like to know is if there is any way that this step could be skipped either by:
-1-
"Patching" the install CD in some way.
-2-
Some boot option I have missed and the info needed to roll my own install CD with this "Add Universe" option set.
-3-
Something I haven't thought of.


I'm well versed enough in Debian. I'd just like to know if there are any options apart from manually doing

```

sudo echo 'deb http://us.archive.ubuntu.com/ubuntu/ Feisty universe' >> /etc/apt/sources.list
sudo aptitude update

```

And what's this "text editor" you speak of? Is it like vim?
Yes, yes, I'm sick of that flame too - just so you know I'm not a newb. ;)

---

### Post by Seisen on 2007-08-02
What i meant by text editor was some people like using vim others like nano, gedit or kate so they should replace text editor with their favorite text editor.

The only thing I can think of to help you is reconstructor.

[http://reconstructor.aperantis.com/]("http://reconstructor.aperantis.com/")

---

