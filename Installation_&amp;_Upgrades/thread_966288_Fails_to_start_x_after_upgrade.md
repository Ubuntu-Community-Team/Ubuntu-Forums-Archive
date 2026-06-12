---
title: "Fails to start x after upgrade"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by joeri_83 on 2008-11-01
I just upgraded to 8.10 and now the XServer won't start. I get the Ubuntu screen, but then it jumps out to a console, and show me a bluescreen saying that it failed to start the x server. If I choose to look at the diagnostics it says:

[INDENT]Warning: Failsafe mode was already attenmpted within 30 seconds
Warning: Falling back to gdm to report the issue[/INDENT]

When I hit ok it tells me to restart gdm when it is configured correctly.

I then get to the console login, above which it says "kinit: No resume imagage, doing normal boot"

What has gone wrong, and how do I solve it? I would appreciate any help!

---

### Post by joeri_83 on 2008-11-01
I found the following in /var/log/Xorg.0.log

```

Warning, couldn't open module type1
UnloadModule: "type1"
Failed to load module "type1" (module does not exist, 0)

```

I am using the Nvidia GLX 177.80 btw.

The log file goes on to say:

```

Screen 0 deleted because of no matching config section
...
Device(s) detected, but none match those in the config file

Fatal server error:
no screens found

```

And that's it.

---

### Post by joeri_83 on 2008-11-01
Ran xfix from recovery mode and then reinstalled the nvidia drivers and that appears to have done the trick! :) Hope that helps some other unlucky soul.

---

### Post by gmlinux on 2008-11-01
I would like to see the answer to this also. I get the exact same thing, my graphics card and monitor are not detected. If I try to reconfigure the x server, the only item it has for configuration is the keyboard.Even if I knew how to get back to 8.04 would be fine.

---

