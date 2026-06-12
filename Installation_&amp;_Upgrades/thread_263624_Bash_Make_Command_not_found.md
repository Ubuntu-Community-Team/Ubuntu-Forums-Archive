---
title: "Bash: Make: Command not found"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by roblisy on 2006-09-23
Hey all,

I'm really new to Unix, but not computers. Anyways, while trying to setup a simple LAMP project that hosts an auction site, I'v come across this error:
```

bash: make: command not found
```

This happens while trying to update Perl, installing libnet, and every other install I try.

My question is this: what the heck? I thought that make was installed and configured by default, I mean I know that it's pretty important.

I'm running the latest (6.06 Dapper Drake) Ubuntu Desktop version on x86.

---

### Post by K.Mandla on 2006-09-23
Try *sudo aptitude install build-essential*.

I think if you want make, you need those build-essential packages. They're not included in a default installation.

---

### Post by roblisy on 2006-09-23
Anyway to do this off of the default CD? I don't have easy net access on this box...

Thanks for the first comment!

---

### Post by K.Mandla on 2006-09-23
Unless I'm mistaken, those packages are on the alternate/install CD. Make sure the CD is still part of your repository list (or *sudo apt-add cdrom* to be sure), then enter the *sudo aptitude install build-essential* command.

---

### Post by aysiu on 2006-09-23
It's on both the Desktop CD *and* the Alternate CD.

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

