---
title: "Anyone else having &quot;issues&quot; with GDM?"
date: 2009-06-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2009-06-10
I noticed that GDM was updated last week with the "new" GDM---has anyone noticed anything "wrong" with it? I don't have a control panel to config GDM anymore & the default is really lacking in options......

---

### Post by Peter76 on 2009-06-10
Just checked, but nothing wrong here...

---

### Post by ad_267 on 2009-06-10
Is this the OpenGL GDM or something else? I'm trying out Kubuntu 9.10 so just have KDM here.

---

### Post by ranch hand on 2009-06-10
Mine is fine.

---

### Post by mc4100 on 2009-06-10
Hmm. I think I might know what's going on. Did you have to install it manually?
I, too, see an update to gdm that's been sitting in the queue for a while and which I've deliberately not been upgrading yet. It's coming in from a PPA, so do you have any enabled from which it might have sneaked in?

Better yet:
```
apt-cache policy gdm
```
> 
  Installed: 2.20.10-0ubuntu3
  Candidate: 2.26.1-0ubuntu0.1
  Version table:
     2.26.1-0ubuntu0.1 0
        500 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
 *** 2.20.10-0ubuntu3 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
        100 /var/lib/dpkg/status

---

### Post by autocrosser on 2009-06-10
Yes--That is the issue---I guess I allowed 2.26 to be installed & it's not quite ready yet....works, but no real way to change settings. It's only on one of my installs, so I'll wait a bit to see if it irons out OK.....

gdm:
  Installed: 2.26.1-0ubuntu0.1
  Candidate: 2.26.1-0ubuntu0.1
  Version table:
 *** 2.26.1-0ubuntu0.1 0
        500 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
        100 /var/lib/dpkg/status
     2.20.10-0ubuntu3 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages

---

### Post by mc4100 on 2009-06-10
Here's [yer problem]("https://launchpad.net/~ubuntu-desktop/+archive/ppa").

---

### Post by zika on 2009-06-10
Without ppa:
gdm:
  Installed: 2.20.10-0ubuntu3
  Candidate: 2.20.10-0ubuntu3
  Version table:
 *** 2.20.10-0ubuntu3 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
        100 /var/lib/dpkg/status

---

### Post by autocrosser on 2009-06-10
Yes--I have been wanting to test the "new" GDM for quite a while now & I guess in a half-asleep moment I determined that this was the time........Works well--just no config as of yet...;););)

---

### Post by pferraro on 2009-06-10
I tried out the new gdm too.  I really love the smooth transition from login to desktop - although deliberately patched away the panel animation and initial wallpaper fade late in the jaunty cycle - unfortunate IMO.

The biggest issue with the new gdm is my desktop session crashes randomly, and throws be back to the login screen, usually after a specific keystoke, e.g. enter.  These crashes don't happen with the old gdm.  I suspect there's some missing error handling somewhere in the new gdm code.  dmesg seems to suggest that gvfs is to blame - it seems to segfault alot - for which several launchpad reports already exist.

---

### Post by qamelian on 2009-06-10
> **pferraro said:**
> I tried out the new gdm too.  I really love the smooth transition from login to desktop - although deliberately patched away the panel animation and initial wallpaper fade late in the jaunty cycle - unfortunate IMO.

The biggest issue with the new gdm is my desktop session crashes randomly, and throws be back to the login screen, usually after a specific keystoke, e.g. enter.  These crashes don't happen with the old gdm.  I suspect there's some missing error handling somewhere in the new gdm code.  dmesg seems to suggest that gvfs is to blame - it seems to segfault alot - for which several launchpad reports already exist.
I don't think these crashes are limited to the new GDM, as I occasionally get them under to old GDM in Jaunty, as well.

---

### Post by zika on 2009-06-10
Now You got me interested. When I try to upgrade using  [http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu) I get offer to remove ubuntu-desktop and fast-user-switch-applet which I am not brave enough to do ... :) I'll pass for time being ... :)

---

### Post by taavikko on 2009-06-10
> **zika said:**
> Now You got me interested. When I try to upgrade using  [http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu) I get offer to remove ubuntu-desktop and fast-user-switch-applet which I am not brave enough to do ... :) I'll pass for time being ... :)

ubuntu-desktop is just a meta-package which determines what the gnome version will be like.

f-u-s-a offers just an applet to switch users etc.
upon removal, "logout" procedures will be available in system->menus

both of them can be removed with no harm.
Just that at this stage of devel, you'll might miss new features if doing so.

---

