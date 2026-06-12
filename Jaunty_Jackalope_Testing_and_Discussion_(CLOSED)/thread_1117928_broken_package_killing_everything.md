---
title: "broken package killing everything"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by skydiver|goose on 2009-04-06
When I try and run apt-get update/upgrade, I get the following:

[http://goose.pastebin.com/f60cd6f8](http://goose.pastebin.com/f60cd6f8)


I also cannot setup my nvidia videocard driver, as when I try and activate the resctricted driver, I get:

SystemError: E:I wasn't able to locate file for the hotkey-setup package. This might mean you need to manually fix this package.


I am totally lost. I'm on 9.04 beta, x64.

---

### Post by issih on 2009-04-06
In essence a script thats meant to be run during the removal/upgrade of hotkey-setup is failing.

The file is:
/etc/init.d/hotkey-setup:

and on line 47 it is failing because of this error:
47: Syntax error: ";;" unexpected (expecting "fi")

Beyond that I'd need to see the actual script to see what it was trying to do.

In essence its a bad package, and is worth reporting as a bug in launchpad.

---

### Post by skydiver|goose on 2009-04-06
How do I report it/find the script? it's driving me crazy, because without the NVIDIA driver, *everything* runs ridiculously slowly

---

### Post by issih on 2009-04-06
Theres a bug already:

[https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/356157](https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/356157)

and a patch is here:

[http://launchpadlibrarian.net/24860190/hotkey-setup.missing-fi.patch](http://launchpadlibrarian.net/24860190/hotkey-setup.missing-fi.patch)

save that text to a file named patchfile and then run:

```
patch /etc/init.d/hotkey-setup < pathto/patchfile
```

Where the pathto is the directory you put the patchfile in.

I think that is the right syntax (Note you may need to be root, i.e. use sudo)

Hopefully that will fix the file and the upgrade will then run smoothly.

N.B. it might be worth saving a backup of the script before patching it.

Hope that helps

---

### Post by SketchyClown on 2009-04-06
Patch works like a charm. Thanks for that. :KS

---

