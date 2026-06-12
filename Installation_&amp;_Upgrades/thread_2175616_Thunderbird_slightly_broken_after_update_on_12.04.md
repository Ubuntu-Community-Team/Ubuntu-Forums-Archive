---
title: "Thunderbird slightly broken after update on 12.04"
date: 2013-09-20
forum: Installation &amp; Upgrades
---

### Post by mathieud on 2013-09-20
Hello,

I updated my Ubuntu 12.04 box yesterday (normal daily updates proposed by ubuntu at startup, not an upgrade). Specifically there was an update of thunderbird (and firefox). I didn't check what pakages were updated.

Now, thunderbird seems to work but all the icons (accounts, folders, sent folders) are the same (standard folder icon in nautilus for instance). Also the folders containing unread messages are no longer in bold.

Is anyone being affected by this? Any workaround?

---

### Post by sudodus on 2013-09-20
I have also problems after the update yesterday (Sept 19). I have

```
$ [COLOR=#0000ff]lsb_release -a[/COLOR]
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise
$ [COLOR=#0000ff]uname -a[/COLOR]
Linux ssd-grund 3.2.0-53-generic-pae #81-Ubuntu SMP Thu Aug 22 21:23:47 UTC 2013 i686 i686 i386 GNU/Linux

```

I have Thunderbird 24.0 from the repositories.

 The window to write letters (or reply to letters) is borked. There is no cursor, and although it is focused, the active window is still the main Thunderbird window, so I can't write anything. This happens after [COLOR=#000000][FONT=Ubuntu]running Thunderbird for [/FONT][/COLOR]a while, and I have to close and re-open Thunderbird to be able to write a letter again.

I'm reporting it at Launchpad as

[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1228002](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1228002)

---

### Post by Tomasz_Borowiec on 2013-09-20
What helped me was disabling the "tasks and mails" plugin - that fixed the icon and bold part, but I still don't have the even/odd email line colouring. Does anybody know how to get that back?

---

### Post by mathieud on 2013-09-20
Hello,

It seems to work for me this evening. I have done nothing.

---

### Post by sudodus on 2013-09-20
That's good :-) but my bug is still alive :-(

---

