---
title: "update-manager -d doesn't have upgrade button"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by phorgan1 on 2010-03-31
I'm on a fully updated and upgraded 9.10, and when I do update-manager -d, I don't get the button to do an upgrade to 10.04!  What could cause this?  I've tried the -d, -c, --check-dist-upgrades, --devel-release, -p, --proposed, and --dist-upgrade.  I'm completely up to date on 9.10, but I want to upgrade to 10.04!

Patrick

---

### Post by 2hot6ft2 on 2010-03-31
Did you try it with sudo?

---

### Post by whoop on 2010-03-31
what does:
```

cat /etc/issue

```
return?

---

### Post by phorgan1 on 2010-03-31
> **whoop said:**
> what does:
```

cat /etc/issue

```
return?

It returns:
Ubuntu 9.10 \n \l

Of course I run update-manager with sudo.

---

### Post by mkvnmtr on 2010-03-31
I believe he was asking if you preceeded the command update-manager -d with sudo.
You might try closing the update manager and doing the whole thing in the terminal.

---

### Post by phorgan1 on 2010-03-31
> **phorgan1 said:**
> It returns:
Ubuntu 9.10 \n \l

Of course I run update-manager with sudo.
Wow!  Strange!  I never thought to try update-manager without sudo, but I just did, and now I get the upgrade button!  Wonder why it wasn't there (over and over again) with sudo?

---

### Post by garvinrick4 on 2010-03-31
sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade

---

### Post by phorgan1 on 2010-04-01
> **mkvnmtr said:**
> I believe he was asking if you preceeded the command update-manager -d with sudo.
You might try closing the update manager and doing the whole thing in the terminal.

Yes, and I told him I did. When I didn't, it worked right.

---

