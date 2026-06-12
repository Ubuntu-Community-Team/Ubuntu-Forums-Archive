---
title: "gnome-terminal: undefined symbol: vte_terminal_set_alternate_screen_scroll"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by pbr on 2010-01-21
I started using the yaquake and tilda terminal emulators a few months ago, so I didn't notice this problem right away, thus I'm unsure what I've done that caused it.  

Today, when I try to run gnome-terminal I get the following error:

[FONT="Courier New"]gnome-terminal: symbol lookup error: gnome-terminal: undefined symbol: vte_terminal_set_alternate_screen_scroll
[/FONT]

I get the error when logged in as myself (pbr) and also if I try it as other users, so it's not related to my local per-user configuration files.

It appears ubuntu has custom versions of gnome-terminal and the VTE widget that support scrolling on the alternate screen?  A couple of google hits spoke about patches for VTE, and one hit showed a patch which seems to confirm this.

[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/262950](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/262950) looks similar - however, I'm seeing this on Ubuntu 9.10 and that bug was quite a while ago.

I tried running 'sudo aptitude reinstall libvte9' and that didn't help.

I'm wondering whether the order of sources in /etc/apt/sources.list might be the problem?

This one has me stumped, after an entire evening of investigation.  Your help is greatly appreciated.

---

