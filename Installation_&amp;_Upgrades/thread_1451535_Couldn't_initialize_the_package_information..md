---
title: "Couldn't initialize the package information."
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by mrudul on 2010-04-10
Hey all, 
I am trying to find the solution to problem where i get the message saying,

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '--2010-03-03' is not known on line 1 in source list /etc/apt/sources.list.d/mediauntu.list, E:The list of sources could not be read.'

I found similar problem posted earlier too but not exact one.

any help would be appreciated.

Thanks in advance. :)

---

### Post by emanuel.b on 2010-04-10
> 'E:Type '--2010-03-03' is not known on line 1 in source list /etc/apt/sources.list.d/mediauntu.list, E:The list of sources could not be read.'

Did you mean "medibuntu", instead of "mediauntu"? If so then you can disable the medibuntu source in "System -> Administration -> Software Sources", then try the update again.

---

### Post by mrudul on 2010-04-11
No, it is mediauntu. I copy pasted the exact message I got while initializing. :(

---

### Post by emanuel.b on 2010-04-11
Well, either way, you just deactivate it in "System -> Administration -> Software Sources", and run the update again...

---

### Post by mrudul on 2010-04-12
hmmm,

but after going there, when I try to reload the repository I got the following message

 Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

E: Type '--2010-03-03' is not known on line 1 in source list /etc/apt/sources.list.d/mediauntu.list
E: Unable to lock the list directory

E: Type '--2010-03-03' is not known on line 1 in source list /etc/apt/sources.list.d/mediauntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


what does it mean? can't update anything because of this problem. :(

---

