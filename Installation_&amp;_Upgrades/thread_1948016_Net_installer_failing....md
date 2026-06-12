---
title: "Net installer failing..."
date: 2012-03-27
forum: Installation &amp; Upgrades
---

### Post by LinUxaliVe on 2012-03-27
Hi.

I'm attempting to install Ubuntu through the minimal net install method, but I seem to be running into some problems.

Even though it doesn't appear to be any different, I used the advanced text install option.

After configuring each step up until "Select and install software", I didn't appear to be receiving any errors. The problem raises it's head during that option where this output pops up on the screen.

```
Select and install software
Installation step failed
```

At that point, I moved over to the tty4 console, and saw the likes of this.

```
The following packages have unmet dependencies
```
```
linux-headers-3.0.0-17-generic depends on linux-headers-3.0.0-17: however
```
```
linux-headers-3.0.0-17 depends on linux-headers-3.0.0-17-generic: however
```
```
main-menu [370]: WARNING **: Configuring 'pkgsel' failed with error code 100
```
```
main-menu [370]: WARNING **: Menu item 'pkgsel' failed .
```

Any ideas as to why this is happening? The full Ubuntu disc installs without issues.

---

### Post by LinUxaliVe on 2012-03-28
Well since this thread will be all the way back on page 3 here soon, could someone who has used the minimal install (mini.iso) disc successfully tell which install path they took?

---

