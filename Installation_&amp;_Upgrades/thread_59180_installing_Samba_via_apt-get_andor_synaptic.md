---
title: "installing Samba via apt-get and/or synaptic"
date: 2005-08-23
forum: Installation &amp; Upgrades
---

### Post by indianatom on 2005-08-23
Hello, I'm  having trouble installing samba.  I would normally just use "sudo apt-get install samba" or synaptic, but I get the following error message: 
```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.10-1ubuntu3) but 3.0.14a-3ubuntu3~5.04ubp1 is to be installed
E: Broken packages
```

According to apt-get I do have samba-common installed: 3.0.14a-3ubuntu3~.

Any help would be great.  Thanks!

Eric

---

### Post by indianatom on 2005-08-23
Nevermind, I found the solution was using Synaptic under "Package" select "Force Version" and use the one it wanted.

---

### Post by realbt on 2005-08-23
I'm having the same problem. And there is another [thread](http://www.ubuntuforums.org/showthread.php?t=44406) with the same problem.

Anyone have any suggestions other than forcing it?

Thanks.

---

### Post by hangon418 on 2005-08-23
lol i was just at that other thread. exact same problem

---

### Post by realbt on 2005-08-23
[QUOTE=hangon418]lol i was just at that other thread. exact same problem[/QUOTE]

Sure would be nice to get this one sorted out!

I'm starting to get worried that I've screwed up all my dependencies somehow.

---

### Post by hangon418 on 2005-08-23
> I'm starting to get worried that I've screwed up all my dependencies somehow. 
yeah same here. if other people did the exact same thing i did.

---

