---
title: "How do I get past &quot;Cannot refresh snap-store&quot; nastygram"
date: 2023-05-06
forum: Installation &amp; Upgrades
---

### Post by jcpfuntner on 2023-05-06
[IMG]https://imgur.com/sY8xpDw[/IMG]I have Ubuntu 22 and when I open *Ubuntu Software* app it shows I have updates: [https://imgur.com/sY8xpDw](https://imgur.com/sY8xpDw)

When I try to upgrade, it asks for my password, churns for a couple of seconds, and then I get a nastygram [https://imgur.com/AcfQpc6](https://imgur.com/AcfQpc6):

```
Unable to updade "Snap Store": (null): cannot refresh "snap-store": snap "snap-store" has running apps (ubuntu-software), pids:2262
```

I tried rebooting and going through *Ubuntu Software* again but run into the same problem.  I suppose it's complaining about the *Ubuntu Software* app I'm opening first but I don't know a way around that.  I did [FONT=courier new]apt-get update[/FONT] and [FONT=courier new]apt list --upgradable[/FONT] but no snap packages are upgradable.

Does anyone have any advice?

[IMG]https://imgur.com/sY8xpDw[/IMG]

---

### Post by #&amp;thj^% on 2023-05-06
Live by the GUI / Die by the GUI...
to update snaps:
```
sudo snap refresh 
```
To just list upgrades
```
sudo snap refresh --list
```
You can also update a specific application if the other method fails
```

sudo snap refresh <Application>
```
BTW You will have to close Gnome-Software first...

---

### Post by jcpfuntner on 2023-05-06
Thanks for the suggestions but I'm still having trouble:

[FONT=courier new]# snap refresh --list[/FONT]
[FONT=courier new]Name        Version           Rev  Size  Publisher   Notes[/FONT]
[FONT=courier new]snap-store  41.3-71-g709398e  959  12MB  canonical&#10003;  -[/FONT]
[FONT=courier new]# snap refresh snap-store[/FONT]
[FONT=courier new]error: cannot refresh "snap-store": snap "snap-store" has running apps[/FONT]
[FONT=courier new]       (snap-store), pids: 2321[/FONT]
[FONT=courier new]# [/FONT]

I even tried rebooting and doing this the first thing.

---

### Post by #&amp;thj^% on 2023-05-06
> **jcpfuntner said:**
> Thanks for the suggestions but I'm still having trouble:

[FONT=courier new]# snap refresh --list[/FONT]
[FONT=courier new]Name        Version           Rev  Size  Publisher   Notes[/FONT]
[FONT=courier new]snap-store  41.3-71-g709398e  959  12MB  canonical&#10003;  -[/FONT]
[FONT=courier new]# snap refresh snap-store[/FONT]
[FONT=courier new]error: cannot refresh "snap-store": snap "snap-store" has running apps[/FONT]
[FONT=courier new]       (snap-store), pids: 2321[/FONT]
[FONT=courier new]# [/FONT]

I even tried rebooting and doing this the first thing.

Ok that's a new one i knew I was smart removing all snap :P
Please try this
```
sudo killall snap-store && sudo snap refresh snap-store
```
Any better now?

---

