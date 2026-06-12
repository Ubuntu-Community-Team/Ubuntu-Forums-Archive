---
title: "Can't use ADD/REMOVE"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by penguinchrissy on 2006-06-12
I'm trying to use Add/Remove Applications to get a couple of apps. This is what I get when I try
Cannot install 'kalzium'
This application conflicts with other installed software. To install 'kalzium' the conflicting software must be removed before.

Switch to the advanced mode to resolve this conflict.

What is wrong and how can I reslove the problem.

---

### Post by aysiu on 2006-06-12
If you have conflicting software, it may mean you have conflicting repositories.

I'd say get a fresh list...
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

... and then try ```
sudo aptitude update
sudo aptitude install kalzium
```

---

### Post by penguinchrissy on 2006-06-12
that worked and thank you now I have the problem of removing programs I don't want or use 
> Cannot remove 'gnome-games' One or more applications depend on 'gnome-games'. To remove 'gnome-games' and the dependent applications, please switch to the advanced software manager.

I have trouble beliving that the system NEEDS games to run so how can I remvoe these if you need a list of programs I would like to remove I can supply one

---

### Post by aysiu on 2006-06-12
Probably the only "application" that depends on *gnome-games* is *ubuntu-desktop*, which you can safely remove, as it's not an application at all--just a "metapackage" that refers to or points to all the default Gnome packages for Ubuntu.

By the way, if you're trying to diagnose problems, it's probably better to use Synaptic Package Manager ("the advanced software manager") or the command-line. Add/Remove Programs is really just for quick-and-dirty installations and removals.

---

