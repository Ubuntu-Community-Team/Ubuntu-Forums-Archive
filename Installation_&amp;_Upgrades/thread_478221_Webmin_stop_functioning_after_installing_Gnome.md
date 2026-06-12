---
title: "Webmin stop functioning after installing Gnome"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by munnan on 2007-06-19
Hi Every body,
I am facing an issue with webmin.
Actually I installed Ubuntu 7.04 Server and webmin .
everything was working fine.
 I installed Gnome.and problem started.
webmin was not oppening on [https://localhost:defaultport/](https://localhost:defaultport/) my default port was 12345.
I again install webmin and it start functioning again.but after restart the same problem.I cannot access webmin.
Please let me know if any body fixed this situation with gnome installation.
Thanks

---

### Post by stalker145 on 2007-06-19
I don't recall the terminal command to use to start WebMin, but what you can check once it's started is whether it is set to automatically start at boot. It is *possible* that this setting has mysteriously changed. My apologies for not having more info for you, but my network here at work does not allow access to [the WebMin site]("http://www.webmin.com").

And don't forget that once you reinstalled, the server probably defaulted back to port 10000 for access insteaad of your desired 12345.

Check back if this doesn't clear things up.

---

