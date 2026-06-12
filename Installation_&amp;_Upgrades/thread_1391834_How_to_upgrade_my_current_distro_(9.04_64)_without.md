---
title: "How to upgrade my current distro (9.04 64) without upgrading to the next (9.10)"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by iconoclast88 on 2010-01-27
I have a new laptop (Asus U50f) that has lots of glitches in 9.10 and 10.4, such as power management failing and freezing when unplugging from AC adapter, random booting issues and kernel failure, video, audio issues.

But 9.04 jaunty works great after i loaded the drivers. 

I want to be able to have the latest 9.04 only updates to all my packages without upgrading to the next distro (9.10 or 10.4)

doing apt-get upgrade has actually upgrade my distro in the past.

Thanks,

Josh

---

### Post by mikewhatever on 2010-01-27
Apt-get upgrade will install all available updates for you system, but you can't upgrade without upgrading to the next release.

---

### Post by snowpine on 2010-01-27
Either:

```
sudo apt-get update && sudo apt-get upgrade
```

or:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

The 2nd will give you kernel upgrades (if available). Neither will upgrade you to 9.10. You can also use the Update Manager if you prefer a GUI.

---

### Post by iconoclast88 on 2010-01-27
Ok, so you both disagree with each other. 

Any other opinions here to break the tie?

---

### Post by arubislander on 2010-01-27
```
sudo apt-get upgrade
``` does not upgrade you to the next release, but
```
sudo apt-get dist-upgrade
``` might, and in my experience will!

But why bother with the commandline? Why not just use the Update Manager? Just disable, or ignore the button to upgrade to a new release...

---

### Post by snowpine on 2010-01-27
> **iconoclast88 said:**
> Ok, so you both disagree with each other. 

Any other opinions here to break the tie?

It's not a popularity contest or a matter of opinion. ;)

If you're ever unclear what a command does, use man:

```
man apt-get
```

That will give you a more accurate answer than a random sampling of users on an internet forum. Good luck!

---

### Post by mikewhatever on 2010-01-28
> **iconoclast88 said:**
> Ok, so you both disagree with each other. 

Any other opinions here to break the tie?

To be fare, you disagree with yourself too, wanting to upgrade without upgrading.;)

---

