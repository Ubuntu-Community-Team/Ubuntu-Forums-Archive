---
title: "gdm won't start on Asus 1201HA"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by Tectuktitlay on 2011-02-28
Hi all,

I've installed Ubuntu on the netbook of a friend of mine, an Asus EEE 1201HA. Now I'm running into a problem. Gdm won't start when I use the latest kernel (2.6.35.25). When I use kernel 2.6.35-22 there's no problem and the gdm start as usual

Under the newer kernel I'm geting errors like:

```
"failed due to unknown user id"
```

When I start gdm manually from tty1 I get the following result:

```
sudo gdm
** (gdm-binary:1594): WARNING **: Failed to acquire org.gnome.DisplayManager
** (gdm-binary:1594): WARNING **: Could not acquire name; bailing out
```

I've tried purging the gdm package and reinstalling it, but that didn't help.

Does anybody have any ideas?

BRgds,

Tec

---

