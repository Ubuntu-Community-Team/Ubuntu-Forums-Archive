---
title: "Use the same home for Ubuntu and Debian"
date: 2005-09-27
forum: Installation &amp; Upgrades
---

### Post by gatopolar on 2005-09-27
Hi list.

I have a Debian workstation and I would like to install Ubuntu on it. I would like to use the same home, tmp and swap partitions. I doubt if I will have some troubles because I use the same home directory and the same user.. Because I know there are some configuration directories in it. 
Is it somehow dangerous to make the installation as I described?

Thank you in advance.

Gatopolar.

---

### Post by lordofkhemenu on 2005-09-27
[quote=gatopolar]Hi list.

I have a Debian workstation and I would like to install Ubuntu on it. I would like to use the same home, tmp and swap partitions. I doubt if I will have some troubles because I use the same home directory and the same user.. Because I know there are some configuration directories in it. 
Is it somehow dangerous to make the installation as I described?

Thank you in advance.

Gatopolar.[/quote] As long as your /home directory is an actual **partition** and not just a directory, you shouldn't have any issues. I've installed several distros utilizing the same /home directory|partition. You just have to remember to use the custom partitioning options available.
Now if it's just a directory, you may have a little more thinking, planning to do.
Before I figured out the whole "/home as a partition" thing, this was a sticky in my brain:[INDENT][LIST]
[*]*Burn your home directory to a CD. The next time you install a distro be sure to create a seperate partition and use it as /home.*[/LIST][/INDENT]Others may have different, more useful advice. Mine is just from my own personal experiences.

---

### Post by gatopolar on 2005-09-27
[QUOTE=lordofkhemenu]As long as your /home directory is an actual **partition** and not just a directory, you shouldn't have any issues. I've installed several distros utilizing the same /home directory|partition. You just have to remember to use the custom partitioning options available.[/QUOTE]

Hi
It is a partition. My question was about, for example Mercury
When I installed it, it put a Mercury directory inside my home folder. I don't know Mercury will try to install a new folder and delete the old one. This could be applicable to any software.

But if you say that you haven't had any problem.

Thanks!

Gatopolar.

---

### Post by katu on 2005-09-27
I installed kubuntu in place of a debian/sid (/home as a separate partition). The only thing that needed changing was the .kde config directory, but then I didn't use kde for at least over a year, so it was pretty old. 
I think, that if you make sure that you have the packages in versions as close to eachother as possible it should be ok. 
Also most packages check for an existing configuration directory before trying to write a new one. At least from my experience ;)

---

