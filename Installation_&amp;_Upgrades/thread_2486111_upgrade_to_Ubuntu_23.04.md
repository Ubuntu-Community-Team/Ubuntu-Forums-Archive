---
title: "upgrade to Ubuntu 23.04 ???"
date: 2023-04-20
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2023-04-20
with this

lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 23.04
Release:	23.04
Codename:	lunar

Do I need to upgrade ?
I have used it for while now.. 

Cheers

---

### Post by ajgreeny on 2023-04-20
You have used what for a while now?  Are you already on 23.04 or a previous version such as 22.04?

Many users, including me, stick to the LTS versions for their main systems, which at the moment is 22.04, but it's your choice.

There is no necessity to upgrade however as 22.04 id fully supported until April 2025 or 2027, depending on which DE version you're using.
If you are already using 23.04 you should certainly run updates frequently either with terminal commands or using the update manager GUI.

---

### Post by guiverc on 2023-04-20
It looks to me like you are already using Ubuntu 23.04.

If you installed either in *alpha*, *beta* or even the later *final* stage, by just applying normal upgrades (*ie. `sudo apt full-upgrade*`) you are running the full Ubuntu 23.04 product. It'll be supported for nine months.

My own system was installed early this year using an *alpha* ISO

```
guiverc@d7050-next:~/uwn/issues/783$   cat /var/log/installer/media-info 
Lubuntu 23.04 "Lunar Lobster" - Alpha amd64 (20230124)

```

but it's now running the final Ubuntu 23.04 product as I apply all upgrades daily (*I apply them three times per day during the development cycle actually*).

For me, I'll *release-upgrade*, possible on the coming weekend, and move to the MM release (*ie. stay on development*), but that's only because I work with a *flavor* team, and I find it helpful. The upgrade I plan doing is not one I'd recommend for average users. I can't do it now; there currently is nothing to *bump* to (why I called the next release 'MM'; I don't yet know the codename & [meta data for it doesn't yet exist]("https://changelogs.ubuntu.com/meta-release-development")).

---

