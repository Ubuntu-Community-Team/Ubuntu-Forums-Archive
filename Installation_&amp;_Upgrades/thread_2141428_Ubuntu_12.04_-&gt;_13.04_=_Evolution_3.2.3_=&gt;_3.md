---
title: "Ubuntu 12.04 -&gt; 13.04 = Evolution 3.2.3 =&gt; 3.6.4 = Loss of MAPI?"
date: 2013-05-02
forum: Installation &amp; Upgrades
---

### Post by guice on 2013-05-02
I just updated my Ubuntu 12.04 all the way to 13.04. In that update, Evolution updated, and now MAPI support is gone... evolution-mapi is installed. But I have no MAPI option anymore. My old mail account is also gone.

Any ideas as to why Evolution is not seeing the MAPI plugin?

*Marking Solved. Not adding EWS accounts is a known issue. Reboot enabled the account to show. MAPI is a depreciated plugin for Exchange 2010.

---

### Post by guice on 2013-05-02
Appears due to [this doc. item]("https://help.gnome.org/users/evolution/3.5/exchange-connectors-overview.html.en"), evolution-mapi is no longer the supported option. I've switched to evolution-ews, and while I do get the option, it does *not* save. I go through the settings: I successfully point to the web URL, and Evolution finds the URL. I finish, hit "Apply", and the email account is never added ...

---

### Post by guice on 2013-05-02
Going to mark this as closed. According to this bug on Launchpad [#1061195](https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/1061195), not adding ews accounts is a known issue with Evolution.

---

