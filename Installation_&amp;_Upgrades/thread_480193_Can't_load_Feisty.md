---
title: "Can't load Feisty"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by coulomb on 2007-06-21
I am posting this again because I filled in the title incorrectly before.


Having moved from XP to Ubuntu Feisty with great success on my desk-top I decided to change over on my laptop also.
When booting from the Ubuntu CD I get the error message "Error in starting Gnome settings Daemon........" later it gets to the screen with the horizontal rectangle with the word Ubuntu on the right, but even though there is continuous activity in the CD and the hard-drive there is no further progress.  I get the same result with a DVD which I have. I have tested the CD and the DVD on my desk-top successfully.
Can anyone help please?

---

### Post by jonthysell on 2007-06-21
I'm getting the same problem on my laptop.

Dell Latitude CPi D266XT

Just to get the machine to boot, I had to add

```
ide=nodma acpi=off
```

to the boot options.

If it's a sound issue with Gnome, I know how to resolve it once I have a working linux install, which I can't get to if the LiveCD never finishes booting.

Is there anyway to go straight to command line or do a direct install from the livecd without actually booting the livecd? I'm on dialup speeds in Africa, so saying "just download the alternate cd" doesn't really help.

Thanks.

---

