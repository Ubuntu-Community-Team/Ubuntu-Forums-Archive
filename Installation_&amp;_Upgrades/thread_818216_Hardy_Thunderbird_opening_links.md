---
title: "Hardy Thunderbird opening links"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by linux6994 on 2008-06-04
To ensure that Thunderbird opens links ensure that /usr/lib/firefox-3.0b5/firefox is set in Preferences > General > Config Editor for helper. apps.browser and network.protocol-handler.app.http and https
this will allow Thunderbird to open links.

---

### Post by glennr on 2008-06-28
See also:

[https://bugs.launchpad.net/bugs/173271]("https://bugs.launchpad.net/bugs/173271")

[URL="https://bugs.launchpad.net/bugs/192513"]https://bugs.launchpad.net/bugs/192513
[/URL]

---

### Post by gauss on 2008-07-15
> **glennr said:**
> See also:

[https://bugs.launchpad.net/bugs/173271]("https://bugs.launchpad.net/bugs/173271")

[URL="https://bugs.launchpad.net/bugs/192513"]https://bugs.launchpad.net/bugs/192513
[/URL]

I installed Kubuntu 8.04 (Hardy Heron) and the suggestions above worked for me. I needed to install thunderbird-gnome-support *and* use Thunderbird's Config Editor to set network.protocol-handler.app.http and network.protocol-handler.app.https to /usr/bin/firefox.

I can understand why Kubuntu might not install thunderbird-gnome-support but I don't understand why Thunderbird in Ubuntu (GNOME) already had the correct config. If it didn't, there'd be a *slew* of postings.

---

