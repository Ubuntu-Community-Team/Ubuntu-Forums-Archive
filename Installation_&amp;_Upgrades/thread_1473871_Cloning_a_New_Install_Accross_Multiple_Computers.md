---
title: "Cloning a New Install Accross Multiple Computers"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by awells527 on 2010-05-05
**Basically what I want to do:**

I have several packages I install after an fresh Ubuntu install, and the new Software Center is very slow compared to gnome-app-install when adding my normal software packages.  What I would like to do is collect all the package names so I can save the list in a text file and install the packages from the CLI on other machines, but I do not know their package names, so my main roadblock is finding an efficient way to get all the package names I have on my computer.

So is there a program out there that groups the apps nicely like the Software Center but tells me the package names, or does the Software Log the installed package names somewhere?

**What I tried so far:**

On a fresh computer, I ran "dpkg --get-selections > before.txt" after the fresh install the get the base package list.  I then went through the long process of installing the extra software from the Software Center, and ran "dpkg --get-selections > after.txt" to get the second package list.  I then ran this:

```
diff before.txt after.txt | grep "> " > diff.txt
```

...to get a list of packages that changed, which should give me a complete package list of what I just installed.

The problem is that it is including all the dependencies, and I don't want to set those packages to manually installed.  Is there a possible way to filter out all the dependencies?

---

