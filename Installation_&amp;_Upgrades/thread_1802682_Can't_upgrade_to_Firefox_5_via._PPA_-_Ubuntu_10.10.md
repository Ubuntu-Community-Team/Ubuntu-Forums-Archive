---
title: "Can't upgrade to Firefox 5 via. PPA - Ubuntu 10.10"
date: 2011-07-12
forum: Installation &amp; Upgrades
---

### Post by el canadiano on 2011-07-12
I was asked to create a new thread by a moderator. Just to refresh,

- I am using Ubuntu 10.10, and cannot upgrade to Firefox 5.
- The error is this.

Changes for the versions:
4.0.1+build1+nobinonly-0ubuntu0.11.04.1~mfs~maverick1
5.0+build1+nobinonly-0ubuntu0.10.10.1~mfs1

This change is not coming from a source that supports changelogs.

- I am using the Firefox PPA. This is the one I'm using.

sudo add-apt-repository ppa:mozillateam/firefox-stable

---

### Post by mikewhatever on 2011-07-12
What you posted above is not an error, the message simply notifies that the list of changes isn't available. Can you explain in detail why can't you upgrade.

---

### Post by ssherwood on 2011-07-12
> [COLOR=Lime]I was asked to create a new thread by a moderator. Just to refresh,

- I am using Ubuntu 10.10, and cannot upgrade to Firefox 5.[/COLOR] [COLOR=Lime]
- The error is this.

Changes for the versions:[/COLOR] [COLOR=Lime]
4.0.1+build1+nobinonly-0ubuntu0.11.04.1~mfs~maverick1
5.0+build1+nobinonly-0ubuntu0.10.10.1~mfs1

This change is not coming from a source that supports changelogs.[/COLOR] [COLOR=Lime]

- I am using the Firefox PPA. This is the one I'm using.[/COLOR] [COLOR=Lime]

sudo add-apt-repository ppa:mozillateam/firefox-stable    [/COLOR]  Hi,

Try this PPA:
```
ppa:ubuntu-mozilla-security/ppa
```and dont remove the PPA:
```
ppa:mozillateam/firefox-stable                      
```

---

### Post by el canadiano on 2011-08-07
Thought you guys might want to know that I fixed this by removing all Firefox PPAs, uninstalling Firefox, then reinstalling it via. the PPAs.

---

### Post by ssherwood on 2011-08-20
Hi,

If you are still having issues follow my video tutorial, as this tutorial install Firefox 6.

[SIZE=2]***[Ubuntu How To: Installing Mozilla Firefox 6]("http://youtu.be/zenxrpZnMMc")***[/SIZE]

---

