---
title: "Allowing normal users to upgrade the system?"
date: 2010-09-11
forum: Installation &amp; Upgrades
---

### Post by FanOfTuxs on 2010-09-11
Hi!

Here's what I want to do: install ubuntu on a laptop and then create a  normal user so that the user could install the normal upgrades without  using the root account (or getting root privileges via sudo).

I know that this can be done by adding the user to the admin group, but this has (at least) two bad side effects:

1. The user can use sudo to gain root access. (And then do everything: install or remove programs...)

2. The update-manager doesn't seem to appear in the panel. (In stead it opens in the background.)

I could easily make a script that downloads and installs the upgrades  automaticly, but I'd like to give the user a chance to choose when to do  all this. So that it's not done for example when the user is using slow  mobile connection.

Any ideas how to do this?

---

### Post by FanOfTuxs on 2010-09-21
Nobody has any ideas? :(

Not even for this:

> **FanOfTuxs said:**
> 
2. The update-manager doesn't seem to appear in the panel. (In stead it opens in the background.)


(And by background I meant that the update application starts automaticly as minimized.)

---

### Post by FanOfTuxs on 2010-11-19
Answering to myself then, to the 2nd part, which can be done with:

```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```Still haven't found a way to do the upgrades without adding the user to the admin group...

---

