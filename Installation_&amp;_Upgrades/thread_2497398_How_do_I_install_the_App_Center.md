---
title: "How do I install the App Center?"
date: 2024-05-03
forum: Installation &amp; Upgrades
---

### Post by peyre on 2024-05-03
I forced the 24.04 upgrade on a side laptop, and noticed that the Software Center is now gone (which I expected), but the App Center isn't there.  Of course I have Synaptic, but I was looking forward to replacement for Software Center.

I assume this was maybe one of the reasons the upgrade is delayed.  So, how do I go about installing the App Center manually?  I'm having trouble finding it in Synaptic or with app's and snap's search and find commands.

---

### Post by #&amp;thj^% on 2024-05-03
Hi peyre, will you try this first:
```
snap-store --quit
```
See if it will quit gracefully.
Or run:
```
killall snap-store
```

---

### Post by peyre on 2024-05-03
It's not there.  Not installed.

However, the error told me the command to get it:  sudo snap install snap-store.

That worked!  Now, the Snap Store looks almost exactly like Software Center.  Is that expected?  I thought the UI would be different.

---

### Post by deadflowr on 2024-05-03
> the Snap Store looks almost exactly like Software Center. Is that expected?

Looks like it, yes. Since it's based on gnome-software.
Behaves like it, partially.
It cannot install flatpaks.
And cannot install deb files from the desktop.

---

### Post by peyre on 2024-05-03
Good deal.  Thanks everyone!

---

### Post by Dennis N on 2024-05-03
App Center is  a specific channel of snap-store and is not like Ubuntu Software.

Check the installed version and channel:
```
dmn@Kayleigh-vm:~$ snap info snap-store
name:      snap-store
summary:   App Center
publisher: Canonical&#10003;
store-url: https://snapcraft.io/snap-store
license:   unset
description: |
  App Center
commands:
  - snap-store
snap-id:      gjf3IPXoRiipCu9K0kVu52f0H56fIksg
[COLOR="#FF0000"]tracking:     latest/stable/ubuntu-24.04[/COLOR]
refresh-date: 23 days ago, at 00:17 MST
channels:
  latest/stable:     41.3-77-g7dc86c8 2024-03-06 (1113) 13MB -
  latest/candidate:  41.3-77-g7dc86c8 2024-03-05 (1113) 13MB -
  latest/beta:       &#8593;                                       
  latest/edge:       0+git.f8622bc    2024-05-03 (1136) 10MB -
  preview/stable:    –                                       
  preview/candidate: 0.2.7-alpha      2023-02-02  (864) 10MB -
  preview/beta:      &#8593;                                       
  preview/edge:      0.3.0-alpha      2023-08-14 (1017) 11MB -
[COLOR="#FF0000"]installed:           0+git.1419621               (1124) 10MB -[/COLOR]

```
If you are tracking  **latest/stable/ubuntu-24.04** that is the App Center used in 24.04.
If you aren't on this channel, you can switch the channel from your terminal with the switch command. My guess (without testing) is this:
```
sudo snap switch --channel=latest/stable/ubuntu-24.04 snap-store
```

---

### Post by peyre on 2024-05-03
Odd, my tracking doesn't give a version number, simply says latest/stable - but that's the same as ubuntu-24.04, I expect.

---

### Post by Dennis N on 2024-05-03
In my output, latest/stable is version 41.something (revsion 1113). That would be Ubuntu Software.
if you want App Center, you will have to switch the channel.
If you don't like it, you can switch back.

---

