---
title: "Can't download beryl packages"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by DuXati on 2007-10-29
Hi,

I'm trying to install Beryl on Ubuntu Gutsy Gibbon. I'm following the tutorial at

[https://help.ubuntu.com/community/CompositeManager/Beryl/Edgy]("https://help.ubuntu.com/community/CompositeManager/Beryl/Edgy")

and everything was going fine up till now. I've installend the appropriate ATI driver as told, added sources etc. 
Now I'm trying to download the beryl packages with Synaptic Package manager but this gives an error saying:

```
The following packages have unresolvable dependencies. 
Make sure that all required repositories are added and enabled in the preferences.

beryl:
 Depends: beryl-settings but it is not going to be installed
 Depends: beryl-manager but it is not going to be installed
```

My sources are correct, as every possible option is checked as downloadable and the beryl packages can be found in the first place.
When I try to download the given packages beryl-settings and beryl-manager, the error return but with other packages. If I proceed on doing this, I eventually end up downloading beryl-settings-bindings, which gives an other error:
```

The following packages have unresolvable dependencies. 
Make sure that all required repositories are added and enabled in the preferences.

beryl-settings-bindings:
  Depends: python (<2.5) but 2.5.1-1ubuntu2 is to be installed
```

What should I do to solve this problem?? I can't just remove python 2.5 which is indeed installed... Should I just install python 2.4 too?

 I've never encountered an error like this and can't find anything specific about it on Ubuntu Forums nor Google, so help would be greatly appreciated!

Tnx for reading this post in the first place :)

DuXati

---

### Post by thelocust on 2007-10-29
Why don't you go with compiz? It's on the repos.

---

### Post by DuXati on 2007-10-30
Thanks dude, I'm a newbie, didn't know that :p

---

### Post by thelocust on 2007-10-30
Gusty should aready have it installed for you.

---

