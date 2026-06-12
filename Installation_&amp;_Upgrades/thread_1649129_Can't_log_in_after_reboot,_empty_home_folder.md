---
title: "Can't log in after reboot, empty home folder"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by musclemanjr on 2010-12-19
Hi everybody,

I recently installed Ubuntu 10.10 on my machine. I logged in and installed a few programs like wine. Everything went fine until I rebooted. Now, after I log in, it gives me 2 error messages:

One about how it could not update ICEAuthority or something

Another about how usr/lib/libconf2-4/gconf-sanity-check2 returned status 256.

Then, something else pops up about how Nautilus can't find or doesn't have permission to write to home/user/Desktop and home/user/.nautilus.

I tried booting in recovery mode and did a dir on /home, but nothing showed up, which makes me think that they somehow disappeared or they aren't being shown.

Any help would be greatly appreciated. Thanks.

---

### Post by PhantmKllr on 2010-12-19
> **musclemanjr said:**
> Hi everybody,

I recently installed Ubuntu 10.10 on my machine. I logged in and installed a few programs like wine. Everything went fine until I rebooted. Now, after I log in, it gives me 2 error messages:

One about how it could not update ICEAuthority or something

Another about how usr/lib/libconf2-4/gconf-sanity-check2 returned status 256.

Then, something else pops up about how Nautilus can't find or doesn't have permission to write to home/user/Desktop and home/user/.nautilus.

I tried booting in recovery mode and did a dir on /home, but nothing showed up, which makes me think that they somehow disappeared or they aren't being shown.

Any help would be greatly appreciated. Thanks.
What programs did you Install?

---

### Post by sikander3786 on 2010-12-20
Welcome to the forums :-)

From Recovery Mode, we need to see the output of this command.

```
ls /home
```

---

