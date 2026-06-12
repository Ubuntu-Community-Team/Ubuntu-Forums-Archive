---
title: "installer kernel command-line options"
date: 2005-10-23
forum: Installation &amp; Upgrades
---

### Post by dannysauer on 2005-10-23
Is there a list somewhere of options that can be passed to the installer kernel from the initial boot?  Specifically, say I have my own local mirror at [http://machine/ubuntu](http://machine/ubuntu).  So I'd like to just say something like "server mirror=http://machine/ubuntu" at the boot prompt.  Presumably there *are* options kinda like that - are they listed anywhere?  I'll bet there's something useful there which I haven't thought of but which will just strike me as terrifically handy once I'm aware of it... :)

---

### Post by 5-HT on 2005-10-23
There are tons of boot options, though the problem is finding out what they all are...

I'm not sure how solve your problem, but I was trying to search for boot options for a problem I was having and didn't run into much luck.

I did find some info though:

1. Try the 'bootparam' man pages
```
 man bootparam 
```

If you haven't finished installation, or don't have access to a *nix machine, the man pages are posted throughout the net, so do a search for the bootparam manual pages and I'm sure you'll find it.

2. The installer itself describes a few boot options, just press the help key (F1 I believe) and there'll be a few there.

3. Knoppix, a live-cd distro based on Debian has a really good cheat-sheet of boot options, I used to have a copy but lost it, though if you look up knoppix cheat-sheet, there shouldn't be any problems finding it.

One note though, the Knoppix boot options may not all work in Ubuntu.

Hope that helps,

---

