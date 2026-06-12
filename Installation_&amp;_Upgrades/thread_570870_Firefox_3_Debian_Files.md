---
title: "Firefox 3 Debian Files"
date: 2007-10-08
forum: Installation &amp; Upgrades
---

### Post by Linux_Man on 2007-10-08
Is there a way that I can get Firefox 3 (gran-paradiso) on Ubuntu as a .deb file? I can get the binary packages from Mozilla's FTP server and they work fine, but I don't want to run it as root to update it. When I was on Windows I could just download the .exe and I could update it fine. I tried googling it and I got the launchpad site to download the .deb s but they wouldn't install because they either wanted to need firefox 3.0 or XLS runner. I would compile from source, but Mozilla's documentation doesn't make much sense, if someone could explain it, it would be wonderful. And yes I know that Firefox 3 is still in alpha/beta but its faster and I enjoy the speed boost.

---

### Post by Linux_Man on 2007-10-08
Does anyone have any links to .deb files that work? Im on Ubuntu 7.04 Fiesty also.

---

### Post by kerry_s on 2007-10-08
why do you have to run it as root?
just unpack it to your home and run it from there, make the launchers(~/firefox/firefox) and link the plugins(rm -rf ~/firefox/plugins && ln -s /usr/lib/mozilla/plugins ~/firefox/plugins)

there's no reason at all to need to run it as root.

---

### Post by Linux_Man on 2007-10-10
So I can update it from help----> Check for updates without being root like I could on Windows?

---

