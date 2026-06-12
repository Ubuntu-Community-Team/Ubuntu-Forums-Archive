---
title: "can't find 'chrome' (stable) after upgrade to 21.10"
date: 2022-02-19
forum: Installation &amp; Upgrades
---

### Post by dwater on 2022-02-19
I just upgraded from LTS to 21.10, and now when I 'search for' chrome using the desktop it shows only the dev and beta versions of chrome that I have installed, but it doesn't show the stable version. I can run 'google-chrome' successfully from the console, and I've checked the symlinks end up pointing to /usr/bin/google-chrome-stable [1] - and the chrome icon appears in the dock then, but I cannot 'Add to favourites' (does nothing). I don't see any messages in syslog...and can't see any other places for error messages to go.

Any ideas how to 'fix' this?

Edge seems to not have this problem (like chrome dev/beta)...perhaps now is the time :) I've been considering it for a while.

Max.

[1] ```
04:40:02 ~$ ls -l /usr/bin/google-chromelrwxrwxrwx 1 root root 31 Jul 20  2019 /usr/bin/google-chrome -> /etc/alternatives/google-chrome
04:40:06 ~$ ls -l /etc/alternatives/google-chrome
lrwxrwxrwx 1 root root 29 Jul 20  2019 /etc/alternatives/google-chrome -> /usr/bin/google-chrome-stable
04:40:12 ~$ 
$ namei /usr/bin/google-chrome | grep '^\s*l'
 l google-chrome -> /etc/alternatives/google-chrome
   l google-chrome -> /usr/bin/google-chrome-stable
     l google-chrome-stable -> /opt/google/chrome/google-chrome




```

---

### Post by Holger_Gehrke on 2022-02-19
I don't think you can add a program to favourites which wasn't started from a .desktop file. So try creating one for google-chrome-stable in ~/.local/share/applications. Use the .desktop files in /usr/share/applications as a template or look up the standard for .desktop files on [freedesktop.org]("https://specifications.freedesktop.org/desktop-entry-spec/latest/").

Holger

---

### Post by dwater on 2022-02-19
Well, that gave me the clue I needed. When I looked in that .local directory, I noticed that there wasn't anything for the beta & dev versions, but there was a 'google-chrome.desktop' file - when I removed that, and logged out/in, it worked just like the others :D

Thanks!

Max.

---

